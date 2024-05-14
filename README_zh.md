# duo-toolbox

[English](README.md)|中文版

简化 duo sdk 编译，用于测试基础组件更新调试

## Quick Start

仓库初始化,下载工具链和更新 submodule

```bash
$ ./init.sh
```

生成单独 rtos `fip.bin`

```bash
$ cd debugloader
$ cd sbi && ./build.sh #生成 sbi.bin
```

选择要使用的 rtos bin 替换目录下 rtos.bin

```bash
$ cd duoRVOS
$ make #生成 os.bin
```

将 os.bin sbi.bin 复制到 fip 目录下

```bash
$ cd fip
$ cp ../debugloader/sbi/fw_bin/sbi.bin ./
$ cp ../debugloader/duoRVOS/os.bin ./
```

export 相关 host-tools 路径，一般是

```bash
$ export PATH=`pwd`/../host-tools/gcc/riscv64-linux-musl-x86_64/bin:$PATH
$ export PATH=`pwd`/../host-tools/gcc/riscv64-elf-x86_64/bin:$PATH
```

生成 `fip.bin`

```sh
$ make fsbl-build
```
