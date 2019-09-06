# Basics: Jenkins Master, Node, Agent and Executor

## Components

- The _Jenkins Master_ is the Jenkins service itself
  It is a webserver that also acts as a *brain* for deciding how, when, and where to run tasks.
- A _Node_ is a server where Jenkins runs jobs on _executors_
- The _agent_ is the tool that manages the executors on a remote _node_, on behalf of jenkins
+ Note that the Jenkins master runs on a _node._

### Jenkins Master

- This is where Jenkins is installed
- Management tasks like configuration, authorization/authentication are executed on the master
- Files written when a Pipeline executes are written to the filesystem
  on the master unless they are off-loaded to an artifact repository (nexus or artifactory)
 - You should not run the workload of building projects on the Master in a production environment
    - You can do this for demos or studying
 -  Some administrative tasks (liek running a backup) are executed on the node that hosts the Jenkins Master
 
 ### Nodes
 
 -  Provide the tools and packages to be used during your builds:
    - Application SDKs such as the JDK or C++ build tools
    - Apache Maven, Gradle, npm, shells, Docker etc
 -  Jenkins monitors each attached node for:
    - Disk space free temp space, free swap
    - Clock time/sync and response time
 -  A node is taken offline if any of these pass the configured threshold
    - You can view available nodes and their executors listed at the bottom left of the jenkins dashboard
    - To manage, go to *Manage Jenkins > Manage Nodes* to view, add, remove, control, and monitor nodes
    
 ### Agents
 
 -  They manage the task execution on behalf of the Jenkins Master, using "Executors"
 -  Are actually small Java client processes that connect to a Jenkins Master over the Java Network Laun Protocol (JNLP)
 -  Each agent is effectively a process with its own PID (Process Identifier) on the host machine
 -  Can use any operating system that supports Java
 
 #### Using Agents
 
 -  They provide different environments for building and testing software
    - Use the underlying node tools
    - Often implemented as  "containers" (such as docker)
-   For example, you can define agents for JDK7 and JDK8 or for Fedora, Debian/Ubuntu, or Linux/macOS/Windows
-   For Pipelines, an agent provides the context in which a stage is executed

#### Using Agents in a declarative pipeline

- Each Pipeline stage is assigned to an agent
- Use *agent any* to specify any available agent
- Use *agent none* for a *stage* that must run with the agent context
- Special purpose agents can be assigned a *label* that is used to access that agent in the Pipeline
- Pipeline writers can also define an agent from within the Pipeline code

#### Executor

- A slot for execution of tasks
- Is effectively a thread in the agent
- The number of executors on a node defines the number of concurrent tasks that can be executed on that node at one time
  - In other words, the number of concurrent Pipeline stages that can execute on that node at one time
  
##### How Many?

- The proper number of executors per node must be determined based on the resources
  available on the node and the resources required for the workload
    - One executor per node is the safest configuration
    - One executor per CPU core may work well if the tasks being run are small enough
    - Monitor I/O performance carefully when running multiple executors on a node
    - Also monitor CPU load, memory usage, and I/O throughput
  - Configure the master node with 0 executors to ensure that no builds run on the master
    - You can run builds on the master for demonstration purposes but should never do this in production environments
     - This is because a build that runs on the Jenkins master can access the same Jenkins home directory with the full permissions            of the jenkins user.
    - This means that such a build can steal secrets, modify data, etc

##### Monitoring Executors

  - Go to *Manage Jenkins > Load Statistics* to track the utilization of executors
      This gives you a graph that identifies:
      - Number of online executors
      - Number of busy executors
      - Number of available executors
      - Queue length (number of jobs waiting for an executor)
