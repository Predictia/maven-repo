maven-repo
==========

Maven repository for Predictia's binaries

How to use it
-------------

Add this in your pom.xml file:

    <repositories>
      <repository>
        <id>predictia-public-snapshots</id>
        <url>https://raw.github.com/Predictia/maven-repo/master/snapshots</url>
      </repository>
      <repository>
        <id>predictia-public-releases</id>
        <url>https://raw.github.com/Predictia/maven-repo/master/releases</url>
      </repository>
    </repositories>


To deploy in this Maven repository
----------------------------------

Clone the git repository locally :

    git clone git@github.com:Predictia/maven-repo.git

Then deploy the files in your local repo (beware if it is a release or a snapshot !!!):

    mvn -DaltDeploymentRepository=snapshot-repo::default::file:PATH_TO/maven-repo/snapshots/ clean deploy

And commit and push your changes to github:

    git commit -m "MESSAGE"
    git push origin master
