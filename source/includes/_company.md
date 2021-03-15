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
  --data-raw '{
	  "name":"Company ABC",
	  "countryCode":"GB",
	  "leadType":"BuyItNow",
	  "industry":"Leisure",
	  "externalReference": "BRHR1234",
	  "cdsId": 1234,
	  "salesReference": "1234",
	  "contact": {
		  "firstName":"First",
		  "lastName":"Last",
		  "email":"demo@demo.com",
		  "phone":"01610000000",
		  "mobile":"0700000000"
	  },
	  "subscription": {
		  "start": "2020-08-07",
		  "end": "2021-08-06",
		  "seats": 3,
		  "package": "connect"
	  }
}'
```
Make sure to replace `access-token` with your own access token.

### HTTP Response

`201 Created`
```
{
    "id": "108c3786-a628-4d48-81c1-9abb2cc23e45",
    "contact": {
        "id": "c09320a4-24e3-4c20-bb21-aa80882143ca"
    },
    "_links": {
        "create-account": {
            "href": "https://app.brighthr.com/reseller-signup/c09320a4-24e3-4c20-bb21-aa80882143ca"
        }
    }
}
```

### Permissions

Scope required: `subscription:write`


## List Companies

Lists all companies in Bright.

### HTTP Request

`GET /v1/company`

```shell
curl --location --request POST 'https://api.brighthr.com/v1/company' \
  --header "Authorization: Bearer access-token"
```
Make sure to replace `access-token` with your own access token.

### HTTP Response

`200 OK`
```
[
	{
		"id":"",
		"cdsId":"",
		"industry":"",
		"leadType":"",
		"name":"",
		"externalReference":"",
		"salesReference":"",
		"tenant":""
	}
]
```

### Permissions

Scope required: `company:read`