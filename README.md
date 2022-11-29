## A Guide on How to Integrate with the BULK SMS API using Oauth2.0 ##

### Table of Contents
1.0 Get Login Details.  
2.0 Get an Access Token and a Refresh Token.  
3.0 Formulate the Request.

#### <b> 1.0 Get Login Details </b>

Get the Oauth2 login details from the Nenasasa portal under Developer->Settings section 

<img src="images/nenasasa_portal.png" width="800px" height="400px" alt="Nenasasa Portal" style="display:block;margin-left:auto;margin-right:auto;">

<i>The details are: client_id, username and grant_type. You'll also need to use your existing password.</i>

#### <b> 2.0 Get an Access Token and a Refresh Token </b>
To get an access_token and a refresh_token, make a request to the Nenasasa endpoint (https://nenasasa.com/api/v1/o/token/). They last for 3600 seconds (10 hours). 

<img src="images/get_access_token.png"  width="600px" height="400px" alt="Get Access Token"  style="display:block; margin-left:auto; margin-right:auto;">

You can use the same endpoint to refresh the token, and receive a new token whenever the access token expires.

<img src="images/refresh_token.png" width="500px" height="800px" style="display:block; margin-left:auto; margin-right:auto;" alt="Refresh Token">

#### <b> 3.0 Formulate the Request </b>
You'll then need to add the access_token to the Authorization header (Authorization: Bearer {access_token}) to sent the SMS request.
 <img src="images/configure_token.png" width="500px" height="800px" style="display:block; margin-left:auto; margin-right:auto;" alt="Add access token to Authorization Header">
 
 <i>Add the access token to Authorization Header </i>
 
 You can formulate the SMS request as below.
 
 <img src="images/send_bulk_sms.png" width="500px" height="800px" style="display:block; margin-left:auto; margin-right:auto;" alt="Send SMS using SEND SMS endpoint">

