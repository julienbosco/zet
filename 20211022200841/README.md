#  Buildroot for building linux for embedded

See (https://buildroot.org)

Building a Docker image (julienbosco/buildroot) as building image.

## Optimization

### Building toolchain

See [section 6.1.3](https://buildroot.org/downloads/manual/manual.html#_cross_compilation_toolchain) for more details. Here is the config

* Architecture: aarch64
* Floating point

## Buildroot configuration

For now, using template for pine64

    make pine64_defconfig

Options:

* Enable ccache

## U-Boot

Trying to build version 2021.08, with pine64-lts_defconfig board.

## Other

(https://wiki.radxa.com/Rockpi4/dev/u-boot/pxe), same goal but with different board.
(https://ericdraken.com/embedded-linux/#bootloaders) worked on sopine.

    #pine64 #baremetal #pxe #uboot #buildroot #linux

