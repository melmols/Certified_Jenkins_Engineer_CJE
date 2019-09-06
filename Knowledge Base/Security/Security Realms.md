# Security Realms & Authentication


## *Review*

*Setting Security Realms tells Jenkins what system to use for authentication
Security Realm is a dedicated database for user and passwords
||5 kinds of Realms supported out of the box, covered below:
Jenkins User Database
Unix user/group Database
Servlet Container
External LDAP
SSO||
New Realms types can be added by other plugins
E.g. Active Director
Users who are not authenticated are always bound to the "anonymous" special user*

## Jenkins user DB Realm

- This realm uses Jenkins local database
    * GUI listing on http://<JENKINS_URL>/asynchPeople/
    * DB is stored in XML files located in ${JENKINS_HOME}/users
- Signing-up enabled by * default:
    * New users can create an account with GUI
    * If *disabled*, admin needs to create user accounts
- Not very "scalable" realm, but very efficient for tiny instances

## Unis User/Group DB Realm

- This realm *Delegates* authentication to the underlying _Unix/Linux_ machine
  * Only users or groups known by the underlying operating system
  * Does not work on Windows
  * PAM compliant: [ https://wiki.jenkins.io/display/JENKINS/PAM+Authentication+Plugin ]
  
- Useful if you have Unix machines that are already configured for authentication

## Servlet Container Realm

-  This realm *delegates* authentication to the servlet engine running Jenkins
  * Jetty, Tomcat. JBoss, WebSphere... already have authentication mechanisms
-  Important: some URL's must not require authentication
  * CLI endpoint: /cli
  * SCMs enpoint (hooks): /git, /subversion...
  * Jars download endpoints: /jnlpJars
  * Current User Page: /whoAmI
  
## LDAP Realm

- This realm *delegates* authentication to an external LDAP service
  * Most companies already have a _Directory Service_ for authentication (maybe more)
- Highly tunable:
  * LDAP  binding can be sub-authenticated
  * Caching mechanism to leverage load on LDAP servers
  * Support for LDAP replicas
  
## Authorization setting

Defines the access rights for users and groups

[] Anyone can do anything
[] Legacy mode *Namely, if a user has the "admin" role, they will be granted full control over the system, 
and otherwise (including anonymous users) will only have the read access*
[] Logged users can do anything
    * [] Allow anonymous read access
[] Matrix-based security
[] Project-based Matrix Authorization strategy
[] Role-based matrix authorization strategy

## Lightweight Authorization

Lightweight authorization relies only on authentication, or a trusted environment
  - *Anyone can do anything*
    * _No_ authorization performed
    * Obvious behaviour; _Not recommended_ outside trusted environment
  - *Legacy mode*
    * Admins have full control, others have read access
  - *Logged in users can do anything*
    * Same as anyone can do anything, except you are forced to log in
    * Useful in trusted environment where you want to have audit trails 
## Matrix based authorization

  - Maps users/groups to Jenkins actions
  - Uses a two dimentional matrix
    * Horizontally: Rights, by categories (like: 'Jobs: Create')
    * Vertically: User and groups known by jenkins (Source: Security Realms)
    
## Credentials and Secrets

- Used to allow Pipelines and plugins to access protected resources
    without having to share passwords with all users who run the Pipeline
- Defined by the administrator
- Stored in encrypted files on the Jenkins Master
    Not stored in the SCM where its contents could be breached
    Credentials are encrypted using a key derived from the master key
    This is stored as a _secret_ so it cannot be deserialized to disk as plain text
- Accessed in the Pipeline using the _environment_ directive

### Credential management

Screens are available to manage credentials
  *Go to _Manage Jenkins > Configure Credentials_ to configure credentials
  *Go to _Credentials_ from the Jenkins dashboard to get information
    about credentials that are currently defined

# Security team

Did you know you can subscribe to the jenkins advisory google group?
Notifications are posted there.

its called: jenkinsci-advisories
https://groups.google.com/forum/#!forum/jenkinsci-advisories



_Source:_

https://jenkins.io/security/

Recommended read:

https://jenkins.io/doc/book/system-administration/security/
