# Basics: Jenkins Master, Node, Agent and Executor

## Components

- The _Jenkins Master_ is the Jenkins service itself
  It is a webserver that also acts as a *brain* for deciding how, when, and where to run tasks.
- A _Node_ is a server where Jenkins runs jobs on _executors_
- The _agent_ is the tool that manages the executors on a remote _node_, on behalf of jenkins
+ Note that the Jenkins master runs on a _node._
