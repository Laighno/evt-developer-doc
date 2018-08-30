# Docker QuickStart

## Step 1: Pull Image

Everitoken Dev Docker image is a compiled version of the Everitoken software designed for local development.

Pull the image from the repository:

    docker pull everitoken/evt:latest

And start the Everitoken node:

    docker run --name evtd -p 8888:8888 -p 9876:9876 -t everitoken/evt evtd.sh --http-validate-host=false --charge-free-mode 

Check it is working:

    docker logs --tail 10 evtd

Your output should be similar to this:

    2018-08-20T21:26:31.614 thread-0   evt_api_plugin.cpp:53         plugin_startup       ] starting evt_api_plugin
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_domain
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_fungible
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_fungible_balance
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_group
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_suspend
    2018-08-20T21:26:31.614 thread-0   http_plugin.cpp:595           add_handler          ] add api url: /v1/evt/get_token
    2018-08-20T21:26:31.614 thread-0   net_plugin.cpp:3126           plugin_startup       ] starting listener, max clients is 25
    2018-08-20T21:26:31.614 thread-0   producer_plugin.cpp:652       plugin_startup       ] producer plugin:  plugin_startup() begin
    2018-08-20T21:26:31.614 thread-0   producer_plugin.cpp:680       plugin_startup       ] producer plugin:  plugin_startup() end

Congrats! You have a very simple single node blockchain running in your Docker container!

Also go to this address in the browser to check that RPC interface is working:

    curl http://127.0.0.1:8888/v1/chain/get_info

You should see a message similar to following:

    {"server_version":"2784029a","chain_id":"dae43118cc62801c4148c4143865be5bde49561fc61671516fc9183cdec91337","evt_api_version":"3.1.0","head_block_num":1,"last_irreversible_block_num":0,"last_irreversible_block_id":"0000000000000000000000000000000000000000000000000000000000000000","head_block_id":"000000019034e61532475fe9e396442127692fb3ddad3f971714213d5c0b2742","head_block_time":"2018-05-31T12:00:00","head_block_producer":"","recent_slots":"","participation_rate":"0.00000000000000000"}


## Step 2: Alias Evtc

Evtc is a command line interface to interact with the blockchain and to manage wallets.

For convenience we will create a bash alias for evtc running inside our container. In terminal, run:

    alias evtc='docker-compose exec evtwd /opt/evt/bin/evtc -u http://evtd:8888 --wallet-url http://localhost:9999

Now try to run evtc --help in your Terminal. You should see a following output:

    Command Line Interface to everiToken Client
    Usage: /opt/evt/bin/evtc [OPTIONS] SUBCOMMAND

    Options:
      -h,--help                   Print this help message and exit
      -u,--url TEXT=http://127.0.0.1:8888
                                  the http/https URL where evtd is running
      --wallet-url TEXT=http://127.0.0.1:9999
                                  the http/https URL where evtwd is running
      -r,--header                 pass specific HTTP header; repeat this option to pass multiple headers
      -n,--no-verify              don't verify peer certificate when using HTTPS
      -v,--verbose                output verbose actions on error
      --print-request             print HTTP request to STDERR
      --print-response            print HTTP response to STDERR

    Subcommands:
      version                     Retrieve version information
      create                      Create various items, on and off the blockchain
      get                         Retrieve various items and information from the blockchain
      net                         Interact with local p2p network connections
      domain                      Create or update a domain
      token                       Issue or transfer tokens
      group                       Update pemission group
      fungible                    Create or update a fungible asset
      assets                      Issue and transfer assets between addresses
      meta                        Add metadata to domain, group ot token
      suspend                     Approve or cancel suspend transactions
      producer                    Votes for producers
      wallet                      Interact with local wallet
      sign                        Sign a transaction
      push                        Push arbitrary transactions to the blockchain

If you don't need evtwd afterwards, you can stop the evtwd service using

    docker-compose stop evtwd

### Stop and remove all

If you have tested all the features, you can stop and remove all the containers using

    docker-compose down

