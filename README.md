maven-repo
==========

Maven repository for Predictia's binaries

How to use it
-------------

Add this in your pom.xml file:

    <repositories>
      <repository>
        <id>predictia-public-snapshots</id>
        <url>https://raw.githubusercontent.com/Predictia/maven-repo/master/snapshots</url>
      </repository>
      <repository>
        <id>predictia-public-releases</id>
        <url>https://raw.githubusercontent.com/Predictia/maven-repo/master/releases</url>
      </repository>
      <repository>
        <id>predictia-thirdparty</id>
        <url>https://raw.githubusercontent.com/Predictia/maven-repo/master/thirdparty</url>
      </repository>
    </repositories>


To deploy in this Maven repository
----------------------------------

Clone the git repository locally :

    git clone git@github.com:Predictia/maven-repo.git

Then deploy the files in your local repo (beware if it is a release or a snapshot !!!):

    mvn -DaltDeploymentRepository=snapshot-repo::default::file:PATH_TO/maven-repo/snapshots/ clean deploy

Deploy jars to third party repo:

    mvn deploy:deploy-file -DgroupId=the.group.id -DartifactId=artifactid -Dversion=version -Dpackaging=jar -Dfile=/path/to/my_jar_file.jar -DrepositoryId=local-thirdparty-repo -Durl=file:PATH_TO/maven-repo/thirdparty/


Relase new version to local maven repository

```
mvn release:prepare
mvn release:perform -Darguments=-DaltDeploymentRepository=releases-repo::default::file:PATH_TO/maven-repo/releases/
```

And commit and push your changes to github:

    git commit -m "MESSAGE"
    git push origin master
