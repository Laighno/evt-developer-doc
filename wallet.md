# Wallet Introdction

Wallet is a app to keep and manage your keys.

## Create a Default Wallet

we will use evtc to create the default wallet, evtc will create wallet server aotomatically:

    evtc wallet create

evtc will prompt that it created the "default" wallet, and will provide a password for future wallet access. You need to keep the password seriously for future use. Here is an example of this output:

    Creating wallet: default
    Save password to use in the future to unlock this wallet.
    Without password imported keys will not be retrievable.
    "PW5KFv4tQfhf8bWwePqrmPM2QbcTTTxUwDzg1bgmaJaHiquT9qeuC"

When creating "default" wallet, it will create a new key pair for you. You can see your default key by typing this:

    evtc wallet keys

Here's an example output:

    [[
        "EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV",
        "5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3"
      ]
    ]

If you want to generate new key, you can type this:

    evtc create key

You will get like:

    Private key: 5K8N8MZfkzdE4iaMVqR2btgTMM4MTWNAjyVJQjN8Zw1EWmXsW52
    Public key: EVT546WaW3zFAxEEEkYKjDiMvg3CHRjmWX2XdNxEhi69RpdKuQRSK

Then you can import new key to your wallet:

    evtc wallet import 5K8N8MZfkzdE4iaMVqR2btgTMM4MTWNAjyVJQjN8Zw1EWmXsW52

Key will be imported like this:

    imported private key for: EVT546WaW3zFAxEEEkYKjDiMvg3CHRjmWX2XdNxEhi69RpdKuQRSK