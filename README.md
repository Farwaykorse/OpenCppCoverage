<!-------------------------------------------------------------><a id="top"></a>
# Fork of OpenCppCoverage
<!----------------------------------------------------------------------------->
<!-- Badges -->
[![Build Status][Travis-badge]][Travis-link]
[![Build status][AppVeyor-badge]][AppVeyor-link]
[![codecov][Codecov-badge]][Codecov-link]
<!-- Description -->
Continuous integration on AppVeyor to generate a release without the installer,
to be used on CI platforms.

### Changes
- Build from frozen and latest versions of dependencies on vcpkg.
  - Frozen release is broken for the bzip2 download.
  - Protocol Buffer path has changed since dependencies where frozen.
- Project files expect a NuGet package.
  - Generating the NuGet file requires the vcpkg/packages directory,
    this causes considerable cache bloat.
  - Fake the .target-file and expected file-structure,
    to allow building without NuGet package.
- AppVeyor has a time limit of 60 minutes per job.
  Building the dependencies takes ~45 minutes, per platform configuration.
  To get around this the dependencies are build and updated in a separate job.
- Run the tests and report in the AppVeyor test overview.
- Generate coverage and upload to [codecov.io][Codecov-link].

### TODO
- Deploy Release build as zip on tag.
- Deploy Release build as zip on latest.
- Deploy NuGet package as zip on tag.
- Add option to only build vcpkg packages in Release configuration.
  - Debug only is broken, vcpkg 'post-build validation' errors.
- Run tests.
  - TestCoverageConsole.exe


<!----------------------------------------------------------------------------->
# OpenCppCoverage

OpenCppCoverage is an open source code coverage tool for C++ under Windows.

The main usage is for unit testing coverage, but you can also use it to know the executed lines in a program for debugging purpose.
## Features:
- **Visual Studio support**: Support compiler with program database file (.pdb).
- **Non intrusive**: Just run your program with OpenCppCoverage, no need to recompile your application.
- **HTML reporting**
- **Line coverage**.
- **Run as Visual Studio Plugin**: See [here](https://github.com/OpenCppCoverage/OpenCppCoveragePlugin) for more information.
- **Jenkins support**: See [here](https://github.com/OpenCppCoverage/OpenCppCoverage/wiki/Jenkins) for more information.
- **Support optimized build**.
- **Exclude a line based on a regular expression**.
- **Child processes coverage**.
- **Coverage aggregation**: Run several code coverages and merge them into a single report.
 
## Requirements
- Windows Vista or higher.
- Microsoft Visual Studio 2008 or higher all editions **including Express edition**. It should also work with previous version of Visual Studio.

## Download
OpenCppCoverage can be downloaded from [here](../../releases).

## Usage
You can simply run the following command:

```OpenCppCoverage.exe --sources MySourcePath -- YourProgram.exe arg1 arg2```

For example, *MySourcePath* can be *MyProject*, if your sources are located in *C:\Dev\MyProject*.

See [Getting Started](https://github.com/OpenCppCoverage/OpenCppCoverage/wiki) for more information about the usage.
You can also have a look at [Command-line reference](https://github.com/OpenCppCoverage/OpenCppCoverage/wiki/Command-line-reference).

<!----------------------------------------------------------------------------->
[top](#top)

[AppVeyor-badge]: https://ci.appveyor.com/api/projects/status/fuasqqstakl49tfb/branch/master?svg=true
[AppVeyor-link]:  https://ci.appveyor.com/project/Farwaykorse/opencppcoverage/branch/master
[Codecov-badge]:  https://codecov.io/gh/Farwaykorse/opencppcoverage/branch/master/graph/badge.svg
[Codecov-link]:   https://codecov.io/gh/Farwaykorse/opencppcoverage
[Travis-badge]:   https://travis-ci.com/Farwaykorse/opencppcoverage.svg?branch=master
[Travis-link]:    https://travis-ci.com/Farwaykorse/opencppcoverage/branches

