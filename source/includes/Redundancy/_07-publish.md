## Publish Redundancy

Allows other admins in the company to view the redundancy

### HTTP Request

`DELETE https://sandbox-api.brighthr.com/v1/redundancy/<ID>/publish`

```shell
curl --location --request DELETE 'http://sandbox-api.brighthr.com/v1/redundancy/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8/publish' \
  --header "Authorization: Bearer Access-Token" \
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "IsVisible": true
    }'
```
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Only Admins (and Managers when manager access is enabled) can publish Redundancies that they created.