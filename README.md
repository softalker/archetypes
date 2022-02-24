# Softalks Maven archetypes
There are four parameters for the [archetype:generate](https://maven.apache.org/archetype/maven-archetype-plugin/generate-mojo.html) goal that can be preconfigured in the .mvn/jvm.config file
```
-DarchetypeGroupId=com -DarchetypeArtifactId=softalks.archetypes.void -DarchetypeVersion=1.0-SNAPSHOT -DarchetypeCatalog=local
```
To create a Maven project based on an archetype provided by this project you should start by defining a properties file with all the mandatory arguments:
```
archetypeGroupId=com
archetypeArtifactId=softalks.archetypes.void
archetypeVersion=1.0-SNAPSHOT
groupId=com
artifactId=softalks.archetypes.void
version=0.9-SNAPSHOT
package=unnecessary # only used for jar packaging but always required
```
And running:
```
mvn archetype:generate -Darchetype.properties=args.properties
```
Before using any of the archetypes defined in this project you must set up your [settings.xml](https://maven.apache.org/settings.html) file like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<settings 
	xmlns="http://maven.apache.org/SETTINGS/1.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>archetype</id>
      <username>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</username>
      <password>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</password>
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
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
</settings>
```
