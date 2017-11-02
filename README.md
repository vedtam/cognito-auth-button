## \<cognito-auth-button\>

`<cognito-auth-button>` Registers an auth with the application and creates a CognitoAuth object using the provided attributes: App client ID, App web domain, scope array, sign-in redirect URL and a sign-out redirect URL.

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
