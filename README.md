[![.github/workflows/void.yml](https://github.com/softalks/archetypes/actions/workflows/void.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/void.yml)
# Softalks Maven archetypes
To use an [archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) of this repository you must send its three [coordinates](https://maven.apache.org/pom.html#maven-coordinates) to the `mvn archetype:generate` [command](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html)
- **archetypeGroupId**
- **archetypeArtifactId**
- **archetypeVersion**

The command has a query mode that cannot be used with this repository. You can (almost) avoid entering that mode by providing the three coordinates alongside an aditional property: **archetypeCatalog** with a fixed value: ***local***

This four values (and no other) can be predefined by means of the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file

The following file content (or command line arguments) will allow creating a project based on a Softalks Maven archetype: [void](https://github.com/softalks/archetypes/tree/main/void)
```
-DarchetypeGroupId=com.softalks -DarchetypeArtifactId=archetypes.void -DarchetypeVersion=1.0 -DarchetypeCatalog=local
```
Every archetype needs four more properties to be defined:
- groupId
- artifactId
- version (default: **1.0-SNAPSHOT**)
- package (default: **${groupId}**)

You can provide this properties alongside the properties (if any) required by the selected archetype:
- As command line arguments (e.g. `mvn archetype:generate ... -DgroupId=...`) what will work in both batch and interactive modes
- One by one, when requested, in interactive mode: `mvn archetype:generate -DinteractiveMode=true -DaskForDefaultPropertyValues=true`

  > The first argument forces interactive mode (the default) if batch mode is in place. The second one makes archetype specific properties with default values behave like its generic counterparts (version & package) when running in interactive mode (asking the user before setting the property with its default value)

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
mvn archetype:generate ...
