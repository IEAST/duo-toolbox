# duo-toolbox

[English] [中文](README_zh.md)

Simplify Duo SDK compilation for testing and debugging basic component updates.

## Quick Start

Initialize repository, download toolchain, and update submodules.

```bash
$ ./init.sh
```

Generate standalone rtos `fip.bin`.

```bash
$ cd debugloader
$ cd sbi && ./build.sh #Generate sbi.bin
```

Select the RTOS bin to be used and replace the rtos.bin in the directory.

```bash
$ cd duoRVOS
$ make #Generate os.bin
```

Copy `os.bin` and `sbi.bin` to the `fip` directory.

```bash
$ cd fip
$ cp ../debugloader/sbi/fw_bin/sbi.bin ./
$ cp ../debugloader/duoRVOS/os.bin ./
```

Export the path to the host tools.

```bash
$ export PATH=`pwd`/../host-tools/gcc/riscv64-linux-musl-x86_64/bin:$PATH
$ export PATH=`pwd`/../host-tools/gcc/riscv64-elf-x86_64/bin:$PATH
```

Generate `fip.bin`.

```sh
$ make fsbl-build
```