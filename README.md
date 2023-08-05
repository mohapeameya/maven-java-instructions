# maven-java-instructions
Maven instructions to create a simple Java project

# create a project with Maven

mvn archetype:generate -DgroupId="com.stripe.app" -DartifactId=StripeApp -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

# specify the encoding to make the project platform independent
<project>
  ...
  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <java.version>1.8</java.version>
    <guava.version>30.1.1-jre</guava.version>
    <junit.version>4.13.1</junit.version>
  </properties>
</project>

# add dependencies
<project>
  ...
  <dependencies>
    <dependency>
      <groupId>com.google.guava</groupId>
      <artifactId>guava</artifactId>
      <version>${guava.version}</version>
    </dependency>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>${junit.version}</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>

# build an executable jar
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <!-- Build an executable JAR -->
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-jar-plugin</artifactId>
        <version>3.3.0</version>
        <configuration>
          <archive>
            <manifest>
              <addClasspath>true</addClasspath>
              <classpathPrefix>lib/</classpathPrefix>
              <mainClass>com.stripe.app.App</mainClass>
            </manifest>
          </archive>
        </configuration>
      </plugin>
      <plugin>
          <groupId>org.apache.maven.plugins</groupId>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.0</version>
          <inherited>true</inherited>
          <configuration>
            <source>${java.version}</source>
            <target>${java.version}</target>
            <compilerArgument>-Xlint:unchecked</compilerArgument>
          </configuration>
        </plugin>
    </plugins>
  </build>
</project>

