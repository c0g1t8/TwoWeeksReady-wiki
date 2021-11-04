Users will need to register and log into the system.

The authentication will be through the [__Auth0__](https://auth0.com/) service. This service allows for application specific account registration as well as social login functionality.

## Login/Signup screen

A tabbed interface with a login tab and a sign up tab.

### Account Login

This will be a basic username and password form. A forgot password link will be made available.

### Account signup -> registration

Minimum Fields required for registration: full name, email address, password, zip code, opt-in status to mailing list. Full name, zip code, opt-in status should be part of a user profile.

## User profile / account settings

User can change their password, zip code, and mailing list preferences.

## Outstanding questions

1. Managing Mailing List
    - Is there an api to register/unregister users?
    - Is there a way to be notified through a callback should a user unregister via the email rather than through the application?
