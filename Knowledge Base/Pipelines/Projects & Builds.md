# Defining Build Projects

## Project Types

- Jenkins supports two major types of projects:
    - Freestyle Job — manually configured in the Jenkins User Interface
    - Pipelines — Configuration as code stored in your Code Repository;
                  it uses a Jenkinsfile that supports 2 syntaxes:
        - Declarative: A simple DSL that efficiently
                       describes a pipeline (ala YAML/JSON)
        - Scripted: A programmatic DSL based on Apache Groovy;
                    more powerful and flexible but more complex

## Declarative Pipeline

  - The newest, and generally easiest, project type
  - Is more "opinionated" than Scripted and Freestyle
  - Uses a DSL based on Apache Groovy, although you do not need
    to know much about Apache Groovy syntax to use it


## Freestyle projects

- Original project type
- Very flexible
- Build any type of project (Apache Ant, Apache Maven, Makefile, Shell script…​)
- Supports most reporting plugins

### Disadvantages of Freestyle Jobs

- Not stored as code
- No default tracking of who made changes
- Flow control capabilities are primitive compared to Pipeline
- Requires lots of plugins for each project
- A project that could be defined in a single Pipeline instead requires many separate jobs
    - All these jobs are "chained" together
