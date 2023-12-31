# Integrating maven and nexus to store artifacts generated through maven
## Its a 2 step process, authentication and transfer
- maven server --------------> Nexus server
- devops engineer shares the repositry url to the developer to edit the pom.xml
- maven server -- authentication --> Nexus server
- maven server -- transfer --------> Nexus server
# Maven authentication to Nexus server
## Create 2 repositories in the nexus one for release and other for snapshot
- share the admin details with the maven settings
- /opt/apache-maven-x.x.x/conf/settings.xml
- edits servers section
- <server> <id>nexus</id> <username>admin</username> <password>nexus</password> </server>
## Configuring Maven pom.xml to upload artifacts to release or snapshot repository
 <repository>
 <id>nexus</id>
 <name>Release Repos</name>
 <url>http://34.125.31.111:8081/repository/first-release/</url>
</repository>

<snapshotRepository>
<id>nexus</id>
<name>Snapshot Repos</name>
<url>http://34.125.31.111:8081/repository/first-snapshot/</url>
</snapshotRepository>
