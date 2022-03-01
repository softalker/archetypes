[![.github/workflows/void.yml](https://github.com/softalks/archetypes/actions/workflows/void.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/void.yml)
 [![.github/workflows/vanilla.yml](https://github.com/softalks/archetypes/actions/workflows/vanilla.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/vanilla.yml)
# Softalks Maven archetypes
This repository was created to contain the source code and artifacts of the [Maven archetypes](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) needed by other Softalks software components
## Archetype selection
To use an archetype of this repository you have first to identify it by setting three properties:
- **archetypeGroupId**
- **archetypeArtifactId**
- **archetypeVersion** (default: **1.0**)

The [Maven Archetype Plugin](https://maven.apache.org/archetype/maven-archetype-plugin/), at least in version `3.2.1`, loads a huge and useless (in this case) list of archetypes at [project generation time](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html). You can set the **archetypeCatalog** property with the value **internal** to avoid it

This four parameters of the generation process (and no other) can be predefined on the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file. The following file content represents a valid example to generate projects based on one specific Softalks Maven archetype: [void](https://github.com/softalks/archetypes/tree/main/void)
```
-DarchetypeGroupId=softalks -DarchetypeArtifactId=archetypes.void -DarchetypeVersion=1.0-SNAPSHOT -DarchetypeCatalog=internal
```
If you choose not to use this file you must put the same content on the command line (alongside all other properties) when generating the project
## Target project properties
Four more properties needs to be set before generating the project:
- **groupId**
- **artifactId**
- **version** (default: **1.0-SNAPSHOT**)
- **package** (default: **${groupId}**. Only used for projects containing Java code)

The selected archetype can have its own required properties and default values. Check its documentation before using it
## User level configuration
Your [settings.xml](https://maven.apache.org/settings.html) file needs to be configured for using this repository:
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
## Project generation
Having the files [.mvn/jvm.options](https://maven.apache.org/configure.html#mvn-jvm-config-file) and [settings.xml](https://maven.apache.org/settings.html) configured as specified above, the following command would be a valid example on how to use the [void Softalks archetype](https://github.com/softalks/archetypes/tree/main/void) to generate a project depending on `junit:junit:4.11`
```
mvn archetype:generate --batch-mode --update-snapshots -DgroupId=junit -DartifactId=junit -Dversion=4.11
