Requirements:
1) Powershell 2.0 with the Microsoft Active Directory modules installed
2) Must be run as an account with permission to perform WMI Queries and querie Active Directory for computer accounts
3) WMI must be enabled and accessible remotely for the servers that will be queried.

Setup:
1) Edit the $domain variable to include part of your AD domain name.  Keep in mind that some usernames will be listed in the old format (domain\user) and others by the UPS (username@domain.local).  So be sure you set this variable using wildcards to encompass both domain formats, or run twice.
2) Edit the $serviceFile and $exceptionFile paths to locations that are available and that the user running the script has read/write/create/delete permissions.

The Services.csv file will list all the services located that are running as users that match the $domain variable.

The Exceptions.csv file will list any servers that the script was unable to query.  Common reasons for this included:
1) The server computer account is still listed in AD but has been decommissioned
2) The server is not responding to WMI requests because of permissions, firewall or the service not running/working.