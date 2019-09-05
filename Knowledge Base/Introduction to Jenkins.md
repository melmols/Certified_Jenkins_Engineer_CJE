#Basics


## Continuous Workflow

###Best Practices

- Put the modified code into SCM
- Build code
- Rest the built code
- Deploy Tested code
- Freeze a copy of the deployed code

## Continuous Integration Loop

                      
                                          _Source Control
                                       -                   -   
                                 Commit                    Initiating CI process   
                                    -                         - 
                           _Development                        _Build
                                      -                      -
                                 Report                    Testing 
                                          -              -   
                                              _Testing

### Concepts

+ _Continuous Integration (CI) is the frequent, automatic integration of code
Automatically tests all new and modified code with the master code
+ _Continuous Delivery (CD) is the natural extension of CI
Ensures that the code is always ready to be deployed
Manual approval is required to actually deploy the software to production
+ _Continuous Deployment automatically deploys all validated changes to production
Frequent Feedback enables issues to be found and fixed quickly                                              
                                              

### Build Tools

They help specify how to build and test your software and when/where/how to deploy it
Use a tool such as Apache Maven, Gradle, npm, Apache Ant, or make to define the specific actions required at each step




## Source Code Management (SCM) Or VCS

Provide recording of changes, merging and tracking capabilities
### Advanced SCM

Advanced SCMs allow a Pipeline run to be triggered by a code modification
Git technology supports this ability
Git is the core technology used in many cloud-based SCM systems, including GitHub, Bitbucket, GitLab, Visual Studio Team Services, Gitea, Gogs, Assembla, Helix, and Deveo
Most of these cloud-based SCM systems are also available as on-premise solutions
Pull-based SCM is also supported by other SCMs such as Mercurial (in Bitbucket) and Perforce
Support the most powerful Jenkins capabilities

### Best Practices
#### Code Modification workflow

To modify the code:
- Clone (copy) the repo to your local computer
- Create a branch for the change you want to make
- Modify your local codebase and test your changes locally
- Create a commit that contains the modified codebase
- Push your commit to the remote, official repository

#### Update workflow

- After you push your commit to the remote repository, create a Pull Request (PR) to request that it be merged into the master branch.
- Jenkins then builds and tests the contents of your changes against what is currently in master and flags any issues
- Colleagues review, comment, and approve your PR
- The contents of the PR can be modified on the remote site or you can push additional commits from your local clone
- When ready, the PR can be merged to master
