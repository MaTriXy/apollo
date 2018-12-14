# Deploying Instructions

These instructions are based on the [instructions](http://central.sonatype.org/pages/ossrh-guide.html)
for deploying to the Central Repository using [Maven](http://central.sonatype.org/pages/apache-maven.html).
Note that this is for Spotify internal use only.

You will need the following:
- The username and password that Spotify uses to deploy to the Central Repository as described in
the open source manual on the internal wiki.
- [GPG set up on the machine you're deploying from](http://central.sonatype.org/pages/working-with-pgp-signatures.html)

Once you've got that in place, you should be able to do deployment using the following commands:

```
# deploy snapshot version
mvn clean deploy # -Prelease to test signing

# make and deploy a release
mvn release:clean release:prepare -Prelease -DautoVersionSubmodules=true
mvn release:perform -Prelease -DretryFailedDeploymentCount=3
```

Then update https://github.com/spotify/apollo/releases with release notes!
