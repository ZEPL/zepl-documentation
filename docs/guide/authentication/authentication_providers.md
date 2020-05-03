# Configure an authentication provider in Zepl
[Username / Password](#user-pass)

[Google](#google)

[OpenID Connect](#openid-connect)
  * [Okta](#openid-connect-okta)
  * [Azure AD](#openid-connect-azure-ad)
> The OpenID Connect protocol is supported by most SSO providers. If you don't see the name of your provider on this page, please check your provider's documentation.

[CAS](#cas)
</br>
</br>

# Username / Password <a name="user-pass"></a>
This is the default authentication method for Zepl and will be enabled upon sign up. This gives each user the ability to create a Zepl user name and password for authentication.

<img src="../../img/authentication/zepl_username_password.png" class="image-box img-100"/>

# Google <a name="google"></a>

>Note: This documentation is coming soon to a Zepl docs page near you!

# OpenID Connect <a name="openid-connect"></a>
Configure authentication through SSO provider with OpenID Connect. Please reference our configuration steps below for several of the top authentication providers. Throughout this configuration, keep track of the 3 key fileds required in Zepl: `OpenID URL`, `Client ID`, and `Client Secret`.

<img src="../../img/authentication/openid_connect/zepl_config_openid_connect.png" class="image-box img-100"/>

## Okta <a name="openid-connect-okta"></a>
> Note: The email address for a users's Zepl account, MUST match the `email` value in that same user's Okta account.

#### In Okta Admin Portal:
1. Create an Application: Select the Applications menu > Add Application > Create Application
2. Check the OpenID Connect radio button and select create
3. Enter this value for the login redirect URL: `https://www.zepl.com/api/v2/authenticator.identity.zepl/callback/openidprovider`
4. Navigate to the general settings for the new application that you created
5. Select `Authorization Code` for Authorized grant types. The final application configuration should look as follows:

  > Note: The "Initiate login URI" can be blank.

  
<img src="../../img/authentication/openid_connect/okta/okta_application_settings.png" class="image-box img-100"/>


5. Scroll to the bottom to find the `Client ID` and `Client secret`. Please copy these or keep for reference in the next section

<img src="../../img/authentication/openid_connect/okta/okta_client_credentials.png" class="image-box img-100"/>

#### In Zepl's Authentication Settings:
1. Select Settings > Authentication > OpenID
2. OpenID URL: `https://{Your Okta Account Name}.okta.com`

  >Note: This should NOT contain '-admin' or a trailing slash character (/) at the end of the url. Be sure to include, `https://`.

3. Client ID: Copy from the okta application you created in the previous section. Example: `4o199js5phG2Cv3204p6`
4. Client Secret: Copy from the okta application you created in the previous section. Example: `0S-djdCveAac3aGz0CtNBOOwndoHL3I1MWbVv7el`
5. Select Save & Activate
6. Now, logout, log back in, and you should be redirected to Okta

<img src="../../img/authentication/openid_connect/okta/okta_zepl_config_openid_connect.png" class="image-box img-100"/>

## Azure AD <a name="openid-connect-azure-ad"></a>
#### In Azure Admin Portal (https://portal.azure.com/):
Creating an Application in Azure AD
1. Select Azure Active Directory > App Registrations > New Registration
2. Enter this value for the redirect URL: `https://www.zepl.com/api/v2/authenticator.identity.zepl/callback/openidprovider`

<img src="../../img/authentication/openid_connect/azure_ad/azure_ad_app_register.png" class="image-box img-100"/>

3. Register > Select your new app
4. Copy Application (client) ID below
5. Copy Directory (tenant) ID below

<img src="../../img/authentication/openid_connect/azure_ad/azure_ad_key.png" class="image-box img-100"/>

Creating a Client Secret:
1. Select Azure Active Directory > App Registrations > Select the app you just created
2. Select Certificates & secrets > + New client secret
3. Copy the secret value below

> Note: Once you navigate away from this page you can no longer copy this value.

<img src="../../img/authentication/openid_connect/azure_ad/azure_ad_secret.png" class="image-box img-100"/>

#### In Zepl's Authentication Settings:
1. Select Settings > Authentication > OpenID
2. OpenID URL: `https://login.microsoftonline.com/{Your Directory (tenant) ID}/v2.0`. Replace "{Your Okta Account Name}" with the Directory (tenant) ID  from above.

  > Note: This should NOT contain a slash character (/) at the end of the url. Be sure to include, `https://`
  
3. Client ID: Copy the Application (client) ID from the previous section. Example: `d610128e-9dda-4575-9d2s-b5e75a1e457w`
4. Client Secret: Copy the client secret from the previous section. Example: `VUq1jKjSsI9HaI1MtaSD3@oZFYfU/I_`
5. Select Save & Activate
6. Now, logout, log back in, and you should be redirected to the Azure authentication page

<img src="../../img/authentication/openid_connect/azure_ad/azure_zepl_config_openid_connect.png" class="image-box img-100"/>

# CAS <a name="cas"></a>

> Note: This documentation is coming soon to a Zepl docs page near you!