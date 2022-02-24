# Softalks Maven archetypes
To use an [archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) of this repository you must send its three [coordinates](https://maven.apache.org/pom.html#maven-coordinates) to the `mvn archetype:generate` [command](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html)
- **archetypeGroupId**
- **archetypeArtifactId**
- **archetypeVersion**

The command has a query mode that cannot be used with this repository. You can avoid entering that mode providing the coordinates and an aditional property named **archetypeCatalog** with the value ***local***

This four (and no other) values can also be predefined by means of the the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file)) file

A valid content for [that file](https://maven.apache.org/configure.html#mvn-jvm-config-file) (or a valid set of command line arguments) to create a new project based on [an specific](https://github.com/softalks/archetypes/tree/main/void) Softalks Maven archetype:
```
-DarchetypeGroupId=com -DarchetypeArtifactId=softalks.archetypes.void -DarchetypeVersion=1.0 -DarchetypeCatalog=local
```
There are three more mandatory properties whithout a deafult value to set for every archetype:
- groupId
- artifactId
- version
- package

You must provide them along with properties (if any) that are specific of the selected archetype. You should be able to provide this properties, one by one, when running Maven en in interactive mode

An example:
```
-DgroupId=com -DartifactId=softalks.archetypes.void -Dversion=0.9-SNAPSHOT
```
Before executing the command you must be sure to have your [settings.xml](https://maven.apache.org/settings.html) file configured like this one:
```
<?xml version="1.0" encoding="UTF-8"?>
<settings 
	xmlns="http://maven.apache.org/SETTINGS/1.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>archetype</id>
      <username>&#103;&#104;&#112;&#95;&#98;&#53;&#107;&#74;&#53;&#122;&#119;&#65;&#119;&#70;&#66;&#56;&#57;&#57;&#99;&#107;&#51;&#65;&#97;&#81;&#57;&#89;&#82;&#111;&#113;&#108;&#66;&#53;&#78;&#73;&#49;&#108;&#75;&#110;&#119;&#76;</username>
      <password>&#103;&#104;&#112;&#95;&#98;&#53;&#107;&#74;&#53;&#122;&#119;&#65;&#119;&#70;&#66;&#56;&#57;&#57;&#99;&#107;&#51;&#65;&#97;&#81;&#57;&#89;&#82;&#111;&#113;&#108;&#66;&#53;&#78;&#73;&#49;&#108;&#75;&#110;&#119;&#76;</password>
    </server>
  </servers>
  <profiles>
    <profile>
      <id>github</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <repositories>
        <repository>
          <id>archetype</id>
          <url>https://maven.pkg.github.com/softalks/archetypes</url>
        </repository>
      </repositories>
    </profile>
  </profiles>
</settings>
```
And, finally, run the archetype generation:
```
mvn archetype:generate -DgroupId=com -DartifactId=softalks.archetypes.void -Dversion=0.9-SNAPSHOT
```
Or, when possible:
```
mvn archetype:generate -Darchetype.properties=args.properties
```
