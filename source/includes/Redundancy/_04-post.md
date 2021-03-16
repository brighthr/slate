## Create Redundancy

Creates a new redundancy process

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/redundancy/`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/redundancy' \
  --header "Authorization: Bearer Access-Token" \
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "RedundancyName": "Redundancy"
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only Admins (and Managers when manager access is enabled) can create Redundancies.

### Body parameters

Parameter | Description
--------- | -----------
RedundancyName | Unique name for the redundancy