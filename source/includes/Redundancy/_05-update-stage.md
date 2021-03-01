## Update Redundancy Stage

Updates a given stage of the redundancy

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/redundancy/<ID>/stage/<STAGE-ID>`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/redundancy//stage/' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  ```

> Make sure to replace `Access-Token` with your client key.

### Permissions

Only Admins (and Managers when manager access is enabled) can create Redundancies.

### Body parameters

Parameter | Description
--------- | -----------
RedundancyName | Unique name for the redundancy