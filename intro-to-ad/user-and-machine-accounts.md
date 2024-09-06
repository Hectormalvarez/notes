# Introduction to Active Directory

## User and Machine Accounts

- when a user logs in the system verifies password and creates an access token.
- token is used to interact and authenticate with services
- user accounts can be unintentionaly misconfigured and represent a large attack surface

## Local Accounts

- stored locally on particular server or workstation
  - can be assigned rights on that host individually or via group membership
  - rights assigned only effective on their host not across domain
- default user accounts:

  1. Administrator
     - SID: S-1-5-domain-500
     - first account created on new windows install
     - cannot be deleted or locked
     - can be disabled or renamed
     - disabled by default - new account is created in local admins group
  2. Guest
     - disabled by default
     - used to allow unauthenticated access
     - recommended to leave disabled
  3. SYSTEM
     - or NT AUTHORITY\SYSTEM account on windows host
     - default account installed and used by windows os
     - unlike root is a service account; does not run in user context
     - no profile; will not appear in user manager; cannot be added to groups
     - highest level of permission one can achieve on a windows host  
       has full control permissions to all files
  4. Network Service
     - predefined account used by Service Control Manager for running Windows services
     - will present credentials to remote services
  5. Local Service
     - predefined account used by Service Control Manager for running Windows services
     - configured with minimul privileges on computer and presents anonymous credentials to network

## Domain Accounts

- granted rights from domain to access resources
- naming attributes:
  - UserPrincipalName (UPN) primary logon name fo user, uses email address format
  - ObjectGUID: unqiue identifier for object in AD, even after deletion
  - SAMAccountName: logon name that supports previous versions of windows clients & servers
  - ObjectSID: user's SID, identifies user and group membership
  - sIDHistory previous SIDs for user if moved between domains
    - after migration last SID will be added to sIDHistory and new SID will become its objectSID

### common attributes

- many attributes; some relevent more than others
- could potentially contain sensitive data used for attack

## Domain-joined vs non-Domain-joined machines

1. Domain-Joined
   - host is part of domain
   - will aquire needed configurations from domain group policies
   - user can login and access resources on any domain joined workstation
2. non-Domain-Joined
   - host is part of a workgroup
   - access controlled by hosting workstation
