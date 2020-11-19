# POST Reference Guide

POST is used to enter new information into the server.

For the full version of the App, this section will be expanded to include additional menu items. 

For the purpose of this POC, only the burger meal is documented. 

The burger JSON object is included in the POST request which is sent to the kitchen. 

When an OK response is received, the order is printed in the kitchen so the cook can start cooking.

The General Putnam Motel Diner API contains the following POST references:

## POST/lunch/burgerMeal/burger Attributes

Attribute | Data Type | Req. | Description | Default
--- | --- | --- | --- | ---
bunType|string|Y|The type of bun for the burger. Either "none", "wholeWheat", "white", or "glutenFree".|"white"
condiment1|string|N|1st condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" – proceed to topping1. If condiment is selected, offer condiment2.|"none"
condiment2|string|N|2nd condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" – proceed to topping1. If condiment is selected, offer condiment3. |"none"
condiment3|string|N|3rd condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". If "none" – proceed to topping1. If condiment is selected, offer condiment4. |"none"
condiment4|string|N|4th condiment selection on the burger. Either "none", "ketchup", "mayo", "chili" or "secretSauce". For all selections, proceed to topping1, as maximum of 4 condiments are allowed. |"none"
main|string|Y|The main course for the meal. Either "burgerMeal", "salad" or "taco". |"burgerMeal"
pattyCook|string|Y|Describes requested level of doneness of the patty. Either "R" (rare), "MR" (medium rare), "M" (medium), "D" (done), "WD" (well done).|"M"
pattyQty|int|Y|Number of patties on the burger. Either 1 or 2. No patty is not an option.|1
pattyType|string|Y|Describes selected patty type. Either "beef", "lamb", or "veggie".|"beef"
pattyWeight|int|Y|Weight of the patty in grams. Either 150 or 300.|150
topping1|string|N|1st topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides. If topping1 is selected, offer topping2. |"none"
topping2|string|N|2nd topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides. If topping2 is selected, offer topping3. |"none"
topping3|string|N|3rd topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". If "none" – the burger order is complete, and the burgerMeal order should proceed to sides. If topping3 is selected, offer topping4. |"none"
topping4|string|N|4th topping selection on the burger. Either "none", "lettuce", "tomato", "pickles", or "cheese". For all selections, proceed to sides as the maximum number of toppings is 4.|"none"

## POST/lunch/burgerMeal/sides Attributes

Attribute|Data Type|Req.|Description|Default
--- | --- | --- | --- | ---
size|string|N|Describes the size of the 2nd side order for the burgerMeal. Size is either "large" or "extraLarge". If "none" – the sides order is complete, and the burgerMeal order should proceed to drink.|"large"
type|string|N|Describes the type of side order for the burgerMeal, either "none", "frenchFries", "coleslaw", or "onionRings". If "none" – the sides order is complete, and the burgerMeal order should proceed to drink. If side is ordered, proceed to side2. There is a maximum of 3 side orders for each burgerMeal.|"frenchFries"

## POST/lunch/burgerMeal/drink Attributes

Attribute|Data Type|Req.|Description|Default
--- | --- | --- | --- | ---
ice|boolean|Y|Indicates if the drink should have ice. Either "yes" or "no". Once selected, the burgerMeal order is complete, and the order can be sent to the kitchen.|"yes"
size|string|Y|The size of the cup, either "large" or "extraLarge".|"large"
type|string|N|Describes the drink selection, either "none", "Coke", "orangeJuice" or "mineralWater”. If "none" – the burgerMeal order is complete, and the order can be sent to the kitchen. If drink type is selected, proceed to drink size. |"Coke"

`Request Example (cURL)`

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
}
http://https://api.gpmd.com/orderingApp/burgerMeal/POC

````

## POST Response Codes

When a correct order is placed, the server replies to the app with an acknowledgement, either with an OK or an error. This is not displayed to the user.  

If the order is OK, the user will receive an order number. In case of an error, the user must be told what went wrong and how to fix the issue to complete the order.

`POST Response Example`

````
200 OK
````

