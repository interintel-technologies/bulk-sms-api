#### A Guide on How to Integrate with the BULK SMS API using Oauth2.0 ####

### 1.0 Get Oauth2 details from your portal under Developer->Settings section 

<img src="images/nenasasa_portal.png">Nenasasa Portal<img>

The details are: client_id, username and grant_type. You'll also need to use your existing password.

### 2.0 Make a request to the endpoint (https://nenasasa.com/api/v1/o/token/) to get an access_token and a refresh_token, which last for 3600 seconds (10 hours) 

<img src="images/get_access_token.png"> Get Access Token <img>

## 2.1 You can use the same endpoint to refresh the token, and receive a new token whenever the access token expires.

<img src="images/refresh_token.png">Refresh Token<img>

### 3.0 You'll then need add the access_token to the headers (Authorization: Bearer {access_token}) and send an SMS request as shown.
 <img src="configure_token.png"> Add access token to Authorization Header<img>
 
 <img src="send_sms.png"> Send SMS using SEND SMS endpoint <img>

