**API Specification Bulk SMS API OAUTH 2.0 v1**

| API Name | Bulk SMS API using OAUTH 2.0 |
| --- | --- |
| Description | Bulk SMS API using OAUTH 2.0 |
| Version | v1 |
| Owner | Implementation Team |
| Contact | Implementation Team |
| Links | TBC |
| Supported Formats | JSON |

**Base URL**

Production: [https://nenasasa.com/api/v1/](https://nenasasa.com/api/v1/token/)

**Authentication**

OAUTH 2.0 has been implemented for this API hence the developer needs to get the OAUTH 2.0 login details (client\_id, username and authorization\_grant\_type) from the Nenasasa portal under Developer-\>Settings section. You will also need to use your existing password

**Rate Limiting**

N/A

**Endpoints**

1. **Get Access Token and Refresh token**

Description: This request returns the access\_token and refresh\_token. Which lasts for 36000s (10 hours)

HTTP Method: POST

URL: /token

**Example Request Headers**

| **ID** | **Name** | **Value** |
| --- | --- | --- |
| 1 | Content-Type | application/json |
|
 |
 |
 |
|
 |
 |
 |

**Request Parameters**

| **ID** | **Name** | **Type** | **Description** | **Required** |
| --- | --- | --- | --- | --- |
| 1 | client\_id | String | OAUTH 2.0 details obtained from Developer-\>Settings section | Yes |
| 2 | username | String | Your username | Yes |
| 3 | password | String | Existing password | Yes |
| 4 | grant\_type | String | OAUTH 2.0 details Obtained from Developer-\>Settings section | Yes |

Sample Request Body:

{

"client\_id" : "harhfurhaeufhrehfuherf===",

"username" : "company1",

"password" : "sdfsdnfjksdf",

"grant\_type" : "password"

}

**Response Headers**

| ID | Name | Value |
| --- | --- | --- |
| 1 | Content-Type | application/json |

**Response Parameters**

| **ID** | **Name** | **Type** | **Description** |
| --- | --- | --- | --- |
| 1 | access\_token | String | access token to be used to as Bearer token |
| 2 | expires\_in | number | validity period in seconds |
| 3 | token\_type | String | Authentication method that uses access\_token in our case the value for this will be Bearer |
| 4 | scope | String | scope of the token |
| 5 | refresh\_token | String | Used to generate an access\_token |

**Sample Response Body**

{

"access\_token" : "access token value",

"expires\_in" : 36000,

"token\_type" : "Bearer",

"scope" : "read write groups",

"refresh\_token": "refresh token value"

}

**Error Responses**

TBC

1. **Get Refresh token**

Description: This request returns the refresh\_token, which lasts for 36000s (10 hours) whenever the access token expires

HTTP Method: POST

URL: /token

**Example Request Headers**

| **ID** | **Name** | **Value** |
| --- | --- | --- |
| 1 | Content-Type | application/json |
|
 |
 |
 |
|
 |
 |
 |

**Request Parameters**

| **ID** | **Name** | **Type** | **Description** | **Required** |
| --- | --- | --- | --- | --- |
| 1 | client\_id | String | OAUTH 2.0 details obtained from Developer-\>Settings section | Yes |
| 2 | username | String | Your username | Yes |
| 3 | password | String | Existing password | Yes |
| 4 | grant\_type | String | refresh\_token | Yes |

Sample Request Body:

{

"client\_id" : "harhfurhaeufhrehfuherf===",

"username" : "company1",

"password" : "sdfsdnfjksdf",

"grant\_type" : "refresh\_token"

}

**Response Headers**

| **ID** | **Name** | **Value** |
| --- | --- | --- |
| 1 | Content-Type | application/json |

**Response Parameters**

| **ID** | **Name** | **Type** | **Description** |
| --- | --- | --- | --- |
| 1 | access\_token | String | access token to be used to as Bearer token |
| 2 | expires\_in | number | validity period in seconds |
| 3 | token\_type | String | Authentication method that uses access\_token in our case the value for this will be Bearer |
| 4 | scope | String | scope of the token |
| 5 | refresh\_token | String | Used to generate an access\_token |

**Sample Response Body**

{

"access\_token" : "access token value",

"expires\_in" : 36000,

"token\_type" : "Bearer",

"scope" : "read write groups",

"refresh\_token": "refresh token value"

}

**Error Responses**

TBC

1. **Send SMS**

Description: This request will send a notification to the destination MSISDN

HTTP Method: POST

URL: /SEND SMS

**Example Request Headers**

| **ID** | **Name** | **Value** |
| --- | --- | --- |
| 1 | Content-Type | application/json |
| 2 | Authorization | Bearer \<access\_token\> |
|
 |
 |
 |

**Request Parameters**

| **ID** | **Name** | **Type** | **Description** | **Required** |
| --- | --- | --- | --- | --- |
| 1 | chid | String | Defines the channel unique ID | Yes |
| 2 | message | String | Message to be sent to the the destination MSISDN | Yes |
| 3 | alias | String | Sender ID | Yes |
| 4 | msisdn | String | Destination number that will receive the message | Yes |

**Sample Request Body**

{

"chid" : "13",

"message" : "This is a test SMS",

"alias" : "INTERINTEL",

"msisdn" : "0702695199"

}

**Response Headers**

| **ID** | **Name** | **Value** |
| --- | --- | --- |
| 1 | Content-Type | application/json |

**Response Parameters**

| **ID** | **Name** | **Type** | **Description** |
| --- | --- | --- | --- |
| 1 | response | Object | Institution details refer to **annex response object** |
| 2 | action\_id | number | unique ID for this action |
| 3 | response\_status | String | Response status code |
| 4 | overall\_status | String | Overall status code |
| 5 | last\_response | String | Describes whether the SMS was sent or not |

**{response object}**

| **ID** | **Name** | **Type** | **Description** |
| --- | --- | --- | --- |
| 1 | validate\_institution | String | Institution captured |
| 2 | get\_gateway\_profile | String | Gateway profile |
| 3 | get\_sms\_notification | String | Notification captured |
| 4 | debit\_float | String | Float balance |
| 5 | send\_notiification | String | Notification sent |

**Sample Response Body**

{

"response": {

"validate\_institution": "Institution captured",

"get\_gateway\_profile": "Got Gateway Profile",

"get\_sms\_notification": "Notification Captured: 134",

"debit\_float": "Float Debited with: 1.00 balance: 80000.00",

"send\_notiification": "Notification Sent. Please check SMS"

},

"action\_id": 1646,

"response\_status": "00",

"overall\_status": "00",

"last\_response": "Notification Sent. Please check SMS"

}

**Error Responses**

TBC

**Changelog**

N/A

**Version 1.0 (7th Dec 2022)**

Added: Send SMS using OAUTH 2.0

Deprecated: N/A

**Conventions**

N/A

**Dependencies**

1. Institution has to be created on the backend
2. Float top up to account

**Known Issues**

N/A

