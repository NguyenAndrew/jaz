# jaz

Because the best way to communicate with others is through jaz

## What is jaz?

JAZ (JSON, API, ZIP) is a transport layer agnostic way of sharing "clear intent" through APIs

## Why jaz?

JAZ allows you to do the following:
* Allows for flexible schemas
* Allows you to input multiple binary files within a single request

## What does jaz look like?

Example 1: You have a consumer that wants to store information about shops, and this information is located across several text files.

Your consumer can give you a request like the following:

example1.zip
```
.
├── api.json                   # The entrypoint for a jaz file (api.json is the default entrypoint name)
├── shop1.txt
├── shop2.txt
├── shop3.txt
```
api.json
```
{
    inputs: [shop1.txt, shop2.txt, shop3.txt]
}
```

And you can reply with the following:
```
Shops stored succesfully!
```

Example 2: Your consumer now wants to get the names and locations of all the shops rated 1 stars

Your consumer can give you a request like the following:

example2.zip
```
.
├── api.json                   # The entrypoint for a jaz file
```
api.json
```
{
    query: "Only include restaurants with 1 stars"
    output: {
                restaurants: [ 
                    {
                        name: "",
                        location: ""
                    }
               ]
   }
}
```

And you can reply with the following:
```
{
    restaurants: [
        {
            name: example_restaurant_1
            location: example_location_1
        },
        {
            name: example_restaurant_2
            location: example_location_2
        }
    ]
}
```
