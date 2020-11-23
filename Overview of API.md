# General Putnam Motel Diner API

## Introduction

The owners of General Putnam Motel Diner are creating an app so that their customers can order their meals as Corona has caused the diner to close its' doors to the public. Using the app, customers will be able to place take-out orders.

In the future, once the diner re-opens to the public, the management wants to put the app on a tablet so that customers can order from their seats in the diner. 

The application will interface with the server-side ordering system which is sitting in the kitchen and prints out orders for the cooks. 

The API is used to interface between the app and the server.

Our company has been requested to provide a POC (proof of concept) for the app. 

If General Putnam Motel Diner management approves POC, they will pay for the final app.

## Authentication

To make an order, the customer needs to insert their full name, email address, and mobile phone number.

This information will be used to send the order status to the customer and the final bill.

Customers can choose whether they wish to receive promotional content.

## Errors

The General Putnam Motel Diner API follows standard HTTP status codes for success or failure of an API call. 

Status | Code Description 
--- | ---
200 - OK | Your meal was successfully ordered.
400 - Bad Request | Your order is incomplete. For example, pattyType is a required field, since you cannot order a burger without a patty.
401 - Unauthorized | The email address or mobile number does not exist.
402 - Request Failed | Your order timed out. Order was not completed within 15 minutes.
404 - Not Found | The main order does not yet exist in the menu. For example, salad or taco are not yet available for lunch on this POC.

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