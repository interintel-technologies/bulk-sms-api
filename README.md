## A Guide on how to Consume the BULK SMS API using Oauth2.0 ##

### Table of Contents
[1.0 Get the Login Details.](#10-get-the-login-details)  
[2.0 Get an Access Token and a Refresh Token.](#20-get-an-access-token-and-a-refresh-token)  
[3.0 Formulate the Request.](#3.0-formulate-the-request)


You can click on the images to get full page view if some details are not clear.

#### 1.0 Get the Login Details #####


Get the Oauth2 login details from the Nenasasa portal under Developer->Settings section. 

<p align="center">
<img src="images/nenasasa_portal.png" width="700px" height="400px" alt="Nenasasa Portal" style="display:block;margin-left:auto;margin-right:auto;">

</p>
<div class="center"><i>The details are: client_id, username and Authorization_grant_type. You'll also need to use your existing password.</i></div>


#### 2.0 Get an Access Token and a Refresh Token ####
To get an access_token and a refresh_token, make a request to the Nenasasa endpoint (https://nenasasa.com/api/v1/o/token/) as illustrated below. They last for 3600 seconds (10 hours). 
<p align="center">
<img src="images/get_access_token.png"  width="700px" height="550px" alt="Get Access Token"  style="display:block; margin-left:auto; margin-right:auto;">
</p>

You can use the same endpoint to refresh the token and receive a new token whenever the access token expires.
<p align="center">
<img src="images/refresh_token.png" width="700px" height="550px" style="display:block; margin-left:auto; margin-right:auto;" alt="Refresh Token">
</p>

#### 3.0 Formulate the Request ####
You'll then need to add the access token to the Authorization header (Authorization: Bearer {access_token}) when making the SMS request.
<p align="center">
 <img src="images/configure_token.png" width="700px" height="550px" style="display:block; margin-left:auto; margin-right:auto;" alt="Add access token to Authorization Header">
</p>
 <div align="center"> <i>Add the access token to Authorization Header </i></div>
 <br></br>  
 
 And then formulate the request body as below. The endpoint changes to (https://nenasasa.com/api/v1/SEND%20SMS).
 <p align="center">
 <img src="images/send_bulk_sms.png" width="700px" height="500px" style="display:block; margin-left:auto; margin-right:auto;" alt="Send SMS using SEND SMS endpoint">
 <p>

