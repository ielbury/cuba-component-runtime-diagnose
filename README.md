[![license](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg?style=flat)](http://www.apache.org/licenses/LICENSE-2.0)
[![Build Status](https://travis-ci.org/mariodavid/cuba-component-console.svg?branch=master)](https://travis-ci.org/mariodavid/cuba-component-console)

# CUBA Platform Component - Console

This application component is a Console for interactive runtime application management and debugging of a [CUBA](https://www.cuba-platform.com/) application.
CUBA-console is based on the idea of the [Grails console](http://plugins.grails.org/plugin/console).

It mainly consists of the three parts:

* interactive Groovy console
* interactive SQL console
* non-interactive diagnose wizard

## What is it about?
Sometimes it is necessary for debugging purposes of a CUBA application to be able to execute code that supports developer and customer support to get insights in the running application.

## Groovy console
The groovy console allows you to interactivly inspect the running application. You enter a groovy script and execute it in an ad-hoc fashion.

![Screenshot Groovy-Console](https://github.com/mariodavid/cuba-component-console/blob/master/img/groovy-console-screenshot.png)

> NOTE: Using the groovy console in production can be dangerous. Make sure that you will use the security subsystem properly so that only allowed users are able to execute code in production. For more information see the section about security

The console uses the [Scripting](https://doc.cuba-platform.com/manual-6.4/scripting.html) Interface of the platform in order to execute groovy code. Therefore most of the features of the scripting interface apply to the groovy console as well.

### Using existing classes

In order to use existing platform beans or your application specific beans, you can use `AppBeans.get()` to get a reference to abitrary Spring beans.

> NOTE: To reference classes by name you have to manually add the corresponding import statements at the top of the scripts

### Execution results

There are different results of a groovy script (displayed in the different tabs). The actual result of the script (meaning the return value of the last statement) is displayed in the first tab. The stacktrace tab displayes the stacktrace of a possible exception that occurs during script execution. The tab executed script shows the actual executed script.

#### Result log

Since `STDOUT` and `STDERR` will not captured through the runtime, `println 'hello world'` will not be included in any of the execution results. To make debug statements you can use the `log` variable which is passed into the script.

The possible methods are:

* `log.debug('debug information')`
* `log.warn('warnnings')`
* `log.error('error information')`

### Download of the execution results

Execution results can be downloaded through the corresponding button. It will create a zip file which will contain the different execution results in different files. Additionally, there is a file called `environmentInformation.log` which will include information about the current environment of execution (like information about the user that executed the script, information about the application itself etc.)

## SQL console
![Screenshot SQL-Console](https://github.com/mariodavid/cuba-component-console/blob/master/img/sql-console-screenshot.png)

## Dialog wizard
![Screenshot Diagnose Wizard](https://github.com/mariodavid/cuba-component-console/blob/master/img/diagnose-wizard-screenshot.png)
