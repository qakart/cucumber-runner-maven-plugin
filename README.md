# cucumber-runner-maven-plugin

Maven plugin for running cucumber features in parallel using cucumber's Main class. To use it, add it to your pom file as a build plugin:

```xml
<build>
  <plugins>
    <plugin>
          <groupId>eu.evops.maven.plugins</groupId>
          <artifactId>cucumber-runner-maven-plugin</artifactId>
          <version>1.0</version>
     </plugin>
    </plugins>
  </build>
```

Then execute using following command:
```bash
mvn cucumber-runner:run
```

By default, this will run your feature files from src/test/resources in parallel using 1 process per available CPU core. On most modern computers this would be 8. You can control threading by specifying number of threads manual in the plugin configuration (threadCount parameter).

You can also specify other cucumber related configurations, a list of them is below:

| Parameter | Type | Description | Default value |
| --------- | ---- | ----------- | ------------- |
| outputFolder | ```File``` | Where all the output files are created | target/cucumber/threads |
| features | ```List<String>``` | List of locations to look for feature files, can use relative location and classpath: format | src/test/resources |
| includeTags | ```List<String>``` | List of tags to include, precede with @ symbol | none |
| excludeTags | ```List<String>``` | List of tags to exclude, precede with @ symbol, a common approach is to exclude @wip and possibly @manual | none |
| gluePaths | ```List<String>``` | List of glue paths to use, java packages that contain your step definitions and hooks | none |
| plugins | ```List<String>``` | List of plugins to use, reporters, formatters etc | none |
| scenarioNames | ```List<String>``` | List of scenario regular expressions for matching scenario names | none |
| dryRun | ```boolean``` | Do not actually run scenario, just run plugins | false |
| monochrome | ```boolean``` | Don't colour output | true |
| strict | ```boolean``` | When set to true, it will fail scenarios if undefined steps are found | true |
| threadCount | ```int``` | Number of process to start | Number of available CPU cores on the system |
