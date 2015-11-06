# Emperical JSON Data Store
EJDS is an API that allows people to store JSON data that will expire after 10 minutes unless extended. As EDJS is an API all documentation is contained below.

### Authorization
For requests that require authorization the HTTP basic authoriztion header will be used in the format

`Authorization: Basic id:key`

### Response Headers
All valid responses will contain the following headers:

`X-EJDS-EXPIRE` - UTC datetime of the JSON Data Store expiery

### Endpoints
#### Create JSON Data Store
This will all users to create a new JSON Data Store. If successful the repsonse will reply with the id, key and time (UTC) that the data store will expire.

`POST /`

Example Response:
```
{
    "id": String,
    "key": String,
    "expire": Datetime
}
```

#### Retrieve JSON Data Store
This will allow users to retrieve the data store which was previously created. This request requires authorization.

`GET /<Storage Id:String>`

#### Extend JSON Data Store
This request will extend the JSON Data Store by 10 minutes for each request to a maximum of 6 extensions. This requests requires authorization. 

`PUT /<Storage Id:String>/extend`

#### Stats for JSON Data Store
This request will allow users to get the stats of the JSON Data Store. This request requires authentication.

`GET <Storage Id:String>/stats`

Example Response:
```
{
    "id": String,
    "expire": String,
    "extensions": Integer,
    "data": {
        "size": String
    },
    "accesses": Integer
}
```