# Publishing test results

- Each suported testing tool generates XML files that contain test results
- JUnit is a publisher that consumer the XML files that contain test results
- To call a JUnit step:
    
                steps {
                        unstash 'Buzz Java 8'
                        sh './jenkins/test-all.sh'
                        junit '**/surefire-reports/**/*.xml'
                      }
                    
  
  
  # Sending Notifications
  
- Notifications can be sent through email as well as Slack and other channels
    - Must have necessary plugins installed
    - Must enable the notification type on the Jenkins Master
- You can specify different notifications to be sent when the Pipeline begins, when it completes, or only when it is successful or when     it fails or when a specific stage is successful or fails
- Use environment variables to incorporate identifiers such as job name, build number, and build URL in your message

    - The examples use environment variables defined by Jenkins itself
    - Some plugins provide other environment variables that you can use
    - A full list of system-wide environment variables is available from the Jenkins dashboard
    
        - Slack Notifications when Build Starts:
                      
                      stages {
                        stage ('Start') {
                          steps {
                            // send build started notifications
                            slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'                                                         (${env.BUILD_URL})")
                          }
                        }
                      }
                      
         - Email Notification when Build Starts
                     
                     /* ... unchanged ... */

                      // send to email
                      emailext (
                        subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                        body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                          <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]                                       </a>&QUOT;</p>""",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                      )

                      /* ... unchanged ... */
                      
         -  To add an approve deploying to prod step: 

                    steps {
                              input(message: 'Deploy to Stage', ok: 'Yes, let\'s do it!')
                          }

        -   You can set timeout for the entire Pipeline or for any stage timeout for the entire Pipeline timeout for the entire Pipeline
             Note: you can add a 'when' clause to specify to skip if its not in the master branch etc 
             Stage('blabla) when { branch 'master' }
                                                                                                                
    
                    options {
                                                                                                              
                      timeout(time: 30, unit: 'MINUTES')
                    }
                    timeout for an input stage
                    steps {
                      timeout(time:3, unit:'DAYS') {
                        input(message: 'Deploy to Stage', ok: 'Yes, let\'s do it!')
                      }
                    } 
                    

# POST

-   post section contains steps to be executed at the end of a Pipeline run or stage
-   post section is divided into conditions such as always, success, failure
-   Each condition lists steps to be executed
                          
-   _Always_ archive the artifacts
    - Even if the stage fails, you want to try to save artifacts and test results so you have them after the Pipeline run finishes
-   _Stash_ the build only on success
                    
                    ...
                    stage('Build Java 7') {
                      steps {
                        sh '''
                          echo I am a $BUZZ_NAME!
                          ./jenkins/build.sh
                        '''
                      }
                      post {
                        always {
                          archiveArtifacts(artifacts: 'target/*.jar', fingerprint: true)
                        }
                        success {
                          stash(name: 'Buzz Java 7', includes: 'target/**')
                        }
                      }
                    }
