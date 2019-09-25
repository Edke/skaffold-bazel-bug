# skaffold-bazel-bug


## Bazel works

```
$ bazel run //:app-img
```

or 
```
$ bazel run //app:app-img
```

## Problem with skaffold and bazel as builder

```
$ skaffold dev
Listing files to watch...
 - project-dev1
 - project-dev2
WARN[0000] k8s/*.yaml did not match any file            
List generated in 285.616584ms
Generating tags...
 - project-dev1 -> project-dev1:e740f54
 - project-dev2 -> project-dev2:e740f54
Tags generated in 6.797319ms
Checking cache...
 - project-dev1: WARN[0000] error checking cache, caching may not work as expected: getting hash for artifact project-dev1: getting hash for main.py: lstat main.py: no such file or directory 
Error checking cache. Rebuilding.
 - project-dev2: Not found. Building
Cache check complete in 248.599108ms
Starting build...
Found [AdaptiDevOps] context, using local docker daemon.
Building [project-dev1]...
DEBUG: Rule 'rules_python' indicated that a canonical reproducible form can be obtained by modifying arguments shallow_since = "1569407463 +0200"
DEBUG: Call stack for the definition of repository 'rules_python' which is a git_repository (rule definition at /home/kraken/.cache/bazel/_bazel_kraken/0b40b3ac08131868d36aa913772c0bd4/external/bazel_tools/tools/build_defs/repo/git.bzl:195:18):
 - /home/kraken/sandbox/skaffold-bazel-bug/WORKSPACE:6:1
INFO: Build options --compilation_mode and --features have changed, discarding analysis cache.
INFO: Analyzed target //:app-img (0 packages loaded, 7011 targets configured).
INFO: Found 1 target...
Target //:app-img up-to-date:
  bazel-bin/app-img-layer.tar
INFO: Elapsed time: 1.607s, Critical Path: 0.99s
INFO: 4 processes: 4 linux-sandbox.
INFO: Build completed successfully, 5 total actions
FATA[0002] exiting dev mode because first build failed: build failed: build failed: building [project-dev1]: build artifact: loading image into docker daemon: reading from image load response: Error processing tar file(exit status 1): archive/tar: invalid tar header 

```
