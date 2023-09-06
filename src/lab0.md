# First of All!

<video id="video" controls="" preload="none">
    <source id="mp4" src="./环境配置.mp4" type="video/mp4">
</video>


关于配置环境，我录了一个视频。我所使用的是UBUNTU22，具体设置如下
![0-0](./lab0-0.png)
# START
在上面的视频之中，可能有人发现了问题，下面这句话当你退出当前的shell之后会失效。因此你需要把这句话也设置为环境变量，比如写入.bashrc
```
export PATH=$PWD/riscv32-softmmu:$PWD/riscv64-softmmu:$PATH
```
START!
```
cd lab0
make
```
![0-1](./lab0-1.png)

then

```
make qemu
```

The shell should looks like:
![0-2](./lab0-2.png)

then , in another shell

```
make gdb
```

if :
```
riscv64-unknown-elf-gdb \
    -ex 'file bin/kernel' \
    -ex 'set arch riscv:rv64' \
    -ex 'target remote localhost:1234'
riscv64-unknown-elf-gdb: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory
make: *** [Makefile:177: gdb] Error 127

```

install it...

[ref](https://blog.csdn.net/qq_35078688/article/details/125326873)

if :

```
riscv64-unknown-elf-gdb \
    -ex 'file bin/kernel' \
    -ex 'set arch riscv:rv64' \
    -ex 'target remote localhost:1234'
riscv64-unknown-elf-gdb: error while loading shared libraries: libpython2.7.so.1.0: cannot open shared object file: No such file or directory
make: *** [Makefile:177: gdb] Error 127

```

install it...

[ref](https://stackoverflow.com/questions/26597527/how-to-install-libpython2-7-so)

then,make gdb again!

![lab0-3](./lab0-3.png)

FINISHI!

