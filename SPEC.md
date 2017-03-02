# `cpk` spec

## Short description

`cpk` downloads a library and its dependencies in a folder. To maintain
simplicity and power, it is the user's job to do some trivial tasks, like
compiling the libraries.

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
```

`BUILD` points to a script that prepares the library, if needed.

If a library has dependencies, it needs a `.depends` file, where each line
contains a URL to a dependency.

```
git://github.com/gnotclub/hello-cpk
https://gnot.club/cpks/dlist.tar.gz
...
```

The `.depends` file is required for projects that use `cpk`. Although projects
themselves are not `cpk` libraries, `cpk` will read the `.depends` file and
install the libraries in the specified folder.
