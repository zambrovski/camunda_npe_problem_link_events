# camunda engine unit test template to reproduce a problem

This git repository contains a simple example of how to reproduce the problem in <a href="https://forum.camunda.org/t/npe-with-process-test-coverage-and-link-events/8441">"NPE with Process Test Coverage and Link Events"</a> in Camunda forum

The project contains the following files:

```
src/
└── test
    ├── java
    │   └── org
    │       └── camunda
    │           └── bpm
    │               └── unittest
    │                   └── SimpleTestCase.java   (1)
    └── resources
        ├── camunda.cfg.xml                       (2)
        └── testProcess.bpmn                      (3)
```
Explanation:

* (1) A java class containing a JUnit Test. It uses the `ProcessEngineRule` for bootstrapping the process engine, as well as [camunda-bpm-assert][assert] to make your test life easier.
* (2) Configuration file for the process engine with the ProcessCoverageInMemProcessEngineConfiguration.
* (3) The BPMN process with a link event.

## Running the test with maven

In order to run the testsuite with maven you can say:

```
mvn clean test
```

## Verifying that the problem lies in the test coverage

Simply edit the ```camunda.cfg.xml``` and use the StandaloneInMemProcessEngineConfiguration instead. The test runs fine then.

[assert]: https://github.com/camunda/camunda-bpm-assert
