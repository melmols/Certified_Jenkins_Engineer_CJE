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
