
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
## Documentation


[1]: http://xseignard.github.io/2013/04/25/quality-analysis-on-node.js-projects-with-mocha-istanbul-and-sonar/
