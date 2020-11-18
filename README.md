# General Putnam Motel Diner API 

## Introduction

The owners of General Putnam Motel Diner are creating an app so that their patrons can order their meals as Corona has caused the diner to close its doors to the public. Using the app, customers will be able to place take-out orders. 

In the future, the management wants to put the app on a tablet so that patrons can order from their seats in the diner (once the diner opens to the public). The application will interface with the server-side ordering system which is sitting in the kitchen and prints out orders for the cooks. 
The API is used to interface between the app and the server.

Our company has been requested to provide a POC (proof of concept) for the app. If General Putnam Motel Diner management approves POC, they will pay for the final app.

## Authentication

To make an order, the customer needs to insert their name, surname, email address, and mobile phone number.
This information will be used to send order status to the customer and the final bill.
Customers can choose whether they wish to receive promotional content.

## Errors

The General Putnam Motel Diner API follows standard HTTP status codes for success or failure of an API call. 

Status | Code Description 
--- | ---
200 - OK | Your meal was successfully ordered.
400 - Bad Request | Your order was unacceptable. For example, the field is pattyType a required field, since you cannot order a burger without a patty.
404 - Not Found | The main order does not yet exist in the menu.
402 - Request Failed | Your order timed out. Order was not completed within 15 minutes.

## Rate Limits 

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

# POST Reference Guide

POST is used to enter new infomration into the server.
For the full version of the App, this section will be expanded to include additional menu items. 
For the purpose of this POC, only the burger meal is documented. 
The burger JSON object is included in the POST request which is sent to the kitchen. 
When an OK response is received, the order is printed in the kitchen so the cook can start cooking.

The General Putnam Motel Diner API contains the following POST references:

## POST/lunch/burgerMeal/burger Attributes

Attribute | Data Type | Req. | Description | Default
--- | --- | --- | --- | ---
bunType|string|Y|The type of bun for the burger. Either "none", "wholeWheat", "white", or "glutenFree".|"white"
condiment1|string|N|1st condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" –proceed to topping1. If condiment is selected, offer condiment2.|"none"
condiment2|string|N|2nd condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" –proceed to topping1. If condiment is selected, offer condiment3. |"none"
condiment3|string|N|3rd condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" –proceed to topping1. If condiment is selected, offer condiment4. |"none"
condiment4|string|N|4th condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". For all selections, proceed to topping1, as maximum of 4 condiments are allowed. |"none"
main|string|Y|The main course for the meal. Either "burgerMeal", "salad" or "taco". |"burgerMeal"
pattyCook|string|Y|Describes requested level of doneness of the patty. Either "R" (rare), "MR" (medium rare), "M" (medium), "D" (done), "WD" (well done).|"M"
pattyQty|int|Y|Number of patties on the burger. Either 1 or 2. No patty is not an option.|1
pattyType|string|Y|Describes selected patty type. Either "beef", "lamb", or "veggie".|"beef"
pattyWeight|int|Y|Weight of the patty in grams. Either 150 or 300.|150
topping1|string|N|1st topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides. |"none"
topping2|string|N|2nd topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides.|"none"
topping3|string|N|3rd topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides.|"none"
topping4|string|N|4th topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides.|"none"

## POST/lunch/burgerMeal/sides Attributes

Attribute|Data Type|Req.|Description|Default
--- | --- | --- | --- | ---
size|string|N|Describes the size of the 2nd side order for the burgerMeal. Size is either "large" or "extraLarge". If "none" – the sides order is complete, and the burgerMeal order should proceed to drink.|"large"
type|string|N|Describes the type of side order for the burgerMeal, either "none", "frenchFries", "coleslaw", or "onionRings". If "none" – the sides order is complete, and the burgerMeal order should proceed to drink. If side is ordered, proceed to side2. There is a maximum of 3 side orders for each burgerMeal.|"frenchFries"

## POST/lunch/burgerMeal/drink Attributes

Attribute|Data Type|Req.|Description|Default
--- | --- | --- | --- | ---
size|string|Y|The size of the cup, either "large" or "extraLarge".|"large"
type|string|N|Describes the drink selection, either "none", "Coke", "orangeJuice" or "mineralWater”. If "none" – the burgerMeal order is complete, and the order can be sent to the kitchen. If drink type is selected, proceed to drink size. |"Coke"
ice|boolean|Y|Indicates if the drink should have ice. Either "yes" or "no". Once selected, the burgerMeal order is complete, and the order can be sent to the kitchen.|"yes"

> Request Example (cURL)

````

curl -H "Content-Type: application/json" -X POST -d'{
   "mealType":"lunch",
   "mealItem":{
  	"main":"burgerMeal",
  	"burger":{
     	"pattyType":"”beef”",
     	"pattyQty":1,
     	"pattyWeightG":300,
     	"pattyCook":"MR",
     	"bunType":"wholeWheat",
     	"condiment1":"ketchup",
     	"condiment2":"secretSauce",
     	"topping1":"lettuce",
     	"topping2":"pickles",
     	"topping3":"None",
     	"topping4":"None"
  	},
  	"sides":{
     	"side1":{
        	"type":"frenchFries",
        	"size":"large"
     	},
     	"side2":{
        	"type":"none",
        	"size":""
     	}
  	},
  	"drink":{
     	"type":"Coke",
     	"size":"large",
     	"ice":"yes"
  	}
   }
}'
http://URL/dpmd/orderingApp/POC

````

## POST Response Codes

When a correct order is placed, the server replies to the app with an acknowledgement, either with an OK or an error. This is not displayed to the user.  

> POST Response Example

````
200 OK
````

# GET Reference Guide

GET is used to get information that already exists in the server.

## GET Retrieve the currently available meal 

Retrieves the meal type that is available at the current time. 

## GET/meal

There are no arguments. 

### Response Schema 

Attribute|Data Type|Description
---|---|---|
mealType|string|The meal that you can order. 
timestamp|date|The time of the request.

> Response Example

````

{ 
“mealType”: “breakfast”, 
“timestamp”: “2020-01-21T07:44:45-05:00” 
} 

````
## GET/tableNo

This is the call which is sent when the server wants to get the bill. The GET request includes the table number. The order number is included in the response. Take-out orders are table 99. When this is printed, the customer can pay the bill.

### Response Schema 

Attribute|Data Type|Description
---|---|---
cost|float|The cost of the item.
orderNum|int|The unique identifier number of the order.
timestamp|date|The time of the request, a unique identifier generated by the date of the CPU.
type|string|The requested order. Either "burgerMeal", "salad", or "taco".

> Response Example 

````

curl -X GET "http://URL/tableNo?id=99"
# response
{
   "orderNum":123,
   "timestamp":"2020-01-21T07:44:45-05:00",
   "Item1":{
  	"ItemOrdered":{
     	"type":"burgerMeal",
     	"Cost":10.99
  	}
   }
   "Item2":{
  	"ItemOrdered":{
     	"type":"salad",
     	"Cost":9.50
  	}
   }
}

````
