# Group Introduction

## What is group

## Create group

Then you may want to define a new group. You can define group using a json file, for excample:
    
    {
        "key": "EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr",
        "root": {
            "threshold": 6,
            "nodes": [
                {
                    "threshold": 1,
                    "weight": 3,
                    "nodes": [
                        { "weight": 1, "key": "EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV" },
                        { "weight": 1, "key": "EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX" }
                    ]
                },
                { "weight": 3, "key": "EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX" },
                {
                    "threshold": 1,
                    "weight": 3,
                    "nodes": [
                        { "weight": 1, "key": "EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV" },
                        { "weight": 1, "key": "EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX" }
                    ]
                }
            ]
        }
    }

Save as `g.json` file, and it defines a simple group, with height of group-tree is 3.

You can create this group by typing:

    evtc -u testnet1.everitoken.io:8888 group create g.json

You will see output:

    executed transaction: d8331476b645157a5c32da91c15085fcedada7ad817beadf1a43c11b45fee9c9
    total elapsed: 6376 us
    total charge: 0.00000 S#1
    (1 of 1)
       action : newgroup
       domain : .group
          key : gp
      elapsed : 6210 us
      details : 
    |->name : gp
    |->group : 
        |->name : gp
        |->key : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
        |->root : 
            |->threshold : 6
            |->nodes : 
                |->threshold : 1
                |->weight : 3
                |->nodes : 
                    |->key : EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
                    |->weight : 1
                    |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
                    |->weight : 1
                |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
                |->weight : 3
                |->threshold : 1
                |->weight : 3
                |->nodes : 
                    |->key : EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
                    |->weight : 1
                    |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
                    |->weight : 1
        |->metas : (empty)

Then you will query this group by group name:

    evtc get group gp

Output:

    |->name : gp
    |->key : EVT7JoY9nbkfWCx2opvUhS9pPmWbLjRuhNCmDTG971PVkhxvAzWWr
    |->root : 
        |->threshold : 6
        |->nodes : 
            |->threshold : 1
            |->weight : 3
            |->nodes : 
                |->key : EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
                |->weight : 1
                |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
                |->weight : 1
            |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
            |->weight : 3
            |->threshold : 1
            |->weight : 3
            |->nodes : 
                |->key : EVT6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
                |->weight : 1
                |->key : EVT8MGU4aKiVzqMtWi9zLpu8KuTHZWjQQrX475ycSxEkLd6aBpraX
                |->weight : 1
    |->metas : (empty)

