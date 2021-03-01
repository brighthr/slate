## Get Manager Access

Checks if managers have access to use redundancy navigator

### HTTP Request

`GET` `https://sandbox-api.brighthr.com/v1/redundancy/access`

```shell
curl "https://sandbox-api.brighthr.com/v1/redundancy/access" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token" \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
{
    "isVisibleToManagers": true
}
```

## Update Manager Access

Enables or disables managers' access to Redundancies.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/redundancy/access`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/redundancy/access' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "IsVisibleToManagers": true
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only Admins can update manager access.

### Body parameters

Parameter | Description
--------- | -----------
IsVisibleToManagers | true or false
