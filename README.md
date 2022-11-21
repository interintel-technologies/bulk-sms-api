## A Guide on How to Integrate with the BULK SMS API using Oauth2.0 ##

#### 1.0 Get Oauth2 details from your portal under Developer->Settings section 

<img src="images/nenasasa_portal.png" alt="Nenasasa Portal" style="width:600;height:600;display:block; margin-left:auto; margin-right:auto;">

<i>The details are: client_id, username and grant_type. You'll also need to use your existing password.</i>

#### 2.0 Make a request to the endpoint (https://nenasasa.com/api/v1/o/token/) to get an access_token and a refresh_token. They last for 3600 seconds (10 hours). 

<img src="images/get_access_token.png" alt="Get Access Token"  style="width:500;height:800;display:block; margin-left:auto; margin-right:auto;">

##### You can use the same endpoint to refresh the token, and receive a new token whenever the access token expires.

<img src="images/refresh_token.png" style="width:500;height:800;display:block; margin-left:auto; margin-right:auto;" alt="Refresh Token">

#### 3.0 You'll then need to add the access_token to the headers (Authorization: Bearer {access_token}) and then sent the SMS request.
 <img src="images/configure_token.png" style="width:500;height:800;display:block; margin-left:auto; margin-right:auto;" alt="Add access token to Authorization Header">
 
 <i>Add the access token to Authorization Header </i>
 
 ##### You can formulate the SMS request as below.
 
 <img src="images/send_bulk_sms.png" style="width:500;height:800;display:block; margin-left:auto; margin-right:auto;" alt="Send SMS using SEND SMS endpoint">

