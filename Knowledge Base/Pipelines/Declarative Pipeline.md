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
