#  Bazel Quick Start #

Make sure that [Bazel is installed](https://docs.bazel.build/versions/master/install.html)
on your system.

Get this code onto your system

```bash
$git clone <this repo>
 cd <this repo>/bazel-hello
 
```

Build and run the tests

```bash
bazel test //...
```

Build and run the example

```bash
 bazel run //:hello_main -- a_commandline_arg
```
