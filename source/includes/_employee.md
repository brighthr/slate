# Employee

The Employee API provides functionality for adding, listing and terminating employees for a BrightHR company.

## List Employees

Retrieves a list of all employees in your company.

### HTTP Request

`GET /v1/employee`

```shell
curl --location --request GET 'https://api.brighthr.com/v1/employee' \
  --header 'Authorization: Bearer access-token'
```

Make sure to replace `access-token` with your access token.

### HTTP Response

`200 OK`
```
[
    {
        "id": "00000000-0000-0000-0000-000000000000",
        "email": "ceo@company.tld",
        "firstName": "Peter",
        "lastName": "Jones",
        "jobTitle": "CEO",
        "profileImage": "https://www.gravatar.com/avatar/205e460b479e2e5b48aec07710c08d50",
        "terminated": false
    }
]
```

### Permissions

An active user bearer token is required.

Scope required: `tbc`


## List Employees by company

Retrieves a list of all employees in your company.

### HTTP Request

`GET /v1/employee`

```shell
curl --location --request GET 'https://api.brighthr.com/v1/employee/company/{companyId}' \
  --header 'Authorization: Bearer access-token'
```

Make sure to replace `access-token` with your access token.

### HTTP Response

`200 OK`
```
[
    {
        "id": "00000000-0000-0000-0000-000000000000",
        "email": "ceo@company.tld",
        "firstName": "Peter",
        "lastName": "Jones",
        "jobTitle": "CEO",
        "profileImage": "https://www.gravatar.com/avatar/205e460b479e2e5b48aec07710c08d50",
        "terminated": false
    }
]
```

### Permissions

An active user bearer token is required.

Scope required: `company:read` Must not have `sub` implying you are a service calling the API.
