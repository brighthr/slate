# Redundancy

The Redundancy API for redundancies.

</br>
</br>
</br>

## List Redundancies

Get a single location by using it's ID.

### HTTP Request

`GET https://sandbox-api.brighthr.com/v1/redundancy/<ID>`

```shell
curl "https://sandbox-api.brighthr.com/v1/redundancy/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8?deleted=true"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
{
    "id": "9b957330-caa0-453c-93d7-85dab5581673",
    "name": "area 5134",
    "createdAt": "2020-09-10T14:09:22.81",
    "createdById": "5a4715c8-a213-4af0-a252-94534799126d",
    "redundancyProcessId": "37d70fb0-1808-4c76-a72c-d2f9847dad8d",
    "createdByName": " ", "progress": [
        {
            "isCompleted": true,
            "updatedAt": "2020-09-10T14:09:29.74",
            "updatedById": "5a4715c8-a213-4af0-a252-94534799126d",
            "updatedByName": " ",
            "stageId": "bc8d7c71-f19c-4184-af4e-62d7540b20da",
            "redundancyId": "9b957330-caa0-453c-93d7-85dab5581673",
            "stageNumber": 1,
            "_links": {
                "UpdateStage":
                {
                    "href": "v1/redundancy/9b957330-caa0-453c-93d7-85dab5581673/stage/bc8d7c71-f19c-4184-af4e-62d7540b20da",
                    "method": "post"
                }
            }
        }]
}
```

## Post Redundancy

Create redundancy jouney.
<aside class="notice">
This section is <code>WIP</code>.
</aside>

## Get Manager Access

Check if managers have access to use redundancy navigator
<aside class="notice">
This section is <code>WIP</code>.
</aside>
</br>
</br>
</br>
