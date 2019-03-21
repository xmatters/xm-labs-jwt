# Generating JSON Web Tokens (JWT)
[JWT](https://jwt.io) is a leading authentication mechanism for APIs due to its secure nature and easy transportability. This is a library for generating these tokens and authenticating with any APIs that require them. 

<kbd>
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
</kbd>

# Pre-Requisites
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!

# Files
* [JWT.js](JWT.js) - A shared library containing the `sign` function for generating the token. 

# How it works
This is just a shared library, so it will need to be added to your integration builder shared libraries. Once there, the `JWT.sign` function can be used to generate a token based on a payload. This token can then be used for authenticating into the third party application. 


# Installation

## xMatters set up
1. Login to xMatters and open up the Integration Builder on the appropriate Comm Plan. 
2. Expand the Shared Libraries section and click Add button. 
3. Replace the entire contents of this script with the script in [JWT.js](JWT.js). 
4. Change the name of the library by clicking on the **My Shared Library** at the top of the screen and replace it with **JWT**. 
5. In the script that needs a token, add the following lines:

   ```javascript
   // Set the secret value for the encryption algorithm. 
   var SECRET = "thesecret-1234";
   
   // Include the JWT library code.
   var JWT = require( 'JWT' );
   
   // This is the payload to be encoded.
   var payload = {
       "iss": "API_KEY_HERE",
       "exp": 1516239022
   }
   
   // Call the sign function and pass the payload and secret values. 
   var jwt = JWT.sign( payload, SECRET );
   
   ```




# Testing
The value returned from the `JWT.sign` function will be the entire token. You can paste this entire thing into the **Encoded** section on the [jwt.io](https://jwt.io) page. Enter the secret used to encrypt the token in the signature part and the header and payload entries will be displayed. If they are not displayed, something went wrong. Check the secret value passsed into the `JWT.sign` function and verify it is correctly entered in the jwt.io page. 

If that still doesn't work, post an issue and we can check it out. 
