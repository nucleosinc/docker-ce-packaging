# Building your own Docker deb package

`.deb` packages can be built from this directory with the following syntax

```shell
make ENGINE_DIR=/path/to/engine CLI_DIR=/path/to/cli deb
```

Artifacts will be located in `debbuild` under the following directory structure:
`debbuild/$distro-$distro_version/`

### NOTES:
* `ENGINE_DIR` -> Specifies the directory where the engine code is located, eg: `$GOPATH/src/github.com/docker/docker`
* `CLI_DIR` -> Specifies the directory where the cli code is located, eg: `$GOPATH/src/github.com/docker/cli`

## Specifying a specific distro

```shell
make ENGINE_DIR=/path/to/engine CLI_DIR=/path/to/cli ubuntu
```

## Specifying a specific distro version
```shell
make ENGINE_DIR=/path/to/engine CLI_DIR=/path/to/cli ubuntu-xenial
```

## Building the latest docker-ce

```shell
git clone https://github.com/docker/docker-ce.git
make ENGINE_DIR=docker-ce/components/engine CLI_DIR=docker-ce/components/cli deb
```

## Build a Specific Version 

```shell
git clone https://github.com/docker/docker-ce.git
cd docker-ce
git checkout v18.03.0-ce
cd ..
make ENGINE_DIR=$(pwd)/docker-ce/components/engine CLI_DIR=$(pwd)/docker-ce/components/cli VERSION=18.03.0-ce ubuntu-xenial
```

## 32-bit i686 Build

```shell
make ENGINE_DIR=$(pwd)/docker-ce/components/engine CLI_DIR=$(pwd)/docker-ce/components/cli ARCH=i686 VERSION=18.03.0-ce ubuntu-xenial
```
