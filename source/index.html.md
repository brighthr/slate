---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='mailto:github@brighthr.com'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Bright API! You can use our API to access data we hold on you, your subordinates and your company.

You can view examples in the dark area to the right.

This API documentation page was created with [Slate](https://github.com/lord/slate). You can fork it and use it as a base for your own API's documentation.

# Authentication

Before you can integratewith our APIs, you must set up your development environment to get OAuth 2.0 client ID and secret credentials for the sandbox and live environments. You exchange these credentials for an access token that authorizes your REST API calls. To test your web and mobile apps, you create sandbox accounts.

To request acces, please contact us <a href='mailto:github@brighthr.com'>here</a>.

Once you have your client ID, you can request an Access Token.

```shell
curl -v https://someurl/oauth2/token \
   -H "Accept: application/json" \
   -u "client_id:secret" \
   -d "grant_type=client_credentials"
```

> Make sure to replace `secret` with your client key.

Once you have the access token you can use it to make API calls by providing it in your headers as in the example.

```
curl -v -X GET https://someurl \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```

> Make sure to replace `Access-Token` with your client key.

<aside class="notice">
You must replace <code>Access-Token</code> with your granted access token.
</aside>

# Locations

The Location API allows you to fetch or set details about any locations that belong to your company.

## Get Location

Get a single location by using it's ID.

### Permissions

All employees for the company a location is part of have permission to view a location. 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

### Links

Links will be provided only if the user has sufficient permissions

Parameter | Permissions | Description
--------- | ----------- | -----------
edit | Admin | URL and method for editing a location
assign | Admin | URL and method for assigning users to a location 
delete | Admin | URL and method for deleting a location

```shell
curl "http://example.com/api/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "LocationName": "fac51",
    "BuildingName": "The Hacienda", 
    "Street": "15 Whitworth Street West",
    "Town": "Manchester",
    "County": "Greater Manchester",
    "Country": "United Kingdom",
    "Postcode": "M1 5DD" ,
    "_links":{
      "edit":{
        "href":"https://example.com/employee/44436/contract",
        "method":"PUT"
      }
    }
  }
```

## Get All Locations

## Create Location

## Update Location

## Delete Location

# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens/"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

