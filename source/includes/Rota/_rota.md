# Rota

The Rota API allows you to fetch or create rotas and shifts.

## Copy Rota

Creates a new rota with shifts copied from a specified rota.

### HTTP Request

`POST https://sandbox-api.brighthr.com/v1/rota/{rotaToCopyId:int}/copy`

```shell
curl --location --request POST 'http://sandbox-api.brighthr.com/v1/rota/{rotaToCopyId:int}/copy' \
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
    "id": 2
  }
```
### Permissions

Admins and managers have the ability to create copied rotas. 

### URL Parameters

Parameter | Description
--------- | -----------
RotaToCopyId | The integer Id of the rota you want to copy

### Body parameters

Parameter | Description
--------- | -----------
StartDate | Start Date of the new rota
Name | A unique name for the new rota

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