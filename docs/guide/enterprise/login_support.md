# Login support

In private enterprise environments, Zepl supports multiple login systems that can be set up after deployment into your VPC. This is the list of all the integrations we support but feel free to contact us if you have any questions about an integration or need one not in the list.

## DB

Zepl's default login system. The user will be authenticated against our own database.

#### Registration

- user registers with email address in the Zepl login page
- user receives an email with an authentication link
- user clicks on the link and creates an account (setting username and password)

#### Login

 The user logs in with their username and password on the Zepl login page.

## [Oauth2](https://en.wikipedia.org/wiki/OAuth)

Zepl's alternate default login system (Google integration).

#### Registration / Login

- user clicks on login with Oauth in the Zepl login page
- user will be redirected to the Oauth2 provider
- user logs in on the Oauth2 provider page
- Zepl auth service will create the account/login if Oauth2 transaction succeeds

## [SAML](https://en.wikipedia.org/wiki/SAML_2.0)

Zepl provides integration with SAML 2.0 supporting these standards:
  - assertion and nameId encryption
  - assertion signatures
  - login (SP initiated)
    - IDP login: HTTP-redirect binding only
    - SP login: HTTP-POST binding only

#### Registration / Login

- user will be redirected to your SAML IDP
- user will login on the SML IDP
- Zepl auth service will create the account/login if the SAML transaction succeeds

## [CAS](https://en.wikipedia.org/wiki/Central_Authentication_Service)

Zepl provides an integration with CAS.

#### Registration / Login

- user will be redirected to your CAS login page
- user will login on the CAS provider
- Zepl auth service will create the account/login if the CAS transaction succeeds

## [LDAP](https://fr.wikipedia.org/wiki/Central_Authentication_Service)

Zepl provides an integration with LDAP 3.

#### Registration / Login

- user will input their ldap userID/password in Zepl's login page
- Zepl auth service will verify with ldap that the login information is correct
- Zepl auth service will create the account/login if the authentication succeeds

## [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token)

We are using JWT tokens for our authorization layer in our application and these tokens can be injected into some notebooks for authorization. If your enterprise needs to leverage JWT in order to have access to some of your data layers (that require your enterprise JWT), we can provide a custom login mechanism that can use your enterprise JWT to login into our system. Please contact us for more information.
