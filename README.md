# General Putnam Motel Diner API

Adapted from [Alex Fiedler](https://www.linkedin.com/feed/update/urn:li:activity:6626465471241732096/) 

## Introduction

The owners of General Putnam Motel Diner are creating an app so that their customers can order their meals as Corona has caused the diner to close its doors to the public. Using the app, customers will be able to place take-out orders.

In the future, once the diner re-opens to the public, the management wants to put the app on a tablet so that customers can order from their seats in the diner. 

The application will interface with the server-side ordering system which is sitting in the kitchen and prints out orders for the cooks. 

The API is used to interface between the app and the server.

Our company has been requested to provide a POC (proof of concept) for the app. 

If General Putnam Motel Diner management approves POC, they will pay for the final app.

# Authentication

To make an order, there is an authentication process.
See here for [Authentication](https://github.com/avichazen/api-doc-example-obw/blob/main/Authentication.md)

# Error Codes

The General Putnam Motel Diner API follows standard HTTP status codes for success or failure of an API call.  
See here for [Error Codes](https://github.com/avichazen/api-doc-example-obw/blob/main/Error%20Codes.md)

## Order Limits 

The General Putnam Motel Diner API supports sending multiple orders in a single request, with a maximum of 3 orders per request. 

## Content Type

Accept: application/json

Content-Type: application/json

## Dates & Times

All times are represented in Eastern Standard Time (EST).
All dates are in ISO 8601 format: YYYY-MM-DDThh:mmTZD

## Mealtimes
Each meal type has a specific time range in which you can order it. 
For the purpose of this POC, the default mealtime is lunch.

Meal Type | ISO 8601 Time Range | Time
--- | --- | ---
Breakfast|YYYY-MM-DDT04:00:00-05:00 - YYYY-MM-DDT11:59:59-05:00|04:00 - 11:59
Lunch|YYYY-MM-DDT12:00:00-05:00 - YYYY-MM-DDT16:59:59-05:00|12:00 - 16:59
Dinner|YYYY-MM-DDT17:00:00-05:00 - YYYY-MM-DDT11:59:59-05:00 |17:00 - 23:59

## Base URL

https://api.gpmd.com

# Resources 

The General Putnam Motel Diner API contains the following resources:
* [GET Reference Guide](https://github.com/avichazen/api-doc-example-obw/blob/main/References/GET%20Reference%20Guide.md)
* [POST Reference Guide](https://github.com/avichazen/api-doc-example-obw/blob/main/References/POST%20Reference%20Guide.md)

# Workflow for Front End Developers

![simple workflow](https://user-images.githubusercontent.com/70967800/101278197-905b0780-37c2-11eb-82d4-b8b6e9190b61.png)
