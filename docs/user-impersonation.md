User Impersonation
==================

Sometimes it becomes necessary to impersonate users.  There are two common scenarios where user impersonation becomes useful:  Seeing an issue that a specific user is seeing with an application and users who find new ways to forget their sign in password.  Both scenarios are equally frustrating for the user and system administrators.  System administrators will generally have site admin privileges and not be able to see what ordinary user accounts see unless they have a separate account for that purpose.  User impersonation becomes a tool for making life simpler.  However, user impersonation support is a security risk.

The SSO server/client, by default, does not enable user impersonation for the aforementioned security reasons.  Enabling user impersonation requires enabling it for each user account that needs it, the application's API key, and the application itself.  The first step is to enable the API key and the application for passing 'sso_impersonate' with an account impersonation token.  Once that is done, the API key will accept impersonation tokens from that point on (unless it is disabled again later).  The next step is to locate a user account and enable impersonation by selecting 'Yes' from the appropriate drop down and clicking 'Save'.  The server will generate a token and a new drop down for automation appears that is optional.  Take the impersonation token and construct a URL by using the token with 'sso_impersonate'.  If you are signed in, you'll likely need to sign out first.  An impersonation URL will look like:

https://yourdomain.com/?sso_impersonate=[impersonation_token]

User impersonation URLs can be bookmarked in a browser for a one-click sign in.  This can be useful for users who frequently forget their password.  Such users are likely a security risk anyway by being part of the group of people who select weak passwords, so the one-click sign in token (64 completely random letters and numbers) is theoretically more secure as long as it is only transmitted over HTTPS.