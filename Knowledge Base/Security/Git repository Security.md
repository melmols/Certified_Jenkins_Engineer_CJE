
# Securing the Git repository

## First, access

Please note, the Jenkins security settings secure the Jenkins install. To secure the Git Repo, access to the Git Repo must be 
configured in the Git Repository itself.

### Collaborators

Define collaborators who can access the repository
  - Each collaborator can be assigned admin, read or write permissions
  - For maximum security, limit the number of people who can merge a PR to the master branch
  - Require that each PR must be approved by someone other than the person who created it
    - This helps protect your repository from malicious Jenkinsfiles and other code
    
 
