ветка lesson-29  подпроект service

поразбираемся с задачей test  (вызов gradle test)

https://docs.gradle.org/current/dsl/org.gradle.api.tasks.testing.Test.html

https://docs.gradle.org/current/userguide/jacoco_plugin.html#sec:jacoco_report_violation_rules

https://docs.gradle.org/current/userguide/checkstyle_plugin.html#sec:checkstyle_dependency_management

https://github.com/checkstyle/contribution/tree/master/xsl

по умолчанию задача jacocoTestReport не зависит никак от задачи test

plugins {
id 'java' // adds 'test' task
}

test {
// discover and execute JUnit4-based tests
useJUnit()

// discover and execute TestNG-based tests
useTestNG()

// discover and execute JUnit Platform-based tests
useJUnitPlatform()

// set a system property for the test JVM(s)
systemProperty 'some.prop', 'value'

// explicitly include or exclude tests
include 'org/foo/**'
exclude 'org/boo/**'

// show standard out and standard error of the test JVM(s) on the console
testLogging.showStandardStreams = true

// set heap size for the test JVM(s)
minHeapSize = "128m"
maxHeapSize = "512m"

// set JVM arguments for the test JVM(s)
jvmArgs '-XX:MaxPermSize=256m'

// listen to events in the test execution lifecycle
beforeTest { descriptor ->
logger.lifecycle("Running test: " + descriptor)
}

// fail the 'test' task on the first test failure
failFast = true

// skip an actual test execution
dryRun = true

// listen to standard out and standard error of the test JVM(s)
onOutput { descriptor, event ->
logger.lifecycle("Test: " + descriptor + " produced standard out/err: " + event.message )
}
}
