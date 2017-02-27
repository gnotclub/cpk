# `cpk` spec

## Short description

`cpk` downloads a library and its dependencies in a folder and executes the libraries' build scripts
to build static libraries.

## Usage

`cpk` downloads the libraries by default in `./deps`. The path can
specified by the user, if needed.

A library is defined by a URL. Based on the protocol prefix (`http://`,
`git://`), it is downloaded as an arhive or as a git repository. If the URL
points to a git repository, the ref can be specified.

## Package format

Each library has a `.metadata` file with multiple `key="value"` lines in it.

```bash
NAME=
DESCRIPTION=
VERSION=
BUILD=
DEP=
DEP=
...
```

Each dependency has a `DEP=` line.

`BUILD` points to a script that builds a static library.
