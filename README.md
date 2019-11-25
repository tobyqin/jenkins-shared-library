# jenkins-shared-library

Jenkins Shared Library Example. A Jenkins shared library is a collection of independent groovy scripts which can be used in Jenkins pipeline runtime.

1. You should add shared library from **Manage Jenkins** screen.
2. You can load the shared library at top of Jenkinsfile.

```groovy
@Library('my-jenkins-shared-library') _

mavenPipeline(
    appName: "my-awesome-app"
)
```

## library structure

Shared library will follow folder structure like this.

```
jenkins-shared-library
|____vars
|____src
|____resources
```

The `vars` directory includes all global scripts can be called directly from a pipeline.
The `src` directory is a regular java source directory, it will be added to classpath during every script compilation.
The `resources` directory will hold all the non-groovy files that required by your pipeline.

## usage example

The repo demonstrates a possibility of shared library implementation, the minimum example:

```groovy
@Library('jenkins-shared-library') _

mavenPipeline(
    appName: "my-awesome-app"
)
```

Above example will create a pipeline for maven project with specified stages:

1. Initialize
2. PreBuild
3. BuildArtifacts
4. SonarQube
5. Deploy
6. AutomationTest
7. Finalize

TODO: add a pipeline picture here.

It is very easy to apply these stages to Gradle projects.

```groovy
@Library('jenkins-shared-library') _

gradlePipeline(
    appName: "my-awesome-app"
)
```

Or nodejs project.

```groovy
@Library('jenkins-shared-library') _

nodejsPipeline(
    appName: "my-awesome-app"
)
```

## advanced usage

We may want to customize the pipeline in some case, example as:

```groovy
@Library('jenkins-shared-library') _

mavenPipeline(
    appName: "my-awesome-app",
    buildFunc: {
        sh "./build.sh"
    }
)
```

The full example of pipeline customization.

```groovy
TODO
```

## copyright & license

This is a demo of my jenkins shared library, no maintenance and support provided.

License under MIT.
