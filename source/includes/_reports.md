# Reports

</br>
</br>
</br>
The Report API allows you to generate reports for your company.

### URL for Reports Dev and Production

Development: https://bright-api-sand.azurefd.net/v1/report

Production: https://bright-api-prod.azurefd.net/v1/report

## Timesheet
Generate a timesheet report for your team for the selected date range, with the option to filter by specific employees and include payroll information.
### HTTP Request
`POST https://bright-api-sand.azurefd.net/v1/report/timesheet`
`POST https://bright-api-prod.azurefd.net/v1/report/timesheet`

```shell
  curl --location --request POST 'https://bright-dev.azurefd.net/api/report/timesheet' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Start": "2020-01-01 00:00:00.0000000 +00:00",
      "End": "2020-01-08 00:00:00.0000000 +00:00",
      "FilterUserIds": ["A82DEE40-7163-4CCE-9E07-4DD4C2884FC2"],
      "IsSummary": "false",
      "IncludeBreakDowns": "false",
      "IncludePayrollDetails": "false"
    }'
```

> Make sure to replace `Access-Token` with your client key.

### Permissions
All employees have permission to request a report. If `FilterUserIds` is not null, it must only contain guids for users which are subordinates of the requester, or the requester themself.

### Body parameters
Parameter | Description
--------- | -----------
Start | Start date and time in ISO 8601 format
End | End date and time in ISO 8601 format
FilterUserIds (Optional) | List of UserGuids to filter by, or null to get a timesheet for all subordinates and the requester
IsSummary | `true` exlcudes details of breaks and provides totalled hours worked per day.
 | `false` includes details of breaks and provides total hours per shift.
IncludeBreakdowns |  Includes weekly and total breakdowns for each employee
IncludePayrollDetails |  Includes `Payroll Number`, `National Insurance`, `Employee Address` columns

### Response
A 200 containing a .csv file stream.

## Expense Report

### HTTP Request
`POST https://sandbox-api.brighthr.com/v1/report/pop`
</br>
`POST https://api.brighthr.com/v1/report/pop`

```shell
  curl --location --request POST 'https://bright-dev.azurefd.net/api/report/pop' \
  --header "Authorization: Bearer Access-Token"
  --header 'Content-Type: application/json' \
  --data-raw '  {
      "Start": "2020-01-01",
      "End": "2020-01-08",
      "PaidExpenses": "true",
    }'
```

> Make sure to replace `Access-Token` with your client key.

### Permissions
Any admin or manager can produce this report. All subordinates' expenses will be included. `Start` and `End` are only required when `PaidExpenses` is `true`.

### Body parameters
Parameter | Description
--------- | ----------
Start | Start date
End | End date
PaidExpenses | `true` Report will contain only paid expenses</br>`false` Report will contain only approved expenses

### Response
A 200 containing a .csv file stream.

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