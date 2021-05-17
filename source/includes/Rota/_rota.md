# Rota

The Rota API allows you to fetch or create rotas and shifts.

## Create Rota

Creates a new rota.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '{
      "name":"Test Rota",
      "startLocalDate":"2021-05-17",
      "duration":7
    }'
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
{
    "id": 580001,
    "guid": "5760d2ed-447b-4c88-af21-227f572f7d8b",
    "name": "Test Rota",
    "startDate": "2021-05-13",
    "duration": 7,
    "initialDuration": 7,
    "published": true,
    "inProgress": true,
    "employeeCount": 1,
    "totalShiftDuration": {
        "hours": 0,
        "minutes": 0
    },
    "_links": {
      "self": {
        "href": "rota/216426a6-8e66-42ac-95fd-f5742876d698"
      },
      "http://api.brighthr.com/rels/shift": {
        "href": "rota/216426a6-8e66-42ac-95fd-f5742876d698/Shift"
      },
      "http://api.brighthr.com/rels/publish": {
        "href": "rota/216426a6-8e66-42ac-95fd-f5742876d698/Publication"
      },
      "http://api.brighthr.com/rels/extend": {
        "href": "rota/216426a6-8e66-42ac-95fd-f5742876d698/Extension"
      },
      "http://api.brighthr.com/rels/week": {
        "href": "rota/216426a6-8e66-42ac-95fd-f5742876d698/Week"
      }
    }
}
```
### Permissions

Admins and managers have the ability to create rotas. 

### Body parameters

Parameter | Description
--------- | -----------
Name | A unique name for the new rota
StartDate | The start date of the rota
Duration | The number of days for the rota's repeating period. For a rota that repeats every week use a value of 7.

## Get Rota

Retrieves a Rota by its unique identifier.

### HTTP Request

`GET https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
{
    "id": 580001,
    "guid": "5760d2ed-447b-4c88-af21-227f572f7d8b",
    "name": "Test Rota",
    "startDate": "2021-05-13",
    "duration": 7,
    "initialDuration": 7,
    "published": true,
    "inProgress": true,
    "employeeCount": 1,
    "totalShiftDuration": {
        "hours": 8,
        "minutes": 0
    },
    "shifts": [
        {
            "start": "2021-05-13T09:00:00+01",
            "end": "2021-05-13T17:00:00+01",
            "breakDuration": {
                "hours": 0,
                "minutes": 0
            },
            "duration": {
                "hours": 8,
                "minutes": 0
            },
            "notes": "",
            "shiftStatus": "Accepted",
            "id": 200,
            "shiftGuid": "5fb7e292-74a4-453b-bdab-62575c56adb4",
            "_links": {
                "self": {
                    "href": "rota/5760d2ed-447b-4c88-af21-227f572f7d8b/shift/5fb7e292-74a4-453b-bdab-62575c56adb4",
                    "method": "get"
                },
                "update": {
                    "href": "rota/5760d2ed-447b-4c88-af21-227f572f7d8b/shift/5fb7e292-74a4-453b-bdab-62575c56adb4",
                    "method": "put"
                },
                "delete": {
                    "href": "rota/5760d2ed-447b-4c88-af21-227f572f7d8b/shift/5fb7e292-74a4-453b-bdab-62575c56adb4",
                    "method": "delete"
                }
            }
        }
    ],
    "_links": {
        "self": {
            "href": "rota/5760d2ed-447b-4c88-af21-227f572f7d8b",
            "method": "get"
        },
        "unpublish": {
            "href": "rota/5760d2ed-447b-4c88-af21-227f572f7d8b/unpublish"
        }
    }
}
```
### Permissions

Admins and managers have the ability to create copied rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaId | The Guid Id of the rota you want to copy

## Delete Rota

Deletes a rota.

### HTTP Request

`DELETE https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '{
      "name":"Test Rota",
      "startLocalDate":"2021-05-17",
      "duration":7
    }'
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to delete rotas. 

## Copy Rota

Creates a new rota with shifts copied from a specified rota.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaToCopyId:guid}/copy`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaToCopyId:guid}/copy' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '{
      "startDate": "2020-12-01",
      "name": "New Rota"
    }'
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
  {
    "id": "532E179F-3316-49B3-AB12-8FCF50FD7A28"
  }
```
### Permissions

Admins and managers have the ability to create copied rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
RotaToCopyId | The Guid Id of the rota you want to copy

### Body parameters

Parameter | Description
--------- | -----------
StartDate | Start Date of the new rota
Name | A unique name for the new rota

## Copy Period

Creates a rota's repeating period with shifts copied from the specified period. A period is a repeating number of days, which defults to 7 days.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaGuid:guid}/period`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaGuid:guid}/period' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '{
      "copyNotes": true,
      "indexOfRotaPeriodToCopy": 1
    }'
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to create copied rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaGuid | The Guid Id of the rota you want to copy

### Body parameters

Parameter | Description
--------- | -----------
copyNotes | Boolean value indicating if notes should be copied from the shifts in the period being copied from to the shifts created in the new period
indexOfRotaPeriodToCopy | An zero based integer index of periods within the rota. For example, to copy the first week set this value to 0.

## Extend Rota

Extends a rota by its period duration. For example a rota that is a week long, that is with a period of 7, adds another 7 days to the end of the rota.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/extend`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/extend' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to extend rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaId | The Guid Id of the rota you want to copy

## Shorten Rota

Shortens a rota by its period duration. For a rota with a repeating period of 7, removes the last 7 days including all shifts that start in those days.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/extend`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/extend' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to extend rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaId | The Guid Id of the rota you want to copy

## Publish Rota

Publishes a rota. This makes the rota visible to employees, and sends notifications about their shifts to them.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/publish`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/publish' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to publish rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaId | The Guid Id of the rota you want to copy

## Unpublish Rota

Publishes a rota. This makes the rota invisible to employees, and sends notifications about their shifts to them.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/unpublish`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaId:guid}/unpublish' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

### Permissions

Admins and managers have the ability to publish rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
rotaId | The Guid Id of the rota you want to copy


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