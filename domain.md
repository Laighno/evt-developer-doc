# Domain Introduction

## What is domain

Domain is classification of tokens, which means every token must belong to a domain.And token is unique within a specific domain.

Domain has three kinds of authorization: `issue`, `transfer`, `manage`:

`issue` means who has the authorization to issue token in this domain.

`transfer` means who has the authorization to transfer token in this domain.

`manage` means who has the authorization to manange this domain: change the authorization of the domain.

Domain which begin with a `.` is for specific use, as `.fungible` which is a special domain that manage fungible token.

## Create domain

Create a domain named cookie:
    
    evtc domain create cookie EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr --payer EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr

Great! You just created a new domain named `cookie`! And `EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr` is `cookie` domian's issuer.

You will get the ouput like this:

    executed transaction: 301df994e24450afc16816c8c0f9c61e42aa15b36c46452f8358c37a14840777
    total elapsed: 9916 us
    total charge: 0.00000 S#1
    (1 of 1)
       action : newdomain
       domain : cookie
          key : .create
      elapsed : 9495 us
      details : 
    |->name : cookie
    |->creator : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->issue : 
        |->name : issue
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1
    |->transfer : 
        |->name : transfer
        |->threshold : 1
        |->authorizers : 
            |->ref : [G] .OWNER
            |->weight : 1
    |->manage : 
        |->name : manage
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1

You can now query the domain you just created!

    evtc get domain cookie

This will get:

    |->name : cookie
    |->creator : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->create_time : 2018-08-30T02:27:03
    |->issue : 
        |->name : issue
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1
    |->transfer : 
        |->name : transfer
        |->threshold : 1
        |->authorizers : 
            |->ref : [G] .OWNER
            |->weight : 1
    |->manage : 
        |->name : manage
        |->threshold : 1
        |->authorizers : 
            |->ref : [A] EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
            |->weight : 1
    |->metas : (empty)
    |->address : EVT0000005X5qdvvvnpfuMNm7CabbLb3P6L2HJpmjyRT6UTiW8hDZ
