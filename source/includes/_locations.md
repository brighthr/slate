# Locations

The Location API allows you to fetch or set details about any locations that belong to your company.

## Get Location

Get a single location by using it's ID.

### HTTP Request

`GET https://sandbox-api.brighthr.com/v1/location/<ID>`

```shell
curl "https://sandbox-api.brighthr.com/v1/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8?deleted=true"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "name": "fac51",
    "buildingName": "The Hacienda",
    "street": "15 Whitworth Street West",
    "townCity": "Manchester",
    "county": "Greater Manchester",
    "country": "United Kingdom",
    "postcode": "M1 5DD",
    "employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://sandbox-api.brighthr.com/v1/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
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

`GET https://sandbox-api.brighthr.com/v1/location/`

```shell
curl "https://sandbox-api.brighthr.com/v1/location/"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
[
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "name": "fac51",
    "buildingName": "The Hacienda",
    "street": "15 Whitworth Street West",
    "townCity": "Manchester",
    "county": "Greater Manchester",
    "country": "United Kingdom",
    "postcode": "M1 5DD",
    "employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://sandbox-api.brighthr.com/v1/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
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

`GET https://sandbox-api.brighthr.com/v1/location/employee/<ID>`

```shell
curl "https://sandbox-api.brighthr.com/v1/location/employee/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2?deleted=true"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "name": "fac51",
    "buildingName": "The Hacienda",
    "street": "15 Whitworth Street West",
    "townCity": "Manchester",
    "county": "Greater Manchester",
    "country": "United Kingdom",
    "postcode": "M1 5DD",
    "employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ],
    "_links":{
      "edit":{
        "href":"https://sandbox-api.brighthr.com/v1/location/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
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

`POST https://sandbox-api.brighthr.com/v1/location/`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/location' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Name": "fac51",
      "BuildingName": "The Hacienda",
      "Street": "15 Whitworth Street West",
      "TownCity": "Manchester",
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
TownCity | Name of the town or city
County | One of a set list of counties found here (TODO)...
Country | One of a set list of countries found here (TODO)...

## Update Location

Updates the address of a location. It will respond with a Bad Request should the jurisdiction of the location change and there are employees assigned to it. A jurisdiction will change if a change in county or country impacts the legislative jurisdiction. A list of jurisdictions and their associated countries and counties can be found here (TODO)...

### HTTP Request

`PUT https://sandbox-api.brighthr.com/v1/location/<ID>`

```shell
curl --location --request PUT 'http://sandbox-api.brighthr.com/v1/location/' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Name": "fac51",
      "BuildingName": "The Hacienda",
      "Street": "15 Whitworth Street West",
      "TownCity": "Manchester",
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
TownCity | Name of the town or city
County | One of a set list of counties found here...
Country | One of a set list of countries found here...

## Delete Location

Delete a location. All employees assigned to that location will become unassigned.

### HTTP Request

`DELETE https://sandbox-api.brighthr.com/v1/location/<ID>`

```shell
curl --request DELETE "https://sandbox-api.brighthr.com/v1/location/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2"
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

`PUT https://sandbox-api.brighthr.com/v1/location/<ID>/assign`

```shell
curl --location --request PUT 'http://sandbox-api.brighthr.com/v1/location/A82DEE40-7163-4CCE-9E07-4DD4C2884FC2/assign' \
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


## Get All Locations by CompanyID

Get all locations for a company.

### HTTP Request

`GET https://sandbox-api.brighthr.com/v1/location/company/{companyId}`

```shell
curl "https://sandbox-api.brighthr.com/v1/location/company/{companyId}"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
[
  {
    "id": "0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8",
    "name": "fac51",
    "buildingName": "The Hacienda",
    "street": "15 Whitworth Street West",
    "townCity": "Manchester",
    "county": "Greater Manchester",
    "country": "United Kingdom",
    "postcode": "M1 5DD",
    "employees": [
      "A82DEE40-7163-4CCE-9E07-4DD4C2884FC2",
      "b336c43e-18ae-4bd6-9961-817dee5f54dd"
    ]
  }
]
```

### Permissions

Only service to services calls with the scope of `location:read` can access this endpoint.

### URL Parameters

Parameter | Description
--------- | -----------
CompanyID | The ID of the company

</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
