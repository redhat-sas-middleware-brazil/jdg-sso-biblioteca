# Red Hat JBoss Data Grid + Single-Sign On with RESTful API

## Overview
This project uses JBoss Data Grid to persist information sent through a RESTful API, authenticated with Red Hat Single-Sign On.

## Prerequisites
* Red Hat JBoss Enterprise Application Platform
* Red Hat JBoss Developer Studio
* Red Hat JBoss Data Grid
* Red Hat Single-Sign On
* A browser or Postman API (preferable)

## Installation, configuration and setup
### Installation of all 
1. At https://access.redhat.com download: 
* Server file for Red Hat JBoss Enterprise Application Platform, Data Grid and Single-Sign On.
* Jar installer for JBoss Developer Studio.
* Maven Repository for Red Hat JBoss Data Grid.
2. Unzip them into the desired folder.
3. For Postman, go to www.getpostman.com and download it.

### Configuration and setup
#### Red Hat JBoss EAP 
1.
2.
3.

#### Red Hat JBoss Data Grid
1. Go to Maven ${user.home}/.m2/ directory.
2. Update the settings.xml file as follows:
```
<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">

   <profiles>
      <profile>
         <id>jboss-datagrid-repository</id>
         <repositories>
            <repository>
               <id>jboss-datagrid-repository</id>
               <name>JBoss Data Grid Maven Repository</name>
               <url>file:///path/to/jboss-datagrid-7.0.0.GA-maven-repository/maven-repository</url>
               <layout>default</layout>
               <releases>
                  <enabled>true</enabled>
                  <updatePolicy>never</updatePolicy>
               </releases>
               <snapshots>
                  <enabled>false</enabled>
                  <updatePolicy>never</updatePolicy>
               </snapshots>
            </repository>
         <pluginRepositories>
            <pluginRepository>
               <id>jboss-datagrid-repository</id>
               <name>JBoss Data Grid Maven Repository</name>
               <url>file:///path/to/jboss-datagrid-7.0.0.GA-maven-repository/maven-repository</url>
               <layout>default</layout>
               <releases>
                  <enabled>true</enabled>
                  <updatePolicy>never</updatePolicy>
               </releases>
               <snapshots>
                  <enabled>false</enabled>
                  <updatePolicy>never</updatePolicy>
               </snapshots>
            </pluginRepository>
         </pluginRepositories>
      </profile>
   </profiles>
   <activeProfiles>
      <!-- make the profile active by default -->
      <activeProfile>jboss-datagrid-repository</activeProfile>
   </activeProfiles>
</settings>
```
3. Make sure to change the path correctly in the settings.xml file.

#### Red Hat Single-Sign On
1. Boot the Server and open your browser at http://localhost:8080/auth. 
2. Create a username/password and go to http://localhost:8080/auth/admin. 
3. Log in with your new user.
4. Go to Users and add a new one at `Add User`. This will be the user required to log into your jsp page.
5. Change the password at `Credentials` and make sure the Temporary button is off.
6. Go to Clients and click on `Create`.
7. Set the id name as the same name of the application (in this case, data_grid-0.0.1-SNAPSHOT).
8. Make sure that the URLs are all set to http instead of https. 
9. Save it.

## Deployment 
