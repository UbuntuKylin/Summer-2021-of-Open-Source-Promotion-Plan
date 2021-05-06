# Raspberry Pi automatic build tool for Ubuntu Kylin

English | [简体中文]

[简体中文]: ../zh_CN/优麒麟树莓派版本自动构建工具.md

## Origin Project

[Ubuntu Kylin for Raspberry Pi] is a custom distribution for Raspberry Pi. The [old project] was built using bash script, now it is moved to [docker]/[qemu] toolchain for automated installation.

[Ubuntu Kylin for Raspberry Pi]: https://github.com/UbuntuKylin/pi
[old project]: https://github.com/vhtq18w/ukarmimg
[docker]: https://www.docker.com
[qemu]: https://www.qemu.org

## Project Description

This project hopes to provide automated support for image building of Ubuntu Kylin for Raspberry Pi through docker/qemu toolchain.

  * Support all models after Raspberry Pi 3.
  * Enabling lower performance usage default settings for [ukui-kwin].
  * Target image support for build jobs on x86, aarch64.

[ukui-kwin]: https://github.com/ukui/ukui-kwin

## Technical Requirements

**Required**

  * docker
  * bash
  
**Optional**

  No

## Technical Keywords

**Docker**, **Raspberry Pi**

## Technical Details

The work on the final release build tool provided by this project is divided into the following main phases.

  * Build environment preparation
  * Pre-build kernel
  * Stage file system generation
  * Image export, partition and uboot setup
  * Integration testing
  
### Build environment

Depending on the host architecture, the build environment will need to explore whether qemu needs to be introduced separately for emulation of the Raspberry Pi, another thing is that docker use buildx provides built-in qemu support. If qemu is to be introduced separately, then aarch64 emulation on x86 and x86 emulation on aarch64 will need to be considered. In addition, the environment should also provide support for the most basic tools, such as `apt`, `dpkg`, `debootstrap`, etc.

### Pre-build Kernel

In particular, a pre-build kernel is not required for the final build image, it is a minimized kernel provided to verify that the release version works properly, and is mainly used to provide an initial contextual environment for integration testing.

### Stage File System

Once we have the build environment, we need to build a stage filesystem of Ubuntu Kylin for Raspberry Pi, which will be used to export the final image. This file system contains the full UKUI desktop environment, as well as some third-party software that we expect to integrate.

### Image Export

Exporting the image from the stage filesystem is straightforward, it is worth noting the design of the partition table writes, how uboot is preconfigured for general use, etc.

### Integration testing

Integration testing here is not integration testing in the usual sense, but rather testing of the UKUI desktop environment after it has been integrated with the Ubuntu Kylin default application. This step verifies that the build will work without dependent hardware.

## Features CheckList

  * [ ] Hardware Support
  
    | Hardware Model       | Support |
    |----------------------|---------|
    | Raspberry Pi 3B      | &#9744; |
    | Raspberry Pi 3B+     | &#9744; |
    | Raspberry Pi 4B(4GB) | &#9744; |
    | Raspberry Pi(8GB)    | &#9744; |

  * [ ] Architecture Support
  
    | Architecture | Support |
    |--------------|---------|
    | amd64        | &#9744; |
    | aarch64      | &#9744; |

  * [ ] Pre-build Kernel
  
    | Kernel Version | Support |
    |----------------|---------|
    | 5.4            | &#9744; |
    | 5.10           | &#9744; |

## Development Plan

The current implementation of the build tool is divided into several phases.

### Phase 1

One to two weeks to investigate whether the buildx provided by docker is suitable for cross-architecture emulation of Raspberry Pi.

### Phase 2

The build tool is implemented to generate the stage file system and export the build image from it. This build image should work on the real hardware.

### Phase 3

Make the build tool support pre-build of the kernel and verify that the resulting kernel can boot the image from the previous phase using docker or qemu.

## Contact

* Mentor: [Burgess Chang], [Mail to him].

[Burgess Chang]: https://github.com/brsvh
[Mail to him]: mailto:open@brsvh.org

## License

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License].

[Creative Commons Attribution-ShareAlike 4.0 International License]: http://creativecommons.org/licenses/by-sa/4.0/
