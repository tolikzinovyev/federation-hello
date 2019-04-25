#  Bazel Federation Quick Start #

Make sure that [Bazel is installed](https://docs.bazel.build/versions/master/install.html)
on your system.


## Get federation-hello code onto your system

```bash
$git clone <this repo>
 cd <this repo>/bazel-hello

```

## Create or update your project's WORKSPACE
Ultimately your client project needs to reference Abseil Federation HEAD which in turn will make federation_deps() function call available. The federation_deps() is a convenient way to access a version of [federation_head.bzl](https://github.com/abseil/federation-head/blob/master/federation_deps.bzl) that your project depends upon.

So in your WORKSPACE first this definition is needed, to define "com_google_absl_oss_federation"
```
http_archive(
    name = "com_google_absl_oss_federation",
    strip_prefix = "federation-head-master",
    urls = ["https://github.com/abseil/federation-head/archive/master.zip"],
)
```
After com_google_absl_oss_federation has been defined we load 
```
load("@com_google_absl_oss_federation//:federation_deps.bzl", "federation_deps")
```
... And Call
```
federation_deps()
```

### Convenience script. We provide a script head_sync.py for convenience. 
This script should be run every time you want to sync with the latest avaialble Federation-Head:

* Make sure that python is installed and avaiable on your system
* Make sure that the following python modules are installed:
** hashlib
** json
** urllib3


### Run head_sync.py to get the latest head 
The script will run and output the latest state of the federation head
```bash
federation-hello (master)$ ./head_sync.py
...
...
********** INSERT THIS INTO YOUR WORKSPACE: *****************
http_archive(
  name = "com_google_absl_oss_federation",
  urls = ["https://github.com/abseil/federation-head/archive/f51f2c275b4b521ad4fa7f1c9143717bd264f400.zip"],  # 2019-04-09T17:26:54Z
  strip_prefix = "federation-head-f51f2c275b4b521ad4fa7f1c9143717bd264f400",
  sha256 = "9c51108ef9a4b5b6f48f2395d01f1785e5ce80a8816da9ca9e344f100cba62c4",
)
*********************************
```


## Step 2: Insert latest federation-head reference into your WORKSPACE
```bash

********** INSERT THIS INTO YOUR WORKSPACE: *****************
http_archive(
  name = "com_google_absl_oss_federation",
  urls = ["https://github.com/abseil/federation-head/archive/f51f2c275b4b521ad4fa7f1c9143717bd264f400.zip"],  # 2019-04-09T17:26:54Z
  strip_prefix = "federation-head-f51f2c275b4b521ad4fa7f1c9143717bd264f400",
  sha256 = "9c51108ef9a4b5b6f48f2395d01f1785e5ce80a8816da9ca9e344f100cba62c4",
)
*********************************
```


## Build and run the tests

```bash
bazel test //...
```

## Build and run the example

```bash
 bazel run //:hello_main -- a_commandline_arg
```
