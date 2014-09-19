#Catch JSON messages
---
###2DM Sticker Redemption
---


#### Send user validation code

```javascript
    Method:
        POST
    
    URL:
        '<server>/validate'

    Request body:
    
        {
          "msisdn": integer,
          "voucher_code": string
        }
        
    Example request:
        {
            "msisdn": 0221053188,
            "voucher_code": "JMS52827KKS"
        }
    
    Responses
    
        200:
            Success
        4XX:
            User error
        5XX:
            Server error
        
        body:
            {
                "message": string
            }
            
    Example successful response:
        
        HTTP Status: 200
        {
            "message": "text message sent"
        }
        
        
    Example failure response:
        
        HTTP Status: 400
        {
            "message": "Not a valid number"
        }
        
```

#### Redeem prize

```javascript
    Method:
        POST
    
    URL:
        '<server>/redeem'

    Request body:
    
        {
          "msisdn": integer,
          "voucher_code": string,
          "security_code": string
        }
        
    Example request:
        
        {
            "msisdn": 0221053188,
            "voucher_code": "JMS52827KKS"
            "security_code": "225KLZ"
        }
    
    Responses
        200:
            Success
        401:
            Invalid security code
        4XX:
            User error
        5XX:
            Server error
        
        Request body:
            
            {
                "message": string
                "prize":{
                    "title" : string,
                    "type" : string,
                    "description" : string,
                }
            }
   
        Example Successful response:
            
            HTTP Status: 200
            {
                "message": "prize redeemed"
                "prize":{
                    "title" : "500mb",
                    "type" : "data",
                    "description" : "NZ carryover data",
                }
            }
    
        Example Failure responses:
            
            HTTP Status: 400
            {
                "message": "Sorry this code has already been redeemed"
                "prize": null
            }
            
            HTTP Status: 400
            {
                "message": "Security code does not match please try again"
                "prize": null
            }
   
        
```
