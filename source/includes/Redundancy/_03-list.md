## List Redundancies

List all redundancies that either are yours or have been shared with you (can only be shared with other admins)

### HTTP Request

`GET` `https://sandbox-api.brighthr.com/v1/redundancy`

```shell
curl "https://sandbox-api.brighthr.com/v1/redundancy" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token" \
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns JSON structured like this:

```json
[
  {
    "id": "9b957330-caa0-453c-93d7-85dab5581673",
    "name": "area 51",
    "createdAt": "2020-09-10T14:09:22.81",
    "createdById": "5a4715c8-a213-4af0-a252-94534799126d",
    "redundancyProcessId": "37d70fb0-1808-4c76-a72c-d2f9847dad8d",
    "createdByName": "user-name",
    "progress": [
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
        },]
  },
...
]
```

