<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /doc/mdsource/README.source.md
To change this file edit the source file and then execute ./run_markdown_templates.sh.
-->

<a id="top"></a>

# ApprovalTests.cpp User Guide

To get the most out of ApprovalTests, start with the  [Tutorial](/doc/Tutorial.md#top).
Once you're up and running, consider the following reference material. 

<!-- toc -->
## Contents

  * [Preparation](#preparation)
    * [Introduction](#introduction)
    * [Setup](#setup)
  * [Use](#use)
    * [Writing Tests](#writing-tests)
    * [Test Frameworks](#test-frameworks)
    * [Customising behaviour](#customising-behaviour)
    * [Common Challenges](#common-challenges)
    * [Common Scenarios](#common-scenarios)
  * [Miscellaneous](#miscellaneous)
    * [Extras](#extras)
    * [Advanced Topics](#advanced-topics)
    * [Suggested Examples](#suggested-examples)
<!-- endtoc -->


## Preparation

### Introduction

* [Overview](/doc/Overview.md#top)
* [Approval Testing (the concept)](/doc/ApprovalTestingConcept.md#top)
* What is Approval Testing?
* Why Approval Tests?
* [The Path to Approval Testing](/doc/PathToApprovalTesting.md#top)
* [Glossary](/doc/Glossary.md#top)

### Setup

There are three different places you might be starting your setup from.

Here's how to set up from:

* [I have nothing](/doc/Setup.md#i-have-nothing)
* [I have code but no tests](/doc/Setup.md#i-have-code-but-no-tests)
* [I have tests and code and want to add Approval Tests](/doc/Setup.md#i-have-tests-and-code-and-want-to-add-approval-tests)

## Use

### Writing Tests

* [Tutorial](/doc/Tutorial.md#top)
* [Testing single objects](/doc/TestingSingleObjects.md#top)
* [Testing containers](/doc/TestingContainers.md#top)
* [Testing exceptions](/doc/TestingExceptions.md#top)
* [Testing combinations](/doc/TestingCombinations.md#top) - containers of containers (of containers...)
* [To String](/doc/ToString.md#top)
* Worked example of getting to 'make the thing; verify the thing' - 'do; verify'
* [Features](/doc/Features.md#top) - recent additions

### Test Frameworks

* [Using Approval Tests With Catch](/doc/UsingCatch.md#top)
* [Using Approval Tests With Google Tests](/doc/UsingGoogleTests.md#top)
* [Using Approval Tests With Doctest](/doc/UsingDoctest.md#top)
* [Supporting a new test framework](/doc/SupportingNewTestFramework.md#top)

### Customising behaviour

* [Reporters](/doc/Reporters.md#top)
* [Custom Comparators](/doc/CustomComparators.md#top)
* [Writers](/doc/Writers.md#top)
* [Namers](/doc/Namers.md#top)
* [Configuration](/doc/Configuration.md#top)
* [All Customizations of Approval Tests](/doc/AllCustomizations.md#top)

### Common Challenges

* Unstable output, e.g. with Dates and Times
* Non-deterministic code
* [Multiple output files per test](/doc/MultipleOutputFilesPerTest.md#top)
* Testing images
* Embedded development

### Common Scenarios

* Non-graphical environments
* [Build Machines and Continuous Integration servers](/doc/BuildMachinesAndCI.md#top)


## Miscellaneous

### Extras

* [Frequently Asked Questions](/doc/FAQ.md#top)
* [Utilities](/doc/Utilities.md#top)
* [Videos](/doc/Videos.md#top)
* [Troubleshooting](/doc/Troubleshooting.md#top)
* 4 benefits of testing
    * Spec
    * Feedback
    * Regression
    * Granularity

### Advanced Topics

* [Contributing to ApprovalTests.cpp](/doc/Contributing.md#top)

### Suggested Examples
* [ApprovalTests](https://github.com/approvals/ApprovalTests.cpp/blob/master/tests/Catch2_Tests/ApprovalsTests.cpp)

