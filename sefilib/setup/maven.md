# Maven

The first thing to do is to add the dependency into your pom.xml file. The artifacts are hosted on Maven Central so no additional repositories should be required.

```xml
<dependencies>
    <dependency>
        <groupId>dev.sefiraat</groupId>
        <artifactId>SefiLib</artifactId>
        <version>[VERSION]</version>
        <scope>compile</scope>
    </dependency>
</dependencies>
```

Replace `[VERSION]` with the latest version of SefiLib, noted below.

![Maven Central](https://img.shields.io/maven-central/v/dev.sefiraat/SefiLib?color=%23aa\&label=SefiLib%20-%20Maven%20Central\&style=for-the-badge)

The library needs to be shaded into your plugin's jar.

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-shade-plugin</artifactId>
            <version>3.3.0</version>
            <configuration>
                <relocations>
                    <relocation>
                        <pattern>dev.sefiraat.sefilib</pattern>
                        <shadedPattern>[YOUR_PACKAGE].sefilib</shadedPattern>
                    </relocation>
                </relocations>
                <filters>
                    <filter>
                        <artifact>*:*</artifact>
                        <excludes>
                            <exclude>META-INF/*</exclude>
                        </excludes>
                    </filter>
                </filters>
            </configuration>
            <executions>
                <execution>
                    <phase>package</phase>
                    <goals>
                        <goal>shade</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>xml
</build>
```

Replace `[YOUR_PACKAGE]` with the name of your plugin's package
