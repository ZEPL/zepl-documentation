# Login support

In private enterprise environments, ZEPL support multiple login systems. This is the list of all the integrations we support, but be free to contact us if you need or have any questions about an integration. Those integrations will be handled after the deployment of ZEPL in your private cloud.

## DB
ZEPL default login system. The user will be authenticated against our own database.
#### Register flow
- user registers with email address in ZEPL login page.
- user receives an email with an authentication link
- user clicks on the link and creates an account (set username and password)
#### Login flow
- user logs in with username and password in ZEPL login page.
## [Oauth2](https://en.wikipedia.org/wiki/OAuth)
ZEPL default login system (google integration).
#### Register / Login flow
- user clicks on login with oauth in ZEPL login page.
- user will be redirected to oauth2 provider.
- user logs in on the oauth2 provider page.
- ZEPL auth service will create account / login if oauth2 provider succeeds.
## [SAML](https://en.wikipedia.org/wiki/SAML_2.0)
ZEPL provides an integration with SAML 2.0.
We support these standard:
  - Assertion and nameId encryption.
  - Assertion signatures.
  - Login (SP initiated).
    - IDP login: HTTP-Redirect binding only
    - SP login: HTTP-POST binding only
#### Register / Login flow
- user will be redirected to your SAML IDP
- user will login on the saml IDP
- ZEPL auth service will create account / login if the SAML transaction succeeds
## [CAS](https://en.wikipedia.org/wiki/Central_Authentication_Service)
ZEPL provides an integration with CAS.
#### Register / Login flow
- user will be redirected to your CAS login page
- user will login on the CAS provider
- ZEPL auth service will create account / login if the CAS transaction succeeds
## [LDAP](https://fr.wikipedia.org/wiki/Central_Authentication_Service)
ZEPL provides an integration with LDAP 3.
#### Register / Login flow
- user will input ldap userID / ldap password in ZEPL login page
- ZEPL auth service will verify against ldap that the login information is correct
- ZEPL auth service will create account / login if the authentification is working
## [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token)
We are using JWT tokens for our authorization layer in our application. And these tokens can be injected in some notebook execution. If your enterprise needs to leverage JWT in order to have access to some of your data layer (that requires your enterprise JWT), we can provide a custom login way that can use your enterprise JWT to login into our system. Contact us for more information.
