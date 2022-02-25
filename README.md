[![.github/workflows/void.yml](https://github.com/softalks/archetypes/actions/workflows/void.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/void.yml)
# Softalks Maven archetypes
To use an [archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) of this repository you have to identify it by loading two properties:
- **archetypeGroupId**
- **archetypeArtifactId**

If you don't want to use the default version (**1.0**) you need also to load the property **archetypeVersion**

Loading **archetypeCatalog** with the value ***internal***  will avoid an unnecesary query to the Maven remote catalog (this should be fixed in a future Maven version)

This four values (and no other) can be predefined by means of the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file

The following file content (or command line arguments) will allow creating a project based on a Softalks Maven archetype: [void](https://github.com/softalks/archetypes/tree/main/void) (archetype for transient projects having one specific dependency)
```
-DarchetypeGroupId=softalks -DarchetypeArtifactId=archetypes.void -DarchetypeVersion=1.1 -DarchetypeCatalog=internal
```
Every archetype needs another four properties before you can use it to create the project:
- groupId
- artifactId
- version (default: **1.0-SNAPSHOT**)
- package (default: **${groupId}**)

The selected archetype can define its own required properties with its own default values. Check its documentation before using it

You must also configure your [settings.xml](https://maven.apache.org/settings.html) file to be like this:
```
<settings 
	xmlns="http://maven.apache.org/SETTINGS/1.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  ...
  <servers>
    ...
    <server>
      <id>archetype</id>
      <username>&#103;&#104;&#112;&#95;&#98;&#53;&#107;&#74;&#53;&#122;&#119;&#65;&#119;&#70;&#66;&#56;&#57;&#57;&#99;&#107;&#51;&#65;&#97;&#81;&#57;&#89;&#82;&#111;&#113;&#108;&#66;&#53;&#78;&#73;&#49;&#108;&#75;&#110;&#119;&#76;</username>
      <password>&#103;&#104;&#112;&#95;&#98;&#53;&#107;&#74;&#53;&#122;&#119;&#65;&#119;&#70;&#66;&#56;&#57;&#57;&#99;&#107;&#51;&#65;&#97;&#81;&#57;&#89;&#82;&#111;&#113;&#108;&#66;&#53;&#78;&#73;&#49;&#108;&#75;&#110;&#119;&#76;</password>
    </server>
  </servers>
  ...
  <profiles>
    ...
    <profile>
      <id>softalks-archetypes</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <repositories>
        ...
        <repository>
          <id>archetype</id>
          <url>https://maven.pkg.github.com/softalks/archetypes</url>
        </repository>
      </repositories>
    </profile>
  </profiles>
  ...
</settings>
```
Lets suposse you:
- have the [.mvn/jvm.options](https://maven.apache.org/configure.html#mvn-jvm-config-file) file content specified above for using the [void](https://github.com/softalks/archetypes/tree/main/void) archetype
- want to use that archetype to generate a project depending on `junit:junit:4.11`. 

You can get your project, in both batch and interactive modes, by running:
```
mvn archetype:generate -DgroupId=junit -DartifactId=junit -Dversion=4.11

[command](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) `mvn archetype:generate`
