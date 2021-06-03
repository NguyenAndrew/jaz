# jaz

Because the best way to communicate with others is through jaz

## What is jaz?

JAZ (JSON, API, ZIP) is a transport layer agnostic way of sharing "clear intent" through APIs.

## Why jaz?

JAZ allows you to do the following:
* Allows for flexible input/output schemas
* Allows input of multiple binary files within a single request
* Allows for rapid product iteration through simplicity and flexibility

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

## Does the zip file have to be a certain name.

No. Feel free to enforce a specific name or let your consumer choose any name they want.

## Does the api.json have to be in a certain format.

No. api.json can be any valid json format.

## Can the api.json be renamed to something else.

The default name is api.json. However, naming is flexible!

## Does the jaz response have to be a zip

The response can be whatever you want to make for the consumer. It can be anything (including zips)!

## Are you limited to a single http when using jaz?

JAZ can use as many (or as little) http endpoints as you like. Choose what is best for your consumer!

## Why jaz, when REST and GraphQL already exists

jaz is compatible with both REST and GraphQL, but could out compete both of these paradigms in the future! 

jaz provides both an extremely convenient way for people to create their own APIs, and allows for consumers to grab the information they want.

## Why doesn't jaz just use multi-part HTTP feature? Why would I use jaz when multi-part exists?

jaz is transport layer agnostic, but there is another reason even when using HTTP. jaz's simplicity and flexibility (both the zip and api.json) provides a better creator and consumer experience then directly using multi-part.

## Wont my API's take a performance hit consuming zips? Won't my consumers take a performance hit creating zips?

Start creating your API's with jaz first, and see if this concern actually applies. Leverage usability and performance, and see what solution best applies for your product and consumers.

## Why zip files? Why not INSERT OTHER file grouping format here?

Technically could have been another format. ZIP is a commonly used to group files together. Also makes "jaz" an easy acronym to remember.

## How can I do API discovery?

You can do API discovery similar to REST and GraphQL. Either have it generated automatically, or write it out manually.

## My API requires the consumer to input a large zip file. However, my serverless backend has a file size limit! What can I do here?

Have your consumer create a request that contains a presigned url to the jaz request, instead of sending in the zip file directly. In the backend of your API, you can use the presigned url to retrieve the actual jaz request.
