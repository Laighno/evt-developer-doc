# Building EveriToken

## Fetch EVT Code

First you need to fetch evt source code here: https://github.com/everitoken/evt, you can run:

    git clone https://github.com/everitoken/evt
    git submodule update --init

This will fetch evt and submodules as well.

## Fetch and Build Dependencies

1. To compile `evt`, you need to use GCC Toolset 7.x. In CentOS7, you can install `devtoolset-7` to get it, which is included in `Centos Software Collections Repository`.

2. You need to use `yum` or `apt` to install these packages: `git` `autoconf` `automake` `libtool` `bzip2-devel` `openssl-devel` `gmp-devel` `python-devel` `lz4-devel` `libzstd-devel`.

3. You need to compile and install `CMAKE`, you can fetch it from here: https://cmake.org/files/v3.10/cmake-3.10.2.tar.gz

4. You need to compile and install `Boost` library 1.66, you can get it from here: https://dl.bintray.com/boostorg/release/1.66.0/source/boost_1_66_0.tar.bz2)

    ./bootstrap
    ./b2 install

5. You need to compile and install `secp256k1-zkp`, you can clone repo from here: https://github.com/cryptonomex/secp256k1-zkp.git

6. You need to compile and install `gflags`, you can clone repo from here: https://github.com/gflags/gflags.git, and you can build dynamic library instead of static library:

    cmake /path/to/gflags

After build all these libraries above, you can then build `evt`.

    cmake /path/to/evt
    make evtd evtc evtwd

## Start single node

Then you should run single test node:
    
    sudo ./evtd -e --http-validate-host=false --charge-free-mode --loadtest-mode --plugin=evt::mongo_db_plugin --plugin=evt::history_plugin --plugin=evt::history_api_plugin --plugin=evt::chain_api_plugin --plugin=evt::evt_api_plugin --plugin=evt::evt_link_plugin --producer-name=evt --delete-all-blocks -d /tmp/evt -m 'mongodb://127.0.0.1:27017'

If successful, `evtd` will display some information, starting with::

    2018-08-30T00:39:48.978 thread-0   chain_plugin.cpp:174          plugin_initialize    ] initializing chain plugin
    2018-08-30T00:39:48.980 thread-0   chain_plugin.cpp:290          plugin_initialize    ] Deleting state database and blocks
    2018-08-30T00:39:49.428 thread-0   chain_plugin.cpp:401          plugin_initialize    ] Starting up fresh blockchain with default genesis state.
    2018-08-30T00:40:20.151 thread-0   token_database.cpp:1367       load_savepoints      ] No savepoints log in token database
    2018-08-30T00:40:20.165 thread-0   mongo_db_plugin.cpp:687       plugin_initialize    ] initializing mongo_db_plugin
    2018-08-30T00:40:20.165 thread-0   mongo_db_plugin.cpp:695       plugin_initialize    ] Deleted all blocks: wiping mongo database on startup
    2018-08-30T00:40:20.165 thread-0   mongo_db_plugin.cpp:709       plugin_initialize    ] connecting to mongodb://127.0.0.1:27017
    2018-08-30T00:40:20.166 thread-0   mongo_db_plugin.cpp:535       wipe_database        ] mongo db wipe_database

## Start the Wallet Manager

In the first terminal windows, start `evtwd`, the wallet management application.

    ./evtwd --http-server-address 127.0.0.1:9999

If successful, `evtwd` will display some information, starting with:

    1692293ms thread-0   wallet_plugin.cpp:41          plugin_initialize    ] initializing wallet plugin
    1692293ms thread-0   http_plugin.cpp:141           plugin_initialize    ] host: 127.0.0.1 port: 9999 
    1692294ms thread-0   http_plugin.cpp:144           plugin_initialize    ] configured http to listen on 127.0.0.1:9999
    1692294ms thread-0   http_plugin.cpp:156           plugin_startup       ] start processing http thread
    1692294ms thread-0   http_plugin.cpp:213           plugin_startup       ] start listening for http requests
    1692294ms thread-0   http_plugin.cpp:218           plugin_startup       ] http io service exit
    1692294ms thread-0   wallet_api_plugin.cpp:70      plugin_startup       ] startin

It says the wallet is listening on 127.0.0.1:9999. This indicated evtwd is running correctly.