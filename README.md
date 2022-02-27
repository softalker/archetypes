[![.github/workflows/void.yml](https://github.com/softalks/archetypes/actions/workflows/void.yml/badge.svg)](https://github.com/softalks/archetypes/actions/workflows/void.yml)
# Softalks Maven archetypes
To use an [archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html) of this repository you have first to identify it by setting three properties:
- **archetypeGroupId**
- **archetypeArtifactId**
- **archetypeVersion** (default: **1.0**)

The [Maven Archetype Plugin](https://maven.apache.org/archetype/maven-archetype-plugin/) (at least in version `3.2.1`) loads, by default, a big remote catalog (useless en this case). You can set the **archetypeCatalog** property with the value **internal** to avoid it

This four parameters of the generation process (and no other) can be predefined on the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file. The following file content will allow the generation of projects based on the Softalks Maven archetype: [void](https://github.com/softalks/archetypes/tree/main/void)
```
-DarchetypeGroupId=softalks -DarchetypeArtifactId=archetypes.void -DarchetypeVersion=1.1 -DarchetypeCatalog=internal
```
> If prefer not to use that file you must put the content directly on the command line, when invoking the `archetype:generate` goal, as you need to do with the rest of properties needed for the project generation

Every archetype needs another four properties before you can use it to generata a project:
- groupId
- artifactId
- version (default: **1.0-SNAPSHOT**)
- package (default: **${groupId}**. Only used for projects containing Java code)

The selected archetype can define its own required properties and default values. Check its documentation before using it

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
We can now create (by example) a project based on the [void](https://github.com/softalks/archetypes/tree/main/void) archetype (supposing we have the [.mvn/jvm.options](https://maven.apache.org/configure.html#mvn-jvm-config-file) file content specified above) that will depend on `junit:junit:4.11` using the [archetype:generate](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) Maven goal
```
mvn archetype:generate --batch-mode -DgroupId=junit -DartifactId=junit -Dversion=4.11
