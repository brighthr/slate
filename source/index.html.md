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

Before you can integrate with our APIs, you must set up your development environment to get OAuth 2.0 client ID and secret credentials for the sandbox and live environments. You exchange these credentials for an access token that authorizes your REST API calls. To test your web and mobile apps, you create sandbox accounts.

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

### URL for Dev and Production

Development: https://bright-dev.azurefd.net/api/location  
Production: https://bright-prod.azurefd.net/api/location

## Get Location

Get a single location by using it's ID.

### HTTP Request

`GET https://bright-dev.azurefd.net/api/location/<ID>`

```shell
curl "https://bright-dev.azurefd.net/api/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8?deleted=true"
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
    "Postcode": "M1 5DD",
    "Employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://example.com/employee/44436/contract",
        "method":"PUT"
      }
    }
  }
```

### Permissions

All employees for the company a location is part of have permission to view a location. 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
deleted | false | If set to true, the result will also include locations that have been marked as deleted.

### Links

Links will be provided only if the user has sufficient permissions

Parameter | Permissions | Description
--------- | ----------- | -----------
edit | Admin | URL and method for editing a location
assign | Admin | URL and method for assigning users to a location 
delete | Admin | URL and method for deleting a location

## Get All Locations

Get all locations that are part of the logged in user's company.

### HTTP Request

`GET https://bright-dev.azurefd.net/api/location/`

```shell
curl "https://bright-dev.azurefd.net/api/location/?deleted=true"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
[
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "LocationName": "fac51",
    "BuildingName": "The Hacienda", 
    "Street": "15 Whitworth Street West",
    "Town": "Manchester",
    "County": "Greater Manchester",
    "Country": "United Kingdom",
    "Postcode": "M1 5DD",
    "Employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://example.com/employee/44436/contract",
        "method":"PUT"
      }
    }
  }
]
```

### Permissions

All employees for the company a location is part of have permission to view a location. 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
deleted | false | If set to true, the result will also include locations that have been marked as deleted.

### Links

Links will be provided only if the user has sufficient permissions

Parameter | Permissions | Description
--------- | ----------- | -----------
edit | Admin | URL and method for editing a location
assign | Admin | URL and method for assigning users to a location 
delete | Admin | URL and method for deleting a location

## Get Location For Employee

Gets a list of locations an employee is assigned to based on their ID

### HTTP Request

`GET https://bright-dev.azurefd.net/api/location/employee/<ID>`

```shell
curl "https://bright-dev.azurefd.net/api/location/employee/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2?deleted=true"
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
    "Postcode": "M1 5DD",
    "Employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://example.com/employee/44436/contract",
        "method":"PUT"
      }
    }
  }
```

### Permissions

All employees for the company a location is part of have permission to view a location. 

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the employee

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
deleted | false | If set to true, the result will also include locations that have been marked as deleted.

### Links

Links will be provided only if the user has sufficient permissions

Parameter | Permissions | Description
--------- | ----------- | -----------
edit | Admin | URL and method for editing a location
assign | Admin | URL and method for assigning users to a location 
delete | Admin | URL and method for deleting a location

## Create Location

Creates a location as part of the company the logged in user is part of.

### HTTP Request

`POST https://bright-dev.azurefd.net/api/location/`

```shell
curl --location --request POST 'http://localhost:7071/api/location' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "LocationName": "fac51",
      "BuildingName": "The Hacienda", 
      "Street": "15 Whitworth Street West",
      "Town": "Manchester",
      "County": "Greater Manchester",
      "Country": "United Kingdom",
      "Postcode": "M1 5DD"
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only users with the Admin role have permissions to create a location.

### Body parameters

Parameter | Description
--------- | -----------
LocationName | Unique name for the location
BuildingName | Building name
Street | Street name
Town | Name of the town or city
County | One of a set list of counties found here (TODO)...
Country | One of a set list of countries found here (TODO)...

## Update Location

Updates the address of a location. It will respond with a Bad Request should the jurisdiction of the location change and there are employees assigned to it. A jurisdiction will change if a change in county or country impacts the legislative jurisdiction. A list of jurisdictions and their associated countries and counties can be found here (TODO)...

### HTTP Request

`PUT https://bright-dev.azurefd.net/api/location/<ID>`

```shell
curl --location --request PUT 'http://localhost:7071/api/location/' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "LocationName": "fac51",
      "BuildingName": "The Hacienda", 
      "Street": "15 Whitworth Street West",
      "Town": "Manchester",
      "County": "Greater Manchester",
      "Country": "United Kingdom",
      "Postcode": "M1 5DD"
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only users with the Admin role have permissions to update a location.

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

### Body parameters

Parameter | Description
--------- | -----------
LocationName | Unique name for the location
BuildingName | Building name
Street | Street name
Town | Name of the town or city
County | One of a set list of counties found here...
Country | One of a set list of countries found here...

## Delete Location

Delete a location. All employees assigned to that location will become unassigned.

### HTTP Request

`DELETE https://bright-dev.azurefd.net/api/location/<ID>`

```shell
curl --request DELETE "https://bright-dev.azurefd.net/api/location/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Only users with the Admin role have permissions to delete a location.

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

## Assign Employees

Assigns a collection of employees to a location. Any users who were previously assigned, but are not present in the new list of assigned employees will be unassigned

### HTTP Request

`PUT https://bright-dev.azurefd.net/api/location/<ID>/assign`

```shell
curl --location --request PUT 'http://localhost:7071/api/location/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2/assign' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "employees":[
        "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
        "ABCDEE40-7163-4CCE-9E07-4DD4C288ABCD"
      ]
    }'
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Only users with the Admin role have permissions to assign to a location.

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the location

# Reports

The Report API allows you to generate reports for your company.

### URL for Dev and Production

Development: https://bright-dev.azurefd.net/api/report

Production: https://bright-prod.azurefd.net/api/report

## Timesheet

Generate a timesheet report for your team for the selected date range, with the option to filter by specific employees.

### HTTP Request

`POST https://bright-dev.azurefd.net/api/report/timesheet`

`POST https://bright-prod.azurefd.net/api/report/timesheet`

```shell
  curl --location --request POST 'https://bright-dev.azurefd.net/api/report/timesheet' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Start": "2020-01-01 00:00:00.0000000 +00:00",
      "End": "2020-01-08 00:00:00.0000000 +00:00",
      "FilterUserIds": ["A82DEE40-7163-4CCE-9E07-4DD4C2884FC2"]
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

All employees have permission to request a report. If `FilterUserIds` is not null, it must only contain guids for users which are subordinates of the requester, or the requester themself.

### Body parameters

Parameter | Description
--------- | -----------
Start | Start date and time in ISO 8601 format
End | End date and time in ISO 8601 format
FilterUserIds (Optional) | List of UserGuids to filter by, or null to get a timesheet for all subordinates and the requester

### Response

A 200 containing a .csv file stream.