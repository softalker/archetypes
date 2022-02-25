[![.github/workflows/void.yml](https://github.com/softalks/archetypes/actions/workflows/void.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/void.yml)
# Softalks Maven archetypes
To use an [archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) of this repository you must provide the value for two properties before invoking the [command](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) `mvn archetype:generate`:
- **archetypeGroupId**
- **archetypeArtifactId**

If you don't want to use the default version (**1.0**) you need also to provide a value for **archetypeVersion**

Providing the value ***local*** or ***internal*** for **archetypeCatalog** you will avoid an unuseful (in this case) and slow query to the remote catalog

This four values (and no other) can be predefined by means of the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file

The following file content (or command line arguments) will allow creating a project based on a Softalks Maven archetype: [void](https://github.com/softalks/archetypes/tree/main/void) (archetype for transient projects having one specific dependency)
```
-DarchetypeGroupId=softalks -DarchetypeArtifactId=archetypes.void -DarchetypeVersion=1.1 -DarchetypeCatalog=internal
```
Every archetype needs another four values to know how to create the Maven project:
- groupId
- artifactId
- version (default: **1.0-SNAPSHOT**)
- package (default: **${groupId}**. Not used for projects having `<packaging>pom</packaging>` in pom.xml)
- interactiveMode (default: **true**. Needed only to force interactive mode when --batch-mode/-B are in place)

You must provide also the properties (if any) required by the selected archetype:
- As command line arguments (valid for --batch-mode and --interactive-mode)
- One by one, in interactive mode: `mvn archetype:generate -DinteractiveMode=true -DaskForDefaultPropertyValues=true`

  > The first argument forces interactive mode (the default) if batch mode is in place. The second one makes archetype specific properties having a default value behave like its generic counterparts (version & package) when running in interactive mode. That is: asking the user before setting the property with its default value

Before executing the command you must be sure to have your [settings.xml](https://maven.apache.org/settings.html) file configured like this:
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
