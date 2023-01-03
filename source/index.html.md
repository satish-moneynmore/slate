---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ

- shell
- ruby
- python
- javascript

toc_footers:

- <a href='#'>Sign Up for a Developer Key</a>
- <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:

- errors

search: true

code_clipboard: true

meta:

- name: description
  content: Documentation for the Kittn API

---

# Introduction

Welcome to the Brand API documentation. The Brand API allows you to retrieve information about brands in the inventory
service.

# Authentication

The Brand API requires authentication using a SecretKey and an AccessKey. These keys can be obtained from the inventory
service team.

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.



`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Brands

## Get All Brands

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "brands": [
    {
      "id": "1",
      "slug": "brand-1",
      "name": "Brand 1",
      "brandImage": "https://example.com/brand-1.jpg",
      "cardImage": "https://example.com/card-1.jpg",
      "saveUptoPercentage": 10,
      "favourite": false
    },
    {
      "id": "2",
      "slug": "brand-2",
      "name": "Brand 2",
      "brandImage": "https://example.com/brand-2.jpg",
      "cardImage": "https://example.com/card-2.jpg",
      "saveUptoPercentage": 20,
      "favourite": true
    },
    ...
  ]
}

```

This endpoint retrieves all Brands.

### HTTP Request

`URL: https://api.saas.dev.moneynmore.net/inventory-service/api/v1/brand`

### Query Parameters

 Parameter | Default | Description                                    
-----------|---------|------------------------------------------------
 page      | false   | page number to return result.                  
 size      | false   | page size to return number of results in page. 

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Brand

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific Brand.

<aside class="warning">By default, the response will contain information about all the brands you have access to. You can request information for one brand at a time using the brand parameter.</aside>

### HTTP Request

`URL: https://api.saas.dev.moneynmore.net/inventory-service/api/v1/brand/{id}`

### Brands API response

 Parameter                 | Description                                               |
---------------------------|-----------------------------------------------------------
| id                        | Unique identifier for the brand                           |
| slug                      | Unique brand identifier                                   |
| name                      | Brand name                                                |
| favourite                 | Whether the brand is a favourite or not                   |
| description               | A brief description of the brand                          |
| balanceEnquiryUrl         | URL for checking the balance on a brand's card            |
| deliveryMethod            | List of methods for delivering brand's cards              |
| countriesServed           | List of countries served by the brand                     |
| currencies                | Currencies accepted by the brand                          |
| categories                | List of categories the brand belongs to                   |
| brandImage                | URL for an image representing the brand                   |
| cardImage                 | URL for an image of the brand's card                      |
| canCheckStock             | Whether the brand's stock can be checked or not           |
| fixedDenominationsList    | List of fixed denominations for the brand's cards         |
| openLowerLimit            | Lower limit for open denominations for the brand's cards  |
| openHigherLimit           | Higher limit for open denominations for the brand's cards |
| minorUnit                 | Minor unit for the brand's cards                          |
| percentageDiscount        | Percentage discount on the brand's cards                  |
| expiryDatePolicy          | Policy for expiry dates on the brand's cards              |
| redemptionInstructionsURL | URL for redemption instructions for the brand's cards     |
| termsAndConditionsURL     | URL for the terms and conditions for the brand's cards    |
| termsAndConditionsCopy    | Copy of the terms and conditions for the brand's cards    |
| redeemMethods             | List of methods for redeeming the brand's cards           |
| barcode                   | Barcode for the brand's cards                             |
| createdAt                 | Timestamp for when the brand was created                  |
| updatedAt                 | Timestamp for when the brand was last updated             |
| tagIds                    | List of tag IDs for the brand                             |
| tags                      | List of tags for the brand                                |

### Delivery Methods

A delivery method defines the way in which a gift card can be provided to you.

### Here are the possible values:

 Parameter | Description                                                            |
-----------|------------------------------------------------------------------------
| code      | The raw gift card code/number.                                         |
| url       | A hosted html template containing the gift card.                       |
| wrapped   | A hosted interactive 'unwrapping' experience containing the gift card. |
| email     | Only used for the Reward Pass product.                                 |

```json
"delivery_methods": [
"code",
"url",
"wrapped"
]
```

### Categories

Each brand will have one or more categories associated with it. A brand's assigned categories will be returned in the
response from the Brands API endpoint.

 Category code      | Category name    
--------------------|------------------
 baby               | Baby             
 beauty             | Beauty           
 books              | Books            
 cars               | Cars             
 charity            | Charity          
 craft              | Craft            
 cryptocurrency     | Cryptocurrency   
 cycling            | Cycling          
 department-store   | Department Store 
 fashion            | Fashion          
 electronics        | Electronics      
 food-and-drink     | Food & Drink     
 gaming             | Gaming           
 home               | Home             
 jewellery          | Jewellery        
 music              | Music            
 other              | Other            
 school-vouchers    | School Vouchers  
 sports             | Sports           
 supermarket        | Supermarket      
 toys               | Toys             
 travel-and-leisure | Travel & Leisure 
 tv-and-movies      | TV & Movies      

```json
"categories": [
"food-and-drink",
"tv-and-movies"
]
```

### Fixed demoninations

Some brands do not support 'open value' requests and instead offer a list of available values we call 'denominations'.

These values apply to both digital and physical gift cards.

```json
"denominations": [
10.00,
20.00,
25.00,
50.00,
100.00
]
```

### Redemption Methods

Redemption methods describe how the end user is able to use/spend/redeem the gift card.

These values apply to both digital and physical gift cards.

 Redemption method code | Description                               
------------------------|-------------------------------------------
 online                 | This card can be redeemed online.         
 instore                | This card can be redeemed in-store.       
 phone                  | This card can be redeemed over the phone. 

```json
"redemption_methods": [
"online",
"instore"
]
```
