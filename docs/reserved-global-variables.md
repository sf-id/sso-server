Reserved Variables
==================

To minimize naming conflicts, the SSO server and client have very specific naming conventions so as to not interfere with the proper operation of applications, each other, and the various providers.  There is a lot to the core system, so avoiding conflicts is important.

There are two reserved prefixes:  '$sso_' and '$bb_'.

When creating global variable names for providers, a '$g_' prefix is recommended for throwaway variables.  For a permanent global, a '$g_providername_' prefix is recommended.  In general, correctly written providers will not need to use global variables.

Both the SSO server and client have a set of define()'d constants.  These are carefully constructed so they won't conflict with each other as well as third-party applications such that there is seamless integration.  The constants are defined in 'config.php', which is generated by each installer.

SSO Server Globals
------------------

* $sso_db - The database class instance for running queries.
* $sso_db_apikeys - A string containing the table name for running API key queries.
* $sso_db_fields - A string containing the table name for running field information queries.
* $sso_db_users - A string containing the table name for running user information queries.
* $sso_db_user_tags - A string containing the table name for running user tag information queries.
* $sso_db_user_sessions - A string containing the table name for running user session information queries.
* $sso_db_temp_sessions - A string containing the table name for running temporary session information queries.
* $sso_db_tags - A string containing the table name for running tag information queries.
* $sso_db_ipcache - A string containing the table name for running IP address cache information queries.
* $sso_fields - An array containing key-value pairs for identifying enabled fields (key) and whether or not the field is encrypted (value).
* $sso_select_fields - An array containing key-value pairs for displaying select dropdowns used throughout the admin interface.
* $sso_settings - An array containing the global configuration, including provider configurations.
* $sso_randomwords - An array containing internal information about the dictionary for exclusive use by the SSO_GetRandomWord() function.
* $sso_namespaces - An array containing possibly validated sessions in the various namespaces that have been signed into.
* $sso_rng - An instance of the CSPRNG class.
* $sso_ipaddr - An array containing normalized information about the remote IP address for use with IP address related operations.
* $bb_usertoken - A string containing a valid user token. Required to be set by 'admin_hook.php' for access to the admin interface.
* $sso_site_admin - A boolean indicating whether or not the user has access to the full admin interface or just a subset.
* $sso_user_id - An optional integer that defines a SSO server user ID of the user in the admin interface for identifying who did what.  Generally only useful for larger organizations where multiple users have the SSO site admin privilege and the SSO client is used to sign in to the admin interface.
* $sso_menuopts - An array containing menu options for passing to Admin Pack to generate the navigation for the admin interface.
* $sso_providers - An array of key-value pairs that map an internal provider name to an instance of the provider.
* $sso_provider - A string containing an internal provider name.
* $sso_header - A string containing the header for the end user interface.  Obtained by capturing the output of 'header.php'.
* $sso_footer - A string containing the footer for the end user interface.  Obtained by capturing the output of 'footer.php'.
* $sso_apirow - An object containing raw database API key information.
* $sso_apikey_info - An array containing extracted API key information.
* $sso_session_id - An array containing two elements - a string and an integer - for identifying a session.
* $sso_sessionrow - An object containing raw database session information.
* $sso_session_info - An array containing extracted session information.
* $sso_session_id2 - An array containing two elements - a string and an integer - for identifying a second session.
* $sso_sessionrow2 - An object containing raw database second session information.
* $sso_session_info2 - An array containing extracted second session information.
* $sso_protectedfields - An array containing provider protected SSO field mapping information.
* $sso_automate - A boolean that specifies if the validation step should be bypassed if possible.
* $sso_userrow - An object containing raw database user information.
* $sso_user_info - An array containing decrypted user information.
* $sso_missingfields - An array containing calculated missing fields for use by an 'index_hook.php' script.
* $sso_target_url - A string containing a base URL for conveniently generating URLs that have a similar target.
* $sso_selectors_url - A string containing a URL to use to return to the selection screen when multiple providers are available.
* $sso_skipsleep - A boolean in the endpoint that indicates whether or not to skip the timing attack defense logic.  Only usable by custom API keys.

The list of globals above are not exhaustive.

PHP SSO Client Globals
----------------------

* $sso_removekeys - An array containing names of $_GET options that should be removed if they appear for the signed in user.  This array should be defined by the application before including the 'client/functions.php' file.  The SSO client will automatically redirect the browser to a URL without the specified options.
* $sso__client - An instance of the 'SSO_Client' class that gets created when the 'client/functions.php' file is included.