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

## Update a portfiles

First, you need to verify that the portfiles are valid. 
```
vcpkg --x-builtin-ports-root=./ports --x-builtin-registry-versions-dir=./versions x-add-version --all --verbose
```

To update the portfiles, you need to clone this repository and then use the `--overlay-ports` option to vcpkg to specify the location of the portfiles. For example:

```
git add ports/foo/
git commit -m 'update foo'
git rev-parse HEAD:ports/foo
```

Then update the `foo` portfile (versions/foo.json) with the new commit hash.

```
git add .
git commit --amend -m 'update foo'
git push
```