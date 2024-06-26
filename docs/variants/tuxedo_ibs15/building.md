# Dasharo for Tuxedo IBS15 Gen6 - Building manual

## Intro

This documents describes the procedure for compiling coreboot for Tuxedo IBS15.

## Requirements

- Docker
    + follow [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
    + follow [Post-installation steps for Linux](https://docs.docker.com/engine/install/linux-postinstall/)
- Git

## Procedure

The easiest way to build coreboot is to use the official Docker image.

Obtain the image:

```bash
docker pull coreboot/coreboot-sdk:0ad5fbd48d
```

Obtain coreboot source code for Tuxedo IBS15:

```bash
git clone https://github.com/Dasharo/coreboot.git
```

Navigate to the source code directory and checkout to the desired revision:

> Replace the REVISION with one of the:
> - `tuxedo_ibs15/release` for the latest released version
> - `tuxedo_ibs15/vVERSION` (e.g. `v1.0.0`) for the given release

```bash
cd coreboot
git checkout REVISION
git submodule update --init --recursive --checkout
```

```bash
./build.sh build
```

The resulting coreboot image will be placed in
`artifacts/dasharo_tuxedo_ibs15_VERSION.rom`.

_Warning: Do not run `./build.sh` as root. This command uses docker and should
be executed as your current user. If you're having trouble running `build.sh`
on your user account, follow the `Docker` instructions outlined in
[Requirements](#requirements)._
