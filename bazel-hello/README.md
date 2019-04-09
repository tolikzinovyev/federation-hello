#  Bazel Federation Quick Start #

Make sure that [Bazel is installed](https://docs.bazel.build/versions/master/install.html)
on your system.


## Get federation-hello code onto your system

```bash
$git clone <this repo>
 cd <this repo>/bazel-hello

```

## Create you project's WORKSPACE

### Option 1 - Use provided WORKSPACE as an example

Nothing to do, you can [build and run the tests](#build-and-run-the-tests)

### Option 2 - Get the latest copy of the Federation WORKSPACE and save it as your project's WORKPACE
```bash
curl https://raw.githubusercontent.com/abseil/federation-head/master/WORKSPACE >> WORKSPACE
```
### Windows Note
The example above assumes that curl is already installed on your system.
* If you are on Windows 10, version 1803 or later, your OS ships with a copy of
curl, already set up and ready to use.
* If you have Git for Windows installed if you downloaded Git from git-scm.com
you have curl.exe under: C:\Program Files\Git\mingw64\bin\ - Simply add the
above path to PATH or call curl explicitly
```bash
"C:\Program Files\Git\mingw64\bin\curl" https://raw.githubusercontent.com/abseil/federation-head/master/WORKSPACE >> WORKSPACE
```
If you are not sure how to install curl on windows
[this StackOverflow](https://stackoverflow.com/questions/9507353/how-do-i-install-and-use-curl-on-windows) answer
might be helpful


## Build and run the tests

```bash
bazel test //...
```

## Build and run the example

```bash
 bazel run //:hello_main -- a_commandline_arg
```
