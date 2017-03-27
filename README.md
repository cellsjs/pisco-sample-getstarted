
# Piscosour Recipe pisco-sample-getstarted


Here we are going to show the first steps to create a very simple first recipe in pisco. In addtion, we will analyze the code with Sonarqube and we will see a lot of interesting data about the project: code issues, size, number of lines, complexity, code coverage, etc...
Let's get started
## First configuration
The first thing we have to do is to create our workspace for cells:
```
workspace::create
```

## Creating the project
In order to create the project, we follow the documentation of cells.
 - [Installation](https://bbva.cellsjs.com/guides/support/installation.html)
 - [Get started](https://github.com/cellsjs/piscosour/blob/feature/generate_docs/doc/get_started.md)

## Analyze project with Sonarqube
The documentation of this section has been extracted from [this website.][1]
The limitations of this section (for other projeccts):
> - It has to be a node.js project
> - You need an installation of Sonarqube in your computer.
> - You  need to have configured sonar-scanner in the path of yor computer.
> -  Include the SonarJS plugin in your Sonarqube installlation (latest versions of sonarqube already have this plugin).

If our tests are already OK, we can launch the command to generate the coverage report:
```
istanbul cover --report lcovonly --dir reports node_modules/.bin/_mocha -- -R  spec test/*.js
```
This instruction means that you are going to launch istanbul cover command with the following params:

- Report type: lcovonly
- Directory where the reports will be found: reports.
- node.js command to execute: ```node_modules/.bin/_mocha -- -R  spec test/*.js```

![Command line editor](/docs/images/istanbul-command-pisco-sample-getstarted-project.png)
Finally we ccan run the sonar-scanner command:
```
sonar-scanner -Dsonar.projectKey=pisco-sample-getstarted -Dsonar.sources=. -Dsonar.exclusions=**/node_modules/**,**/test/** -Dsonar.javascript.lcov.reportPaths=reports/lcov.info
```
Unfortunately, we can not get a coverage report becasuse we hace the tests written in a functional way (invoking node commands) other than invoking the Javascript API.
This is the command-line oputput:
```
INFO: Scanner configuration file: /home/albertoeyo/sngular/Middleware/sonar-scanner-2.9.0.670/conf/sonar-scanner.properties
INFO: Project root configuration file: NONE
INFO: SonarQube Scanner 2.9.0.670
INFO: Java 1.8.0_121 Oracle Corporation (64-bit)
INFO: Linux 4.8.0-36-generic amd64
INFO: User cache: /home/albertoeyo/.sonar/cache
INFO: Load global settings
INFO: Load global settings (done) | time=64ms
INFO: User cache: /home/albertoeyo/.sonar/cache
INFO: Load plugins index
INFO: Load plugins index (done) | time=4ms
INFO: SonarQube server 6.3.0
INFO: Default locale: "es_ES", source code encoding: "UTF-8" (analysis is platform dependent)
INFO: Process project properties
INFO: Load project repositories
INFO: Load project repositories (done) | time=79ms
INFO: Load quality profiles
INFO: Load quality profiles (done) | time=19ms
INFO: Load active rules
INFO: Load active rules (done) | time=570ms
INFO: Load metrics repository
INFO: Load metrics repository (done) | time=71ms
INFO: Publish mode
INFO: Project key: pisco-sample
INFO: -------------  Scan pisco-sample
INFO: Load server rules
INFO: Load server rules (done) | time=97ms
INFO: Initializer GenericCoverageSensor
INFO: Initializer GenericCoverageSensor (done) | time=0ms
INFO: Base dir: /home/albertoeyo/sngular/wk-cells/cells-workspace/pisco-sample
INFO: Working dir: /home/albertoeyo/sngular/wk-cells/cells-workspace/pisco-sample/.scannerwork
INFO: Source paths: .
INFO: Source encoding: UTF-8, default locale: es_ES
INFO: Index files
INFO: Excluded sources: 
INFO:   **/node_modules/**
INFO:   **/test/**
INFO: 15 files indexed
INFO: 3831 files ignored because of inclusion/exclusion patterns
INFO: Quality profile for js: Sonar way
INFO: Sensor NoSonar Sensor [php]
INFO: Sensor NoSonar Sensor [php] (done) | time=1ms
INFO: Sensor Coverage Report Import [csharp]
INFO: Sensor Coverage Report Import [csharp] (done) | time=0ms
INFO: Sensor Coverage Report Import [csharp]
INFO: Sensor Coverage Report Import [csharp] (done) | time=0ms
INFO: Sensor Unit Test Results Import [csharp]
INFO: Sensor Unit Test Results Import [csharp] (done) | time=0ms
INFO: Sensor XmlFileSensor [java]
INFO: 1 source files to be analyzed
INFO: 1/1 source files have been analyzed
INFO: Sensor XmlFileSensor [java] (done) | time=251ms
INFO: Sensor Analyzer for "php.ini" files [php]
INFO: Sensor Analyzer for "php.ini" files [php] (done) | time=6ms
INFO: Sensor JavaScript Squid Sensor [javascript]
INFO: 3 source files to be analyzed
INFO: 3/3 source files have been analyzed
INFO: Test Coverage Sensor is started
INFO: Sensor JavaScript Squid Sensor [javascript] (done) | time=425ms
INFO: Sensor Zero Coverage Sensor
INFO: Sensor Zero Coverage Sensor (done) | time=38ms
INFO: Sensor Code Colorizer Sensor
INFO: Sensor Code Colorizer Sensor (done) | time=1ms
INFO: Sensor CPD Block Indexer
INFO: org.sonar.scanner.cpd.deprecated.DefaultCpdBlockIndexer@63485d7 is used for js
INFO: Sensor CPD Block Indexer (done) | time=0ms
INFO: Calculating CPD for 1 files
INFO: CPD calculation finished
INFO: Analysis report generated in 101ms, dir size=23 KB
INFO: Analysis reports compressed in 12ms, zip size=10 KB
INFO: Analysis report uploaded in 32ms
INFO: ANALYSIS SUCCESSFUL, you can browse http://localhost:9000/dashboard/index/pisco-sample
INFO: Note that you will be able to access the updated dashboard once the server has processed the submitted analysis report
INFO: More about the report processing at http://localhost:9000/api/ce/task?id=AVsP55AbOTsm9I2yoYJR
INFO: Task total time: 4.941 s
INFO: ------------------------------------------------------------------------
INFO: EXECUTION SUCCESS
INFO: ------------------------------------------------------------------------
INFO: Total time: 6.093s
INFO: Final Memory: 47M/419M
INFO: ------------------------------------------------------------------------
```
If we go to the project main page we can see all the parameters sonarqube has analyzed:
![Sonar project main page](/docs/images/pisco-sample-getstarted-sonarqube-main-page.png)

[1]: http://xseignard.github.io/2013/04/25/quality-analysis-on-node.js-projects-with-mocha-istanbul-and-sonar/
