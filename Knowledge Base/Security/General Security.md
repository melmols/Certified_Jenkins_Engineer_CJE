# Why do we need security? 
(if you ever asked this question, hopefully not)

- Jenkins is an automation server: it runs tasks
- Does everyone have the right to run tasks on Jenkins, anonymously ?
- Your Jenkins instance could be used for cryptocurrency mining, to launch a DDoS bot, or to send spam email
- Jenkins accesses source code and generates binaries
- These are valuable and need to be protected from both theft and unauthorized modification

### I pledge...


- To keep software updated: Security and other features get better with each release
- Understand security vulnerabilities: Configure features to protect the environment
- Make use of least privilege principle: Grant each user only the rights they need
- Defense in depth: Systems are layered; put appropriate security on all layers
- To prevent; detection is better: Continuously monitor to detect any intrusions

### What Needs to be Secured?

- Access to Git or other SCM repository
- Access to Jenkins Master and all nodes
- Resources created by Pipeline
- Executable steps of a Pipeline

# Jenkins Security

### Defaults

- Each Jenkins installatin is "locked down" by default
  - *Butler is the only account created
  - *Butler can do everything
  - Other users can not do pretty much anything until the admin (butler) explicitly configures permissions
- Other security options are set to a restrictive level

#### Identities

- anonymous user — any user who is not authenticated
- admin (System) user — has full access to all Jenkins resources
  All background threads run under this identity
- authenticated user — defined as a group that includes all authenticated users other than butler
  Administrator can define different permissions to different users within this group

#### Other default features

- JNLP TCP Port is disabled
  * Used to commmunicate with agents launched via the JNLP protocol, for example: Windows-based agents
- Markup Formatter is set to plain text
  * Unsafe characters such as < and & are treated as text characters to prevent unsafe HTML and/or JavaScript
- Cross Site Request Forgery (CSRF) protection is enabled 
  * A CSRF attack can lead to a malicious actor to delete projects, alter builds, or modify the Jenkins system configuration
- Agent-to-Master Access Control sybsystem is turned on
  * Administrators can create specific exemptions that are required
 
 
 ### Enabling security
 
 Navigate to the global config: Manage Config >  Enable Global Security
 
 #### Security Realms for authentication
 
- Setting Security Realms tells Jenkins what system to use for authentication
    * Security Realm is a dedicated *database* for user and passwords
- 4 kinds of *Realms* supported out of the box, covered below:
    1)  Jenkins User Database ( you can choose for users to sign up)
    2)  Unix user/group Database
    3)  Servlet Container
    4)  External LDAP
    5)  Operations Center SSO
- New Realms types can be added by other plugins
    * E.g. Active Directory
- Users who are not authenticated are always bound to the "Anonymous" special user
 

 
