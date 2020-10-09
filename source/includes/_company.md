# Company

The Company API provides functionality for managing BrightHR subscriptions, and can be used by company administrators, BrightHR and our partners.
It handles registering new companies, sending signup email reminders and managing subscription dates.

## Create a new Company

Registers a new BrightHR company and subscription details.

### HTTP Request

`POST /v1/company`

```shell
curl --location --request POST 'https://api.brighthr.com/v1/company' \
  --header "Authorization: Bearer access-token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Name": "Demo Company"
    }'
```
> Make sure to replace `Access-Token` with your client key.

### Permissions

Scope required: `subscription:write`

### Body parameters

Parameter | Description
--------- | -----------
Name | The company name

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
