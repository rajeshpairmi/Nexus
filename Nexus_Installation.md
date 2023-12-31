# Nexus Installation 
## step1 : Download dependencies in /opt file for java & Nexus
- install wget (sudo yum install wget -y)
- download JDK17 https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.rpm to /opt folder
- download https://download.sonatype.com/nexus/3/latest-unix.tar.gz
- wget https://download.sonatype.com/nexus/3/nexus-3.45.0-01-unix.tar.gz
- tar -xzvf nexus-3.45.0-01-unix.tar.gz
- mv nexus-3.45.0-01 /opt/nexus # This helps in creating a shortcut object for version to nexus
## step2: Install java 
- sudo yum install java -y
## step3: add nexus user to perform the operations, provide sudo permissions and assign directory ownership of /opt/nexus and /opt/sonatype folders.
- userad nexus # create nexus user along with home directory
- /etc/sudoers
- add lines nexus ALL=(ALL) NOPASSWD:ALL # This allows nexus user to elevate permissions as needed.
- chown -R nexus:nexus /opt/nexus
- chmod 775 /opt/nexus
- chown -R nexus:nexus /opt/sonatype
- chowmod -R /opt/sonatype
## step4: modify nexus configuration to set 'nexus' user to run nexus
- vim /opt/nexus/bin.nexus.rc
- modify file run_as_user = "nexus"
## step5: create nexus as a service
- ln -s /opt/nexus/bin/nexus /etc/init.d/nexus
- su -nexus
- sudo systemctl start nexus
- sudo systemctl status nexus
## step6: access the nexus url externally
- publicIP:8081
