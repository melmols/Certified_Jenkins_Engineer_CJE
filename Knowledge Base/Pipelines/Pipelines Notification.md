# Parallel Steps

- Builds and tests for different platforms are independent
  - This means we can run them in parallel to make the Pipeline run faster
- If the build is successful, we stash the results of the build
  - Each test can then unstash the appropriate build to use
  
# Publishing Test results

- Each supported testing tool generates XML files that contain test results
- JUnit is a publisher that consumes the XML test reports and generates
  graphical visualizations of the historical test results
- Call the junit step to capture your test results

Example code: source CloudbeesUni

                    steps {
                      unstash 'Buzz Java 8'
                      sh './jenkins/test-all.sh'
                      junit '**/surefire-reports/**/*.xml'
                    }

# Sending Notifications

- Notifications can be sent through email as well as Slack and other channels
  - Must have necessary plugins installed
  - Must enable the notification type on the Jenkins Master
- You can specify different notifications to be sent when the Pipeline begins, when it completes, or only when it is successful or when it fails or when a specific stage is successful or fails
- Use environment variables to incorporate identifiers such as job name, build number, and build URL in your message
   - The examples use environment variables defined by Jenkins itself
   - Some plugins provide other environment variables that you can use
   - A full list of system-wide environment variables is available from the Jenkins dashboard


## Slack Notifications when Build Starts

                    stages {
                      stage ('Start') {
                        steps {
                          // send build started notifications
                          slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME}                                            [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                        }
                      }
                    }

## Email Notification when Build Starts
                    /* ... unchanged ... */

                    // send to email
                    emailext (
                      subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                      body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME}                         [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
                      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                    )

                    /* ... unchanged ... */



