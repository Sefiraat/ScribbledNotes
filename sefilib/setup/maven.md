# Maven

The first thing to do is to add the repository and the dependency for SefiLib to your `pom.xml`

```xml
<repositories>
    <repository>
        <id>sefilib</id>
        <name>sefi-central</name>
        <url>https://sefiraat.jfrog.io/artifactory/default-maven-local</url>
    </repository>
</repositories>
```

```xml
<dependencies>
    <dependency>
        <groupId>io.github.sefiraat</groupId>
        <artifactId>SefiLib</artifactId>
        <version>[VERSION]</version>
        <scope>compile</scope>
    </dependency>
</dependencies>
```

Replace `[VERSION]` with the latest version of SefiLib, currently `0.1.3.0`

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
                        <pattern>io.github.sefiraat.sefilib</pattern>
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
