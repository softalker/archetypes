# Softalks Maven archetypes
There are four parameters of the [archetype:generate](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) goal that are required to create an archetype based Maven project and that, besides, can be be preconfigured by means of the [.mvn/jvm.config](https://maven.apache.org/configure.html#mvn-jvm-config-file) file. 
- The parameters **archetypeGroupId**, **archetypeArtifactId** and **archetypeVersion** (**1.0-SNAPSHOT** by default) identify the archetype
- The value ***local*** of the parameter **archetypeCatalog** avoids an unnecesary (and very slow) query to the Maven Central archetype registry

This is a valid content for that file (or a valid set of command line arguments) selecting [one](https://github.com/softalks/archetypes/tree/main/void) of this repository's archetypes to create a new Maven project:
```
-DarchetypeGroupId=com -DarchetypeArtifactId=softalks.archetypes.void -DarchetypeVersion=1.0 -DarchetypeCatalog=local
```
You should be able to predefine the rest of mandatory arguments using, in this case, a properties file (let's call it **args.properties**) that would be later referenced by the command line argument **archetype.properties**:
```
groupId=com
artifactId=softalks.archetypes.void
version=0.9-SNAPSHOT
```
But this posibility seems not to be working rigth now and you must pass all these parameters using the command line:
```
-DgroupId=com -DartifactId=softalks.archetypes.void -Dversion=0.9-SNAPSHOT
```

Note that each archetype can have its own required properties that you should include in the properties file/command line

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
