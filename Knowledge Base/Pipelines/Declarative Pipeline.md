# Stages and Steps


The basic Declarative Pipeline structure is a sequence of stages which include steps:
- A stage groups tasks to be done; it includes steps
  - Stages are the logical segmentation of a Pipeline
- A step defines an actual task, such as execute a script or program
- Any non-setup work should occur within a stage block
- Code outside stage blocks executes on the Jenkins Master node
- Most of the code inside stage blocks executes on agent nodes

An artifact is a file produced as a result of a Jenkins build

- You see that we only have one artifact, which is the pipeline.log file.
- This is a raw log of the Pipeline that is produced by every Pipeline run.
- It is not a "user-friendly" file but it does include detailed information
  that is sometimes helpful when you are debugging complex Pipelines.

## Think About Pipeline Design

- It’s not good design to run unit tests and regression tests in the same stage.
- After running unit tests, you should run other types of medium-impact tests before you run regression tests.

## What is a Jenkinsfile ?

- The Jenkinsfile is your Pipeline (Pipeline-as-code)
- It uses a DSL based on Apache Groovy syntax
- Text file that can be edited with any text editor
- It should be located in the root of your SCM repository

## Jenkinsfile structure
- Here you can clearly see the structure of your Declarative Pipeline:
  - The first line of the file must be "pipeline" to open a pipeline block
    in which all the rest of the code is included.
      - One Jenkinsfile can contain multiple pipeline blocks
- The second line of the file must define the global agent
  - This may be agent any or agent none.
  - You can define different agents for different stages
    but you must always have a global agent statement.
    
## Summary of Jenkins Pipeline Sections

- agent — Specifies where the Pipeline or a specific stage executes
      - Declarative Pipeline requires a global declaration of agent as the first line in the pipeline block. It is possible to use               different agents for different stages but the global agent statement is always required.
- stage — A conceptually distinct subset of the Pipeline, such as "MyBuild", "MyTest", or "MyDeploy". Used to present Pipeline                     status/progress. Stage labels should be significant for your application.
- steps — A series of distinct tasks inside a stage.
- The Jenkinsfile can also include Sections, Directives, Options, and so forth;
  - For full information about Pipeline syntax, see jenkins.io/doc/book/pipeline/syntax 
 
    
