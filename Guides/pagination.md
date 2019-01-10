A number of resources have support for pagination of responses. These list APIs will share a common structure by taking the following parameters: *sortOrder*, *offset* and *pageSize*

### Arguments
***
sortOrder    - ASC or DESC
***
offset         - Starting page number.
***
pageSize    - Number of returned resources per page.
***

### APIs using pagination

[List all bank accounts](1_0_0#/http/api-endpoints/beneficiary-bank-accounts/list-bank-accounts)

[Search transactions](1_0_0#/http/api-endpoints/transactions/search-transactions)

[View a statement of transactions](1_0_0#/http/api-endpoints/statements/get-statement)