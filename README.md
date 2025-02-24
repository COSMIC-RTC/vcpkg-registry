# COSMIC VCPKG REPOSITORY

This repository contains the vcpkg portfiles for the Cosmic C/C++ compiler.

## Usage

To use the Cosmic vcpkg portfiles, you need to add it in your `vcpkg-configuration.json`. 

Example of a `vcpkg-configuration.json` file:

```json
{
    "default-registry": {
      "kind": "git",
      "baseline": "d5ec528843d29e3a52d745a64b469f810b2cedbf",
      "repository": "https://github.com/microsoft/vcpkg"
    },
    "registries": [
      {
        "kind": "git",
        "baseline": "6dd1b0ef94de7ae735f5cce61b6625d854a271e2",
        "repository": "https://github.com/COSMIC-RTC/vcpkg-registry",
        "packages": [ "pybind11" ]
      },
      {
        "kind": "artifact",
        "location": "https://github.com/microsoft/vcpkg-ce-catalog/archive/refs/heads/main.zip",
        "name": "microsoft"
      }
    ]
  }
  ```

## Create a new portfile

To create a new portfile, follow these steps:

1. Create a new directory for your portfile under the `ports` directory.
2. Add the necessary files for your portfile (e.g., `CONTROL`, `portfile.cmake`).
3. Add the new portfile to the registry..

For example:

```bash
mkdir -p ports/foo
touch ports/foo/CONTROL
touch ports/foo/portfile.cmake
git add ports/foo/.
git commit -m "Temporary commit"
vcpkg x-add-version --x-builtin-ports-root=./ports --x-builtin-registry-versions-dir=./versions foo
```

Then commit the new portfile to the registry.

```bash
git add .
git commit --amend -m 'Add foo portfile'
git push
```

## Update a portfiles

To update a portfile, follow these steps:

```bash
git add ports/foo/.
git commit -m "Temporary commit"
vcpkg x-add-version --x-builtin-ports-root=./ports --x-builtin-registry-versions-dir=./versions foo
```

Then commit the updated portfile to the registry.

```bash
git add .
git commit --amend -m 'Update foo portfile'
git push
```

## License

The Cosmic vcpkg portfiles are licensed under the [LGPL-3.0 license ](LICENSE).
