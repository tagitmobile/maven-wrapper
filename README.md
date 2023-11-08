# maven-wrapper
The repository project for executing Maven scripts with CI tools using `mvnw`.


## Dependency Plug-In 

### Downloading a Single Artifact

To download a single artifact with it's dependency information, the commands are:

```
mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT:jar -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true
mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT:pom -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true
mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT:module -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true
```

> **Maven POM and Gradle Module**
>
> The `.pom` and `.module` files must be preserved to ensure that the artifact dependencies are preserved.

For projects with sources and javadoc, include the following commands:

```
mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT:jar:sources -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true
mvnw dependency:copy -Dartifact=com.tagit.commons:tagit-core:7.5.0.M1-SNAPSHOT:jar:javadoc  -DoutputDirectory=downloaded_artifacts -Dmdep.useBaseVersion=true
```

If done properly, you should have downloaded the following files:
```
.\downloaded_artifacts\tagit-core-7.5.0.M1-SNAPSHOT-javadoc.jar
.\downloaded_artifacts\tagit-core-7.5.0.M1-SNAPSHOT-sources.jar
.\downloaded_artifacts\tagit-core-7.5.0.M1-SNAPSHOT.jar
.\downloaded_artifacts\tagit-core-7.5.0.M1-SNAPSHOT.module
.\downloaded_artifacts\tagit-core-7.5.0.M1-SNAPSHOT.pom
```

> For more information, refer to https://maven.apache.org/plugins/maven-dependency-plugin/copy-mojo.html

## Deploy Plug-In

### Publishing a Single Artifact

To upload a single artifact with it's dependency information, the command is:

```
mvnw deploy:deploy-file -Durl=https://nexus.tagitmobile.com/repository/maven-qa -DrepositoryId=tagit-central -Dfile="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.jar" -DgroupId="com.tagit.commons" -DartifactId="tagit-core" -Dversion="7.5.0.M1" -Dfiles="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.pom,downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.module" -Dclassifiers="," -Dtypes="pom,module" -DgeneratePom=false -DpomFile="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.pom" -Dnexus.username="gradle" -Dnexus.password="Tagit123" -s "./settings.xml"
```

> **Maven POM and Gradle Module**
>
> The `.pom` and `.module` files must be preserved to ensure that the artifact dependencies are preserved.

For projects with sources and javadoc, include the following commands:

```
mvnw deploy:deploy-file -Durl=https://nexus.tagitmobile.com/repository/maven-qa -DrepositoryId=tagit-central -Dfile="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.jar" -DgroupId="com.tagit.commons" -DartifactId="tagit-core" -Dversion="7.5.0.M1" -Dfiles="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.pom,downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.module" -Dclassifiers="," -Dtypes="pom,module" -DgeneratePom=false -DpomFile="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT.pom" -Dnexus.username="gradle" -Dnexus.password="Tagit123" -s "./settings.xml" -Dsources="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT-sources.jar" -Djavadoc="downloaded_artifacts/tagit-core-7.5.0.M1-SNAPSHOT-javadoc.jar"
```

> For more information, refer to https://maven.apache.org/plugins/maven-deploy-plugin/deploy-file-mojo.html
