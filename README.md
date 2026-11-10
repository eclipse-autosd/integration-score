# AutoSD Eclipse S-CORE Integration

This template gives a basic structure to build project on top of Eclipse S-CORE with Bazel.

This repoitory's structure is inspired by the Eclipse S-CORE [reference integration repository](https://github.com/eclipse-score/reference_integration).

## Project Structure

* `bazel/`: common bazel module files included by `MODULE.bazel`
* `src/`: your project's source code!
* `images/`: rules to build an AutoSD Bootc image that can be applied in a VM or device that is running AutoSD
* `patches/`: several patch files to build some external modules (i.e s-core components)'
* `scripts/`: some utility scripts
* `.bazelrc`: a file that contains several pre-defined rules to build targets (such as toolchian registration)
* `.bazelversion`: a file that contains the recommended verison of Bazel to use, Bazelisk will use it by default

## Useful Bazel Commands

NOTE: Any `bazel` commands can also be replaced with [bazelisk](https://github.com/bazelbuild/bazelisk).

* `bazel mod deps --lockfile_mode=update`: update lockfile
* `bazel mod tidy`: the equivalent of `go mod tidy` for Bazel; it organizes/re-structures your Bazel files (MODULE, BUILD, .bzl, etc)
* `bazel clean --expunge`: clean all build cache

## Building

There are too build configs to build projects (as defined in `.bazelrc`):

* `autosd-x86_64`: native toolchain for `x86_64` builds
* `autosd-aarch64`: native toolchain for `aarch64` builds
* `autosd-crossland`: cross compilation of `aarch64` builds in a `x86_64` host machine

To build a target just run (`$config` being one of the above options):

```bash
$ bazel --config $config //src:hello
```

## License

[Apache-2](./LICENSE)
