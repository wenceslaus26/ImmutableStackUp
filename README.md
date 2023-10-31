Guide: Integrating Immutable Passport into Your Application

Immutable Passport simplifies user authentication for your application, allowing users to seamlessly log in using their Ethereum addresses. 
This guide will walk you through the steps to integrate Immutable Passport into your application.

Prerequisites:

-> Node.js installed on your development environment.
-> A basic understanding of JavaScript and React (for the example).
-> An Immutable Developer Hub account (https://developer.immutable.com/).

Step 1: Set Up Your Application

For this guide, we will create a simple React application, but you can integrate Immutable Passport into an existing application as well.

1) Create a new React application or use an existing one. You can create one using create-react-app in your terminal using the following command:
--> npx create-react-app immutable-passport-demo
2) Navigate into the app's directory using the command below:
-->cd immutable-passport-demo
3) Open your application's codebase in your preferred code editor.

Step 2: Register Your Application on Immutable Developer Hub

1) Visit the Immutable Developer Hub (https://developer.immutable.com/).
2) Log in with your Immutable account or create one if you haven't already.
3) Once logged in, navigate to the "Applications" section.
4) Click "Create New Application" and fill out the required information, including your application's name and redirect URL.
5) Save your changes. You will receive a Client ID and Client Secret, which you will use in your application.

Step 3: Install and Initialize the Passport Client

1) In your application's root directory, install the @immutable/passport package by running this command in your terminal:
-> npm install @immutable/passport
2) Initialize the Passport client in your application by adding the following code to your main JavaScript file (e.g., src/index.js):
-> import ImmutablePassport from '@immutable/passport';

   const passport = new ImmutablePassport({
     clientId: 'YOUR_CLIENT_ID', // Replace with your Client ID
     redirectUri: 'http://localhost:3000/auth/callback', // Your app's redirect URI
   });

Step 4: Log In a User with Passport

1) Create a "Login" button or link in your application's user interface.
2) Add an event listener to this button/link that initiates the Passport login process:
-> const loginButton = document.getElementById('login-button');
   loginButton.addEventListener('click', () => {
     passport.login();
   });

Step 5: Display User Information

1) After a successful login, you can access the ID token, access token, and the user's nickname from the Passport client.
-> const idToken = passport.getIdToken();
   const accessToken = passport.getAccessToken();
   const userNickname = passport.getUser().nickname;
2) You can then display this information in your application's UI or use it for further functionality.

Step 6: Log Out a User

1) Create a "Log Out" button in your UI.
-> const logoutButton = document.getElementById('logout-button');
   logoutButton.addEventListener('click', () => {
     passport.logout();
   });

Step 7: Initiate a Transaction from Passport

To initiate a transaction from Passport, you can use the Immutable Passport API. 
For example, you can send a placeholder string and obtain the transaction hash:
-> passport.initiateTransaction({
     to: '0xRecipientAddress',
     value: '0.01 ETH',
     data: '0xPlaceholderData',
   }).then((transactionHash) => {
     console.log(`Transaction Hash: ${transactionHash}`);
   }).catch((error) => {
     console.error(`Transaction Error: ${error}`);
   });

Step 8: Testing Your Application

1) Run your application:
-> npm start
2) Open your application in a web browser, and you should now have the Immutable Passport authentication integrated into your app.



