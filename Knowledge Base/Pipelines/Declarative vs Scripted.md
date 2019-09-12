# DECLARATIVE VERSUS SCRIPTED PIPELINE
Two different syntaxes for Pipeline

Both are built on same Pipeline subsystem

Both definitions are stored in a Jenkinsfile under SCM ("Pipeline-as-code")

Both rely on Apache Groovy syntax (JVM-based scripting language)

Both can use steps built into Pipeline or provided in plugins

Both support shared libraries

# SCRIPTED PIPELINE
Executed serially, from top down

Relies on Groovy expressions for flow control

Requires extensive knowledge of Groovy syntax

Very flexible and extensible

Limitations are mostly Groovy limitations

Power users with complex requirements may need it

Novice users can easily mess up the syntax

# DECLARATIVE PIPELINE
Stricter, pre-defined structure

Requires only limited knowledge of Groovy syntax

Using Blue Ocean simplifies the Pipeline creation process even more

Encourages a declarative programming model

Reduces the risk of syntax errors

Use the script step to include scripts within a Declarative Pipeline


# CLASSIC WEB UI
You code the Jenkinsfile using the text editor of your choice

Use the Jenkins dashboard to run and configure the Pipeline

Provides some tools to simplify the process, such as the Snippet Generator that generates a line of code based on the task that is required and information you input to an appropriate form

Supports all features for Declarative and Scripted Pipelines
