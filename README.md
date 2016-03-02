# test-ebean-enhancement tile

Maven tile that performs the Ebean enhancement on entity beans in target/test-classes.

## Example use

In your project pom under build / plugins add the tiles-maven-plugin with the following configuration. Note that this example also brings in the java-compile tile.

```xml
      <!-- maven build / plugins -->

      <plugin>
        <groupId>io.repaint.maven</groupId>
        <artifactId>tiles-maven-plugin</artifactId>
        <version>2.8</version>
        <extensions>true</extensions>
        <configuration>
          <tiles>
            <tile>org.avaje.tile:test-ebean-enhancement:1.1</tile>
          </tiles>
        </configuration>
      </plugin>

```



## What it does


```xml
  <!-- defaults, override in your project pom if needed -->

  <properties>
    <ebeanorm-enhancement.plugin.args>debug=0</ebeanorm-enhancement.plugin.args>
    <avaje-ebeanorm-mavenenhancer.version>4.9.1</avaje-ebeanorm-mavenenhancer.version>
    <avaje-ebeanorm-mavenenhancer.target-test-classes>target/test-classes</avaje-ebeanorm-mavenenhancer.target-test-classes>
  </properties>

  <build>
    <plugins>

      <plugin>
        <groupId>org.avaje.ebeanorm</groupId>
        <artifactId>avaje-ebeanorm-mavenenhancer</artifactId>
        <version>${avaje-ebeanorm-mavenenhancer.version}</version>
        <executions>
          <execution>
            <id>test</id>
            <phase>process-test-classes</phase>
            <configuration>
              <classSource>${avaje-ebeanorm-mavenenhancer.target-test-classes}</classSource>
              <transformArgs>${ebeanorm-enhancement.plugin.args}</transformArgs>
            </configuration>
            <goals>
              <goal>enhance</goal>
            </goals>
          </execution>
        </executions>
      </plugin>

    </plugins>

  </build>

```
