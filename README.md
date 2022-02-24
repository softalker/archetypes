# Softalks Maven archetypes
Giving a file args.properties like this:
```
archetypeGroupId=com
archetypeArtifactId=softalks.archetypes.void
archetypeVersion=1.0-SNAPSHOT
groupId=com
artifactId=softalks.archetypes.void
version=0.9-SNAPSHOT
package=unnecessary # but required by the maven-archetype-plugin
```
And running:
```
mvn archetype:generate -DarchetypeCatalog=local -Darchetype.properties=args.properties
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
