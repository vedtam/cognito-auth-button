## \<cognito-auth-button\>

`<cognito-auth-button>` for Polymer, registers an auth with the application and creates a CognitoAuth object using the provided attributes: App client ID, App web domain, scope array, sign-in redirect URL and a sign-out redirect URL.

### Example usage:

Include the necessary AWS libraries into your `index.html` file:

```html
<script src="https://github.com/aws/amazon-cognito-identity-js/blob/master/dist/aws-cognito-sdk.min.js"></script>
<script src="https://github.com/aws/amazon-cognito-identity-js/blob/master/dist/amazon-cognito-identity.min.js"></script>
<script src="https://github.com/aws/amazon-cognito-auth-js/blob/master/dist/amazon-cognito-auth.min.js"></script>
```

Install:

```html
bower i vedtam/cognito-auth-button --save
```

Create a new element and provide the necessary credentials:

```html
<cognito-auth-button
  region="[[region]]"
  client-id="[[ClientID]]"
  app-web-domain="[[AppWebDomain]]"
  token-scopes-array="profile,email,openid"
  redirect-uri-sign-in="[[RedirectUriSignIn]]"
  redirect-uri-sign-out="[[RedirectUriSignOut]]"
  identity-provider="Facebook"
  sign-in-label="Login"
  sign-out-label="Logout"
  class="login-btn"></cognito-auth-button>
```

### Setting up Cognito User Pools

In case if you got here after endless hours of figuring Cognito out (as it was in my case), and how to set up Facebook as an external identity provider for User Pools (NOT Federated Identities), before implementing `<cognito-auth-button>`, follow these steps:

### Step: Facebook App

1. Navigate to Facebook: https://developers.facebook.com/
2. Create new app in My Apps
3. Add Facebook Login in Products
4. Collect Facebook app id and secret (needed later)
5. Use specificed domain name in Valid OAuth redirect:
  `https://myapp.auth.eu1.central1.1.amazoncognito.com/` (the part "myapp" you can name yourself, but it needs to match with the name used in AWS Congnito)

### Step: AWS Cognito User Pools

1. Login to AWS and navigate to Cognito service
2. Create user pool in Cognito, say: `myapp_user_pool`
3. Collect Pool Id (needed later)
4. Create client in App clients (no secret needed)
5. Collect app id (needed later)
6. Define domain in App integration > Domain name, say: `myapp`
7. Enable Facebook and configure credentials in Federation > Identity providers
8. Back in App client Settings check "Facebook" and define callback for sign in/out urls. Example: https://localhost:3000/ or the domain on which you host your app (has to be https://)
9. Select Allowed OAuth Flows: Implicit grant
10. Select Allowed Oauth Scopes: email, openid, profile

### Step: AWS Cognito Federated Identities

11. Create new identity pool say: `myapp_identity_provider`
12. Create role for unauthenticated and authenticated (see policy examples)
13. Under Authentication Providers select Cognito and add User Pool ID and App client id (collected at step: 3. and 5.)
