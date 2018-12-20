# Login support

In enterprise environments, ZEPL support multiple login systems. This is the list of all the integrations we support, but be free to contact us if you need or have any questions about an integration. Those integration will be handle after the deployment of ZEPL in your private cloud.

## DB
ZEPL default login system. The user will be authenticated against our own Database.
#### Register flow
- user register with email adress in ZEPL login page.
- user receive an email with a link
- user click on the link and create an account (set username and password)
#### Login flow
- user login with username and password in ZEPL login page.
## [Oauth2](https://fr.wikipedia.org/wiki/OAuth)
ZEPL default login system (google integration).
#### Register / Login flow
- user click on login with oauth in ZEPL login page.
- user will be redirect to oauth2 provider.
- user login on the oauth2 provider page.
- ZEPL auth service will create account / login if oauth2 provider succeed.
## [SAML](https://en.wikipedia.org/wiki/SAML_2.0)
ZEPL provide an integration with SAML 2.0.
We support those standard:

  - Assertion and nameId encryption.
  - Assertion signatures.
  - Login (SP initiated).
    - IDP login: HTTP-Redirect binding only
    - SP login: HTTP-POST binding only
#### Register / Login flow
- user will be redirect to your SAML IDP
- user will login on the saml IDP
- ZEPL auth service will create account / login if the SAML transaction succeed
## [CAS](https://fr.wikipedia.org/wiki/Central_Authentication_Service)
ZEPL provide an integration with CAS.
#### Register / Login flow
- user will be redirect to your CAS login page
- user will login on the CAS provider
- ZEPL auth service will create account / login if the CAS transaction succeed
## [LDAP](https://fr.wikipedia.org/wiki/Central_Authentication_Service)
ZEPL provide an integration with LDAP 3.
#### Register / Login flow
- user will write is ldap userID / ldap password in ZEPL login page
- ZEPL auth serrvice will verify against ldap that the login information is correct
- ZEPL auth service will create account / login if the authentification is working
## [JWT](https://fr.wikipedia.org/wiki/JSON_Web_Token)
We are using JWT token for our authorization layer in all our application. And those token can be injected in some notebook execution. If your enterprise need to leverage JWT in order to access to some of your data layer (that require your enterprise JWT), we can provide a custom login way that can use your enterprise JWT to login in our system. Contact us for more information.
