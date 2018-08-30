# Fungible Introduction

## What is fungible token

Fungible means There is no difference between two tokens.

For example, money is a typical fungible token.
Because if spending one dollar, I won't care spending this coin or another.

Correspondingly, nonfungible means each token is unique. If I have two cats, I must differentiate them even though they looks absolutely the smae.

There is two kind of authorization in fungible `issue` `manage`.

In everitoken, token is nonfugible if we don't point out it is fungible.

## Create fungible

Create a fungible named RMB:

    evtc fungible create RMB rmb "5,S#3" EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr "100.00000 S#3" --payer EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr

Great! You just created a new gungible named `RMB`! And `EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr` is `RMB` fungible's creator.

You will get the ouput like this:

    executed transaction: 03aa93e2a9af4fe1be7db55623d24685334d7ee1e7382dec205a5ab32f3edb09
    total elapsed: 510 us
    total charge: 0.00000 S#1
    (1 of 1)
       action : newfungible
       domain : .fungible
          key : 3
      elapsed : 346 us
      details : 
    |->name : RMB
    |->sym_name : rmb
    |->sym : 5,S#3
    |->creator : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->issue : 
        |->name : issue
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1
    |->manage : 
        |->name : manage
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1
    |->total_supply : 100.00000 S#3

And then you could issue this fungible to others:

    evtc fungible issue EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr "1.00000 S#3" --payer EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr

Ouput:

    executed transaction: b5d31351dac16be0189dd599350474fff537384bcad59e4a5e74453cee6c9cdb
    total elapsed: 499 us
    total charge: 0.00000 S#1
    (1 of 1)
       action : issuefungible
       domain : .fungible
          key : 3
      elapsed : 323 us
      details : 
    |->address : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->number : 1.00000 S#3
    |->memo : 

Check the asset:
    
    ./evtc get balance EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr

Output:

    (1 of 1)
    |->1.00000 S#3
