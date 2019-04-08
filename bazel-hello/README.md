#  Bazel Quick Start #

Make sure that [Bazel is installed](https://docs.bazel.build/versions/master/install.html)
on your system.

Build and run the tests

```bash
bazel test //...
```

Build and run the example

```bash
 $git clone <this repo>
 cd <this repo>/bazel-hello
 bazel run //:hello_main -- a_commandline_arg
```
