---
title: API Reference

language_tabs:
  - shell
  - php

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the DNA API! You can use our API to access DNA API endpoints, which can get information on various elements customers, devices, and billing in our database.

We have language bindings in Shell and PHP we also have <a href='https://www.getpostman.com/collections/af70b4327c9f4ded36f5'>Postman</a> for you to test the methods without writing code! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


This example API documentation page was created with [Slate](https://github.com/tripit/slate). 

# API Flow

The Api offers different methods here are some flow examples so you can visualize how the information will flow:

## Flow Diagram Legend

<img src="images/legend.png" alt="Legend">

## Create Client Method

<img src="images/client.png" alt="Client">

## Activate Client Method

<img src="images/activate.png" alt="Activate">

## Suspend Client Method

<img src="images/suspend.png" alt="Suspend">

## Create Device Method

<img src="images/device.png" alt="Device">

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://staging.api.nexogy.com/api/oauth/token?grant_type=password&client_id=<value>&client_secret=<value>&username=<value>&password=<value>&scope=<value>"
  -H "Accept: application/json"
```

```php

```

> Make sure to replace the required `<value>` with the information provided.

> The above command returns a JSON structured like this:

```json
[
  {  
     "token_type":"Bearer",
     "expires_in":1200,
     "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2",
     "refresh_token":"kvwLi6kTeq7DGbfsKLVvz/6zaCioe8Vk50x1QdlHJDFp4thYzPj5v"
  }
]
```

<aside class="warning">It is very important that in order for this documentation to work, you must have requested access to the API and recieved the following information: </aside>

Key | Value | Description
--------- | ------- | -----------
grant_type | password | This value is constant.
client_id | ????? | Once you've been approved to use our API you'll receive this value.
client_secret | ?????| Once you've been approved to use our API you'll receive this value.
username | ????? | Once you've been approved to use our API you'll receive this value.
password | ????? | Once you've been approved to use our API you'll receive this value.
scope | ????? | Once you've been approved to use our API you'll receive this value.

Once you have the values described above you can make the API calls using your <code>access_token</code> and the <code>token_type</code> .
To help with your development use Postman and add the following [Collection](http://example.com/developers).

DNA API expects for the <code>token_type</code> and <code>access_token</code> to be included in all API requests to the server in a header that looks like the following:

`Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2`

<aside class="notice">
You must replace <code>`values`</code> with your provided values. and add the <code>token_type</code> and <code>access_token</code> as values for the <code>Authorization</code>headers for all your API calls.
Additionally use the <code>Accept:application/json</code> Headers for every API call.
</aside>

# Client

## Create a Client

> To Create a new client, use this code:

```shell
curl "https://staging.api.nexogy.com/api/residential/client?email=<value>&
first_name=<value>&last_name=<value>&zipcode=<value>&address=<value>&address2=<value>&sameBillingAddress=<values>&billing_zipcode=<value>&billing_address=<value>&billing_address2=<value>&has_subreseller_id=<value>&subreseller_id=<value>&start_billing_date=<value>&did_porting=<value>&did_number=<value>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/client';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Populate array with parameters
$data['email'] = 'example@mail.com';
$data['first_name'] = 'John';
$data['last_name'] = 'Doe';
$data['zipcode'] = '12345';
$data['address'] = 'Client address';
$data['address2'] = 'Client address 2';
$data['sameBillingAddress'] = 1;
$data['has_subreseller_id'] = 1;
$data['subreseller_id'] = '123';
$data['billing_zipcode'] = '12345';
$data['start_billing_date'] = '06/08/2017';
$data['did_porting'] = 0;
$data['did_number'] = '3052304777';

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);
curl_setopt($c, CURLOPT_POSTFIELDS, http_build_query($data));

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "client": {
      "id": 92769,
      "ns_domain": "kerryking2.com"
    },
    "taxes": {
            "breakdown": [
                {
                    "tax_name": "FL COMMUNICATIONS SERVICES TAX",
                    "percent_taxable": "1.0000"
                },
                {
                    "tax_name": "FL 911 SURCHARGE",
                    "percent_taxable": "1.0000"
                }
            ],
            "usage": {
                "Long Distance Calls": [
                    {
                        "tax_name": "FEDERAL UNIVERSAL SERVICE FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "LOCAL COMMUNICATIONS SVC. TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FL COMMUNICATIONS SERVICES TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FEDERAL TRS FUND",
                        "percent_taxable": "1.0000"
                    }
                ],
                "International Calls": [
                    {
                        "tax_name": "FEDERAL UNIVERSAL SERVICE FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FL COMMUNICATIONS SERVICES TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FEDERAL TRS FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "LOCAL COMMUNICATIONS SVC. TAX",
                        "percent_taxable": "1.0000"
                    }
                ]
            }
        }
  }
}
```

This endpoint creates a Client on DNA. You will get back a <code>id</code> and a <code>ns_domain</code> these will be required for other operations. Besides that, you will also get a tax breakdown and usage in percent.

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/client?email=<value>&
first_name=<value>&last_name=<value>&zipcode=<value>&address=<value>&address2=<value>&sameBillingAddress=<values>&billing_zipcode=<value>&billing_address=<value>&billing_address2=<value>&has_subreseller_id=<value>&subreseller_id=<value>&start_billing_date=<value>&did_porting=<value>&did_number=<value>`

### Query Parameters

<aside class="warning">This request has no default parameters or values. Ignoring this will result in an error.</aside>

Parameter | Example | Description
--------- | ------- | -----------
start_billing_date | 05/29/2017 | Date in  MM/DD/YYYY Format for Billing purposes
has_subreseller_id | 1 | This is an id used to group your client's IDs under a subreseller account if you have resellers that handle your clients this is how we would identify them for consolidation purposes. Accepts 1 or 0.
subreseller_id | 1234 | Send this parameter only if you use a subreseller structure.
email | email@email.com | Email used for any information required for the client, for example to send received V-mail.
first_name | Steve | First name for the client.
last_name | Harris | Last name for the client.
zipcode | 33134 | The client's zipcode.
address | 126 Mendoza avenue | The client's address.
address2 | apartment 7A | The client's second line address.
sameBillingAddress | 1 | Accepts 1 or 0 and determines if the address parameter will be used for billing, when 0 <code>billing_address</code> and <code>billing_zipcode</code> are required.
billing_address | 2121 ponce de leon | The billing address.
billing_address2 | 2121 ponce de leon | The billing second line address.
billing_zipcode | 33308 | The billing zipcode.
did_porting | 0 | Acepts 1 or 0 depending on if the did_number you are providing is ported or no.
did_number | 3052304999 | Main phone number for the client.

<aside class="success">
Remember — store your <code>&lt;id&gt;</code> and <code>&lt;ns_domain&gt;</code> for future operations!
</aside>

## Activate a Client

```shell
curl "https://staging.api.nexogy.com/api/residential/client/<id>/activate"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/client/id/activate';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>

```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "timestamp": 1496930642
  }
}

```

This endpoint activates a specific client. If the client was previously cancelled, it activates the client on Netsapiens and sets the billing_status to active on DNA.

<aside class="warning">You will need the <code>&lt;id&gt;</code> for this operation</aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/client/<id>/activate`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the client to activate,the one we sent you when the client was created

## Suspend a Client

```shell
curl "https://staging.api.nexogy.com/api/residential/client/<id>/suspend"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/client/id/suspend';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "timestamp": 1496940922
  }
}
```

This endpoint suspends a Client. It just locked the client on Netsapiens. This is different from the cancel endpoint.

<aside class="warning">You will need the <code>&lt;id&gt;</code> for this operation</aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/client/<id>/suspend`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the client to suspend, the one we sent you when the client was created

## Cancel a Client

```shell
curl "https://staging.api.nexogy.com/api/residential/client/<id>/cancel"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/client/id/cancel';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "timestamp": 1496931834
  }
}
```

This endpoint cancels a Client. It performs two operations, first suspends the client domain on Netsapiens and then set the billing_status of the client to suspended.

<aside class="warning">You will need the <code>&lt;id&gt;</code> for this operation</aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/client/<id>/cancel`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the client to cancel, the one we sent you when the client was created

## Get Status

```shell
curl "https://staging.api.nexogy.com/api/residential/domain/<domain>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/domain/<domain>';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "status": "active",
    "timestamp": 1496259363
  }
}
```

This endpoint gets the status of a domain. Status are locked or active

<aside class="warning">You will need the <code>&lt;domain&gt;</code> for this operation</aside>

### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/domain/<domain>`

### URL Parameters

Parameter | Description
--------- | -----------
domain | The domain name of the client.

## Get Taxes

```shell
curl "https://staging.api.nexogy.com/api/residential/taxes/<client_id>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/taxes/<client_id>';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
    "result": "OK",
    "data": {
        "taxes": {
            "breakdown": [
                {
                    "tax_name": "FEDERAL TRS FUND",
                    "percent_taxable": "0.6490"
                },
                {
                    "tax_name": "LOCAL COMMUNICATIONS SVC. TAX",
                    "percent_taxable": "1.0000"
                }
            ],
            "usage": {
                "Long Distance Calls": [
                    {
                        "tax_name": "FEDERAL TRS FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FL COMMUNICATIONS SERVICES TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FEDERAL UNIVERSAL SERVICE FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "LOCAL COMMUNICATIONS SVC. TAX",
                        "percent_taxable": "1.0000"
                    }
                ],
                "International Calls": [
                    {
                        "tax_name": "FL COMMUNICATIONS SERVICES TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FEDERAL UNIVERSAL SERVICE FUND",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "LOCAL COMMUNICATIONS SVC. TAX",
                        "percent_taxable": "1.0000"
                    },
                    {
                        "tax_name": "FEDERAL TRS FUND",
                        "percent_taxable": "1.0000"
                    }
                ]
            }
        }
    }
}
```

This endpoint gets the tax information for a certain client.

<aside class="warning">You will need the <code>&lt;client_id&gt;</code> for this operation</aside>

### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/taxes/<client_id>`

### URL Parameters

Parameter | Description
--------- | -----------
client_id | The ID of the client.

## Update

```shell
curl "https://staging.api.nexogy.com/api/residential/client/<id>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/client/<id>';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Populate array with parameters
$data['start_billing_date'] = '06/08/2017';

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);
curl_setopt($c, CURLOPT_POSTFIELDS, http_build_query($data));

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "timestamp": 1496941963
  }
}
```

This endpoint updates the information of a client in DNA. For now it's only available for the start_billing_date field.

<aside class="warning">You will need the <code>&lt;id&gt;</code> for this operation</aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/client/<id>`

### URL Parameters

Parameter | Example | Description
--------- | ------- | -----------
start_billing_date | 06/08/2017 | Date in  MM/DD/YYYY Format for Billing purposes.

## Send LOA

```shell
curl "https://staging.api.nexogy.com/api/residential/loa"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/loa';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Populate array with parameters
$data['client_id'] = 1111;
$data['loa'] = '@' . realpath('loa.pdf');

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);
curl_setopt($c, CURLOPT_POSTFIELDS, http_build_query($data));

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "timestamp": 1496941963
  }
}
```

When porting a number, usually providers request a signed LOA to confirm ownership, identity and authorization from the end customer to execute the porting. This endpoint takes this document in pdf format, already signed and links it to the client.

<aside class="warning">You will need the <code>&lt;id&gt;</code> for this operation</aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/loa`

### URL Parameters

Parameter | Example | Description
--------- | ------- | -----------
client_id | 1111    | The ID of the client,the one we sent you when the client was created.
loa       |         | The pdf file containing a signed LOA. The file size must be smaller than 1.5 MB

## Get Porting Updates

```shell
curl "https://staging.api.nexogy.com/api/residential/task/porting/<client_id>/updates"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/task/porting/<client_id>/updates';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
    "data": {
        "number": "3056028300",
        "status": "Pending",
        "provider": "Peerless",
        "trunk_group": "Default",
        "destination": "NETSAPIENS",
        "timestamp": 1503514889
    }
}
```

This endpoint allows to get the status of the porting task. Possible status returned are "Pending", "Completed", or "Unable to Port".

<aside class="warning">You will need the <code>&lt;client_id&gt;</code> for this operation</aside>

### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/task/porting/<client_id>/updates`

### URL Parameters

Parameter | Example | Description
--------- | ------- | -----------
client_id | 1111    | The ID of the client,the one we sent you when the client was created.

## Get Shipping Updates

```shell
curl "https://staging.api.nexogy.com/api/residential/task/shipping/<client_id>/updates"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/task/shipping/<client_id>/updates';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
    "data": {
        "equipment": "Grandstream HandyTone HT801 (ATA)",
        "mac": "0015656B4586",
        "serial": "FOC1106X1A0",
        "shippings": [
          "0": [
            "method": "FedEx",
            "address": "666 Valhalla st.",
            "status": "Shipped",
            "trackings": [
              "0": "779816675513"
            ]

          ]
        ],
        "timestamp": 1503515720
    }
}
```

This endpoint allows to get the status of the equipment shipping task.

<aside class="warning">You will need the <code>&lt;client_id&gt;</code> for this operation</aside>

### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/task/shipping/<client_id>/updates`

### URL Parameters

Parameter | Example | Description
--------- | ------- | -----------
client_id | 1111    | The ID of the client,the one we sent you when the client was created.

## Projects

```shell
curl "https://staging.api.nexogy.com/api/residential/projects/<format>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/projects/web';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> If you use the value 'web' with parameter format, you just have to access the url through a web browser to see the list of projects. If you use the value 'json', the endpoint will return the list of projects in json format.

```json
{
    "result": "OK",
    "data": [
        {
            "company": "Company 1",
            "agent": "Agent",
            "quoted_by": "Carlos Mathison",
            "signed": "Fri, Aug 25, 2017 12:00 AM",
            "started": "Fri, Aug 25, 2017 3:35 PM",
            "pending_tasks": [
                "Phones PO & Shipping",
                "Forward when Offline",
                "Porting",
                "Project Completed"
            ]
        },
        {
            "company": "Company 2",
            "agent": "Agent",
            "quoted_by": "Carlos Mathison",
            "signed": "Tue, Aug 29, 2017 12:00 AM",
            "started": "Tue, Aug 29, 2017 3:10 PM",
            "pending_tasks": [
                "Phones PO & Shipping",
                "Project Completed"
            ]
        },
    ]
}
```

This endpoint either shows a web page with a list of all provisioning projects or returns the same list in json format. The list includes the name of the company, the agent of the project, the user who quoted the project, the date the project was signed and started, and a list of tasks with their corresponding status. You can search by company name or filter by agent in the web version. Clicking on the "Phones PO & Shipping" will show the details of the shipping task. The most important requirement is that the token has to be passed as a header (Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2 ) in the web browser.

Examples:

Web interface
`https://staging.api.nexogy.com/api/residential/projects/web` 

List in json format
`GET https://staging.api.nexogy.com/api/residential/projects/json`


### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/projects/<format>`

Parameter | Example | Description
--------- | ------- | -----------
format    | web     | This value is 'web' or 'json'. If you use 'web' the endpoint will show a list of projects in HTML format. If you use 'json', you will get the same list but in json format.

# Device

Once a Client is Created a default device is created, additional devices may be created later, with the device method.

## Device method

```shell
curl "https://staging.api.nexogy.com/api/residential/device?client_id=<value>&domain=<value>&ext=<value>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/device';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Populate array with parameters
$data['domain'] = '06/08/tomaraya.com';
$data['client_id'] = '12345';
$data['ext'] = '1003';

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);
curl_setopt($c, CURLOPT_POSTFIELDS, http_build_query($data));

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>

> The above command returns JSON structured like this:

```json
{
 "result": "OK",
 "data": {
   "subscriber_name": "1012",
   "aor": "sip:1012@kirkhammet.com",
   "domain": "kirkhammet.com",
   "authentication_key": "encrypted key",
   "regservers": {
     "server1": {
       "address": "sandbox.nexogy.net",
       "port": "5092"
     }
   },
   "timestamp": 1496682921
 }
}
```

The Device method behaves different according to the parameters it receives. You can pass the domain or the client_id, no need to pass both. If no ext is sent the default extension is created, in this case extension=1000 and the device information is returned. If a number is sent in this parameter and the device exists this method returns device information. If a number is sent and the device doesn't exist, that device for that extension is created.

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/device?client_id=<value>&domain=<value>&ext=<value>`

### URL Parameters

Parameter | Description
--------- | -----------
client_id | The client ID of the requested device. You get this information whe the client was created.
domain | The domain you received when the client was created.
extension | This parameter is optional. This is the extension of the customer's device. If no device is sent the default extension is created, in this case extension=1000 and the device information is returned. If a number is sent in this parameter and the device exists this method returns device information. If a number is sent and the device doesn't exist, that device for that extension is created.

### JSON Response

Parameter | Description
--------- | -----------
subscriber_name | The Devices extension number.
aor | The identifier of device and The domain.
authentication_key | The SIP password for the device. For security reasons we use gpg for encryption. You will recieve this parameter encrypted in Base 64 using gpg. With the Public Key you previously sent to us.
regservers | an array with the available registration servers and ports, this is required for your configuration.

Refer to this documentation in order to generate the key here:

<a href='https://help.github.com/articles/generating-a-new-gpg-key/'>Documentation for gpg</a>

<aside class="warning">Send us the public key indicated in step 13 of the <code>gpg</code> documentation found above. For this operation.</aside>

# Did

## Search Dids

```shell
curl "https://staging.api.nexogy.com/api/dids/search?npa=<value>&state=<value>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/dids/search?npa=305&state=FL';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
  "result": "OK",
  "data": {
    "return": {
      "npas": {
        "npa": "305"
      },
      "quantity": 6,
      "consecutive": 1,
      "result": {
        "tn": [
          {
            "number": 3052304666,
            "category": "Vanity"
          },
          {
            "number": 3052304777,
            "category": "Vanity"
          },
          {
            "number": 3052304999,
            "category": "Vanity"
          },
          {
            "number": 3054344555,
            "category": "Vanity"
          },
          {
            "number": 3054344600,
            "category": "Vanity"
          },
          {
            "number": 3054344777,
            "category": "Vanity"
          }
        ]
      },
      "tnCount": 6
    }
  }
```

This endpoit conducts a search by area code and state name and returns available did numbers to be used when creating a new client.

### HTTP Request

`POST https://staging.api.nexogy.com/api/dids/search?npa=<value>&state=<value>`

### URL Parameters

Parameter | Description
--------- | -----------
npa | Area code of the desired number.
state | State of the desired number.

## Provision 911 Did

```shell
curl "https://staging.api.nexogy.com/api/residential/e911?client_id=<value>&address1=<value>&address2=<value>&city=<value>&state=<value>&zip=<value>&force=<value>"
  -H "Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2"
  -H "Accept:application/json"
```

```php
<?
// Set api url
$apiUrl = 'https://staging.api.nexogy.com/api/residential/e911';
// Start cURL
$c = curl_init();
curl_setopt($c, CURLOPT_CONNECTTIMEOUT, 5);
curl_setopt($c, CURLOPT_RETURNTRANSFER, true);

// Populate array with parameters
$data['client_id'] = '6559';
$data['address1'] = '1111 Somestreet st';
$data['address2'] = '';
$data['city'] = 'City;
$data['state'] = 'ST';
$data['zip'] = '33000';
$data['force'] = '0';

// Set up headers
$request_headers = array();
$request_headers[] = 'Authorization: Bearer '. $access_token;
$request_headers[] = 'Accept: application/json';
curl_setopt($c, CURLOPT_HTTPHEADER, $request_headers);

// Setup the remainder of the cURL request
curl_setopt($c, CURLOPT_URL, $apiUrl);
curl_setopt($c, CURLOPT_POST, true);
curl_setopt($c, CURLOPT_POSTFIELDS, http_build_query($data));

// Execute the API call and return the response
$result = curl_exec($c);
curl_close($c);
?>
```

> The above command returns JSON structured like this:

```json
{
    "result": "OK",
    "data": {
        "timestamp": 1498572262
    }
}
```

This endpoint sets the 911 address for the number associated to the client. Behind the scenes it has two layers of address validation, the first one using UPS API and the second one uses Bandwidth API. For the request to be successful it has to go through both layers. In case the address is not valid but the validation services have other options, they will be presented to the user with the message "ambiguous address", so the user may select any of them. In case the validation services can't provide valid options, the user will get a message of "invalid address" and the action won't be completed.

If the user wants to use an invalid address anyway, the parameter "force=1" would need to be sent to be passed with value 1.

<aside class="warning">Our recommendation is to first validate the address using the provided services and it the address is still correct after validadion then force it. Do not force addresses unless there's no other option. </aside>

### HTTP Request

`POST https://staging.api.nexogy.com/api/residential/e911?client_id=<value>&address1=<value>&address2=<value>&city=<value>&state=<value>&zip=<value>&force=<value>`

### URL Parameters

Parameter | Description
--------- | -----------
client_id | The client ID. You get this information when the client was created. This parameter is required.
address1   | Street address. This parameter is required.
address2   | Second line of street address. This parameter is not required.
city      | City name. This parameter is required.
state     | State name. This parameter is required.
zip       | Zipcode. This parameter is required.
force     | Wether the address will be forced or not (1 or 0). This parameter is not required.

# Requests Dashboard

## Requests List

This endpoint shows a web page with the list of all requests made. To use it, you just have to send a get from any browser. The list includes the Ip, url requested, date of the request, request headers, parameters, the response sent by the api and the response code. You can search by token or filter by start and end date. Information can also be ordered by clicking the table headers. The most important requirement is that the token has to be passed as a header (Authorization:Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjY1N2 ) in the web browser.

Examples:

Web interface
`https://staging.api.nexogy.com/api/residential/dev-dashboard` 


### HTTP Request

`GET https://staging.api.nexogy.com/api/residential/dev-dashboard`


