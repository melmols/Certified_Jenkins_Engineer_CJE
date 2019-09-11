_CloudBees Inverted LogoCloudBees University: Jenkins Pipeline - Fundamentals | Pipeline Introduction© 2019 CloudBees, Inc. All Rights Reserved



# CONTINUOUS DELIVERY (CD)
Teams produce software in short cycles

Software is built and tested frequently

SCM hooks/webhooks detect source code changes and trigger the Pipeline to run

Software can be reliably released at any time

Applications in production can be incrementally updated

Requires a straightforward and repeatable process

Continuous Delivery means that every change is ready to be deployed

# CONTINUOUS DEPLOYMENT
Extends Continuous Delivery

Every change is automatically deployed into production

# WHAT IS CD FLOW?
CD is about setting a "flow", from SCM commit to deployed application

# cd pipeline

Flow begins when new code is checked into Source Code Management

New code is built and tested with the code that is already in SCM

One Pipeline can build the code for various platforms such as JVM 6, JVM 7 and JVM 8; or Linux, macOS and Windows; or iOS and Android

Several test stages are usually defined in the flow

One Pipeline can run different levels of tests on different platforms

When the code passes all tests, it is ready to be deployed to production

# PROJECT TYPES

The Continuous Delivery build flow is defined as a project, of one of the following types:

Freestyle Projects

Pipeline Projects

Declarative Pipeline

Scripted Pipeline

# FREESTYLE ("CHAINED") PROJECTS
Original Jenkins method for defining the build flow

Use job orchestration tools like the Job DSL plugin or Jenkins Job Builder

Are still supported but have limitations for Continuous Delivery and Deployment

# FREESTYLE LIMITATIONS
Provides only sequential steps

A job does not "survive" upon restarts (even planned restarts)

Chaining job with upstream/downstream:

Is only GUI-based; not code

Does not provide centralized configuration

    ## FREESTYLE CD FLOW
        A Real-world CD Flow requires features that Freestyle Projects cannot provide:

        Requires (Complex) Conditional Logic

        Requires Resources Allocation And Cleanup

        Involves Human Interaction For Manual Approval

        Should Be Resumable At Some Point On Failure


# JENKINS PIPELINE
jenkins.io/doc/book/pipeline

Jenkins Pipeline is a tool for defining your Continuous Delivery/Deployment flow as code

New fundamental "type" in Jenkins that conceptualizes and models a Continuous Delivery process

Two syntaxes:

Scripted: sequential execution, using Groovy expressions for flow control

Declarative: uses a framework to control execution

Uses the Pipeline DSL (Domain-specific Language)

programmatically manipulate Jenkins Objects

Captures the entire continuous delivery process as code

Pipeline is not a job creation tool like the Job DSL plugin or Jenkins Job Builder

# PIPELINE BENEFITS 
The pipeline functionality is:

Durable: The Jenkins master can restart and the Pipeline continues to run

Pausable: can stop and wait for human input or approval

Versatile: supports complex real-world CD requirements (fork, join, loop, parallelize)

Extensible: supports custom extensions to its "DSL" (Domain-specific Language)

### more benefits:

Reduces number of jobs

Easier maintenance

Decentralization of job configuration

Easier specification through code

# Pipeline as code

- A Pipeline is defined in a Jenkinsfile

  - Uses a DSL based on Apache Groovy

- Deployment flow is expressed as code

 -  Can express complex flows, conditionals and such

- The Jenkinsfile is stored on an SCM

  - Works with SCM conventions such as Branches and Git Pull Requests

  - Applies versioning, testing and merging against your CD Pipeline definition

  - Classic Web UI configuration is possible

JENKINS VOCABULARY 1/2
Master:

Computer, VM or container where Jenkins is installed and run

Serves requests and handles build tasks

Agent: (formerly "slave")

Computer, VM or container that connects to a Jenkins Master

Executes tasks when directed by the Master

Has a number and scope of operations to perform.

Node is sometimes used to refer to the computer, VM or container used for the Master or Agent; be careful because "Node" has another meaning for Pipeline

JENKINS VOCABULARY 2/2
Executor:

Computational resource for running builds

Performs Operations

Can run on any Master or Agent

Can be parallelized on a specific Master or Agent

# JENKINS PIPELINE SECTIONS
The Jenkinsfile that defines a Pipeline uses a DSL based on Apache Groovy syntax

Is structured in sections, called stages

Each stage includes steps

steps include the actual tests/commands to run

An agent defines where the programs and scripts execute

This is illustrated in the following simple Jenkinsfile:

            pipeline {
              agent { label 'linux' }
              stages {
                stage('MyBuild') {
                  steps {
                    sh './jenkins/build.sh'
                  }
                }
                stage('MySmalltest') {
                  steps {
                    sh './jenkins/smalltest.sh'
                  }
                }
              }
            }


