# COSMIC VCPKG REPOSITORY

This repository contains the vcpkg portfiles for the Cosmic C/C++ compiler.

## Usage

To use the Cosmic vcpkg portfiles, you need to clone this repository and then use the `--overlay-ports` option to vcpkg to specify the location of the portfiles. For example:

```
git clone
cd vcpkg
./bootstrap-vcpkg.sh
./vcpkg install --overlay-ports=<path-to-cosmic-vcpkg-repo>/ports <package-name>
```

## Add/Update a portfiles

To add/update the portfiles, you need to clone this repository and then use the `--overlay-ports` option to vcpkg to specify the location of the portfiles. For example:

```
git add ports/foo/.
git commit -m "Temporary commit"
vcpkg x-add-version --x-builtin-ports-root=./ports --x-builtin-registry-versions-dir=./versions foo
added version 1.0.0#1 to path/to/registry/versions/f-/foo.json
added version 1.0.0#1 to path/to/registry/versions/baseline.json
```

Then update the `foo` portfile (versions/foo.json) with the new commit hash.

```
git add .
git commit --amend -m 'Update foo to new version'
git push
```