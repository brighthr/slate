## Put Redundancy - FolderId

Assigns a folderId to a saved redundancy, linking the redundancy and its documents folder.

`PUT`
`https://sandbox-api.brighthr.com/v1/redundancy/<ID>/folder`

```shell
curl "https://sandbox-api.brighthr.com/v1/redundancy/0ceeb215-c6d6-4aaa-8586-4184cbb8ccd8/folder"
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer Access-Token"
```
> Make sure to replace `Access-Token` with your client key.
> The above command returns 200:
> Payload must contain a valid FolderId Guid:

```json
{
    "folderId": "9b957330-caa0-453c-93d7-85dab5581673"
}
```