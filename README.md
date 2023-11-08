# maven-wrapper
The repository project for executing Maven scripts with CI tools using `mvnw`.


## Dependency Plug-In 

### Downloading an Artifact

To download a single artifact, the command is:

`mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true -Dtransitive=false`
