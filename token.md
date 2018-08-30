# Token Introduction

## What is token

Token(nonfungible token) is a kind of certification that you own something.

## Issue token

Issue token `t1` `t2` `t3` in domain `cookie`:

    evtc token issue cookie EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr -n t1 t2 t3 --payer EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr


You will get the ouput like this:
    
    executed transaction: 3947c11af79c645faab204bc678927e2dd826996fafbc9ea5c3a984390
    total elapsed: 412 us
    total charge: 0.00000 S#1
    (1 of 1)
       action : issuetoken
       domain : cookie
          key : .issue
      elapsed : 235 us
      details : 
    |->domain : cookie
    |->names : 
          |->t1
          |->t2
          |->t3
    |->owner : 
          |->EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr

Then yopu could check the token:

    evtc get token cookie t1

Output:

    |->domain : cookie
    |->name : t1
    |->owner : 
          |->EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->metas : (empty)
