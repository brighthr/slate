## Archive Redundancy

Creates a new redundancy process

### HTTP Request

`DELETE https://sandbox-api.brighthr.com/v1/redundancy/<ID>`

```shell
curl --location --request DELETE 'http://sandbox-api.brighthr.com/v1/redundancy/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only Admins (and Managers when manager access is enabled) can archive Redundancies.