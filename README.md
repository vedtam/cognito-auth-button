## \<cognito-auth-button\>

`<cognito-auth-button>` Registers an auth with the application and creates a CognitoAuth object using the provided attributes: App client ID, App web domain, scope array, sign-in redirect URL and a sign-out redirect URL.

### Example usage:

AWS include the necessary libraries into your `index.html` file:

```html
<!-- AWS -->
<script src="js/aws-cognito-sdk.min.js"></script>
<script src="js/amazon-cognito-auth.min.js"></script>
<script src="js/amazon-cognito-identity.min.js"></script>
<script src="https://sdk.amazonaws.com/js/aws-sdk-2.130.0.min.js"></script>
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
