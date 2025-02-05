<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /doc/mdsource/Reporters.source.md
To change this file edit the source file and then execute ./run_markdown_templates.sh.
-->

<a id="top"></a>

# Reporter


<!-- toc -->
## Contents

  * [Supported Diff Tools](#supported-diff-tools)
    * [Mac](#mac)
    * [Linux](#linux)
    * [Windows](#windows)
  * [Registering a default reporter](#registering-a-default-reporter)
  * [Front Loaded Reporters](#front-loaded-reporters)
    * [Blocking Reporters](#blocking-reporters)
  * [Miscellaneous Helper Reporters](#miscellaneous-helper-reporters)
    * [Auto-approving](#auto-approving)
<!-- endtoc -->



## Supported Diff Tools

The DiffReporter class goes through a chain of possible reporters to find the first option installed on your system.
Currently the search goes in this order:

### Mac

<!-- snippet: mac_diff_reporters -->
<a id='snippet-mac_diff_reporters'/></a>
```h
new BeyondCompareReporter(),
new DiffMergeReporter(),
new KaleidoscopeReporter(),
new P4MergeReporter(),
new KDiff3Reporter(),
new TkDiffReporter(),
new VisualStudioCodeReporter()
```
<sup>[snippet source](/ApprovalTests/reporters/MacReporters.h#L49-L57) / [anchor](#snippet-mac_diff_reporters)</sup>
<!-- endsnippet -->

### Linux

<!-- snippet: linux_diff_reporters -->
<a id='snippet-linux_diff_reporters'/></a>
```h
new MeldReporter(),
new KDiff3Reporter()
```
<sup>[snippet source](/ApprovalTests/reporters/LinuxReporters.h#L26-L29) / [anchor](#snippet-linux_diff_reporters)</sup>
<!-- endsnippet -->

### Windows

<!-- snippet: windows_diff_reporters -->
<a id='snippet-windows_diff_reporters'/></a>
```h
new TortoiseDiffReporter(),
new BeyondCompareReporter(),
new WinMergeReporter(),
new AraxisMergeReporter(),
new CodeCompareReporter(),
new KDiff3Reporter(),
new VisualStudioCodeReporter(),
```
<sup>[snippet source](/ApprovalTests/reporters/WindowsReporters.h#L72-L80) / [anchor](#snippet-windows_diff_reporters)</sup>
<!-- endsnippet -->

## Registering a default reporter

At present, the default Reporter is the DiffReporter. Whenever you call Approvals, you have the chance to pass in your own Reporter. However, if you would like to change what the default reporter is when you don't pass in a specific Reporter, you can do this at a global or per-test level, by adding the line:

<!-- snippet: use_as_default_reporter_in_main -->
<a id='snippet-use_as_default_reporter_in_main'/></a>
```cpp
// main.cpp:
#include <memory>
auto defaultReporterDisposer = Approvals::useAsDefaultReporter(std::make_shared<DiffReporter>() );
```
<sup>[snippet source](/tests/Catch2_Tests/main.cpp#L18-L22) / [anchor](#snippet-use_as_default_reporter_in_main)</sup>
<!-- endsnippet -->

The return value is ["Disposable"](/doc/DisposableObjects.md#top), meaning it will restore the original reporter when the object destructs. Because of this, if you do not store the result in a variable, it will immediately undo itself by the end of the line.

## Front Loaded Reporters

By default, Approval tests will not launch any reporters on supported CI machines. To do this, we use front loaded reporters...

Front loaded reporters allow you to block all normal reporting behaviour. This is useful in situations like running on a CI Machine, where you wouldn't want a reporter to open.

For more information, see [Build Machines and Continuous Integration servers](/doc/BuildMachinesAndCI.md#top).

Here is an example of not launching any reporters if you are on a machine with a particular name, by using [BlockingReporter](https://github.com/approvals/ApprovalTests.cpp/blob/master/ApprovalTests/reporters/BlockingReporter.h).

<!-- snippet: do_not_report_on_named_machine -->
<a id='snippet-do_not_report_on_named_machine'/></a>
```cpp
// main.cpp
auto frontLoadedReportDisposer = ApprovalTests::Approvals::useAsFrontLoadedReporter(
    ApprovalTests::BlockingReporter::onMachineNamed("MyCIMachineName") );
```
<sup>[snippet source](/examples/googletest_existing_main/main.cpp#L19-L23) / [anchor](#snippet-do_not_report_on_named_machine)</sup>
<!-- endsnippet -->

Once you have added that, even calling approvals with a specific Reporter will not launch it on the CI system (but will for all other systems). For example:

<!-- snippet: basic_approval_with_reporter -->
<a id='snippet-basic_approval_with_reporter'/></a>
```cpp
ApprovalTests::Approvals::verify("text to be verified", ApprovalTests::Windows::AraxisMergeReporter());
```
<sup>[snippet source](/examples/googletest_existing_main/GoogleTestApprovalsTests.cpp#L11-L13) / [anchor](#snippet-basic_approval_with_reporter)</sup>
<!-- endsnippet -->

### Blocking Reporters

Blocking reporters are a simple class, designed for use with FrontLoadedReporters, to prevent launching of reporters in certain environments.

<!-- snippet: do_not_report_on_named_machine -->
<a id='snippet-do_not_report_on_named_machine'/></a>
```cpp
// main.cpp
auto frontLoadedReportDisposer = ApprovalTests::Approvals::useAsFrontLoadedReporter(
    ApprovalTests::BlockingReporter::onMachineNamed("MyCIMachineName") );
```
<sup>[snippet source](/examples/googletest_existing_main/main.cpp#L19-L23) / [anchor](#snippet-do_not_report_on_named_machine)</sup>
<!-- endsnippet -->

## Miscellaneous Helper Reporters

While most reporters open some sort of external program, for the purpose of understanding how the tests went wrong, and verifying the correct answer, there are some reporters that are helpful for specific situations.

### Auto-approving

There are three reporters that can help with the approving of single or multiple tests.

* `AutoApproveIfMissingReporter`: if there is no approved file already, the received file will automatically be copied over the approved one. Otherwise, it does nothing. One possible cause for confusion here is if you ran the test previously with a standard reporter, that will have created an almost-empty approved file, which will then block this from working.
* `ClipboardReporter`: this puts the command-line to moved the approve file on to your computer's clipboard. You then review this, and paste it in to a terminal window. This only works with one test at a time.
* `AutoApproveReporter`: be careful, this will overwrite every existing ".approved" file, with no confirmation. This is best used when you are expecting large numbers of files that are already version-controlled to be updated, and you would rather review the changes in your version control system. 


---

[Back to User Guide](/doc/README.md#top)
