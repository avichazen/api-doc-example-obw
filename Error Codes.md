## Errors

The General Putnam Motel Diner API follows standard HTTP status codes for success or failure of an API call. 

Status | Code Description 
--- | ---
200 - OK | Your meal was successfully ordered.
400 - Bad Request | Your order is incomplete. For example, pattyType is a required field, since you cannot order a burger without a patty.
401 - Unauthorized | The email address or mobile number does not exist.
402 - Request Failed | Your order timed out. Order was not completed within 15 minutes.
404 - Not Found | The server could not find what was requested. This is only a POC (proof of concept), and not all menu options exist.
