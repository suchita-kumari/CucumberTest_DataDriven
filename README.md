selenium- cucumber-Test
=================

CucumberTest_DataDriven : Automation Testing Using Java and NgWebdriver

CucumberTest_DataDriven is a Data driven development (DD) approach to write automation test script to test Web application
It enables you to write and execute automated acceptance/unit tests.
It is cross-platform, open source and free.
Automate your test cases with minimal coding.
[More](https://cucumber.io/docs)

Locate element using NgWebdriver
[Here ](https://github.com/paul-hammant/ngWebDriver).

Testdata
----------------------------------

YAML file is used to store test data and passed as parameter to cucumber test [More details](https://learn.getgrav.org/advanced/yaml)


 

Documentation
-------------
* [Installation](doc/installation.md)
* [Predefined steps](doc/canned_steps.md)

Download a Framework
--------------
* Maven - https://github.com/suchita-kumari/CucumberTest_DataDriven

Writing a test
--------------

The cucumber features goes in the `features` library and should have the ".feature" extension.

You can start out by looking at `features/login.feature`. You can extend this feature or make your own features using some of the [predefined steps](doc/canned_steps.md) that comes with framework


Predefined steps
-----------------
By using predefined steps you can automate your test cases more quickly, more efficiently and without much coding.

The predefined steps are located [here](doc/canned_steps.md)

Running test
--------------

Go to your project directory from terminal and hit following commands
* `mvn test (default will run on local firefox browser)`
* `mvn test "-Dbrowser=chrome" (to use any other browser)`

Using canned tests in your project
----------------------------------

In your TestRunner class add a glue option: ExtendedCucumber runner has been used

The use of Extended Cucumber runner is similar to standard runner. Actually it is wrapper above the standard Cucumber runner object. [For more details](http://mkolisnyk.github.io/cucumber-reports/extended-cucumber-runner) 


```
package stepDefintions;
package stepDefintions;

import com.github.mkolisnyk.cucumber.runner.ExtendedCucumber;
import com.github.mkolisnyk.cucumber.runner.ExtendedCucumberOptions;
import com.github.mkolisnyk.cucumber.runner.ExtendedTestNGRunner;

import cucumber.api.CucumberOptions;

@ExtendedCucumberOptions(jsonReport = "Reports/cucumber.json",
        detailedReport = true,
        detailedAggregatedReport = true,
        overviewReport = true,
        coverageReport = true,
        jsonUsageReport = "Reports/cucumber-usage.json",
        usageReport = true,
        toPDF = true,
        excludeCoverageTags = {"@flaky" },
        includeCoverageTags = {"@passed" },
        outputFolder = "Reports")
@CucumberOptions(plugin = { "html:Reports/cucumber-html-report",
        "json:Reports/cucumber.json", "pretty:Reports/cucumber-pretty.txt",
        "usage:Reports/cucumber-usage.json", "junit:Reports/cucumber-results.xml" },
        features = { "./src/test/resources/features" },
        glue = { "info.seleniumcucumber.stepdefinitions" })

public  class RunSmokeTest extends ExtendedTestNGRunner {
}





```

Test Report
--------------
Overview report cucumber-results-feature-overview.html can be investigated further (generated under Reports). 
Overview section contains aggregated information on run status per features/scenarios/steps. It’s some kind of results summary.

Screenshot
--------------

Screenshot on failures captured and store under "Screenshots"



