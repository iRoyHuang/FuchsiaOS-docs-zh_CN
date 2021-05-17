# Bootsvc

`bootsvc` is (typically) the first program loaded by usermode (contrast with
[userboot](userboot.md), which is loaded by the kernel).  `bootsvc` provides
several system services:
`bootsvc`是第一个在usermode下被加载的程序（usermode与userboot不同的是，userboot是内核加载的）。
`bootsvc`提供了几个系统服务：

- A filesystem service with the contents of the bootfs (/boot)
- A loader service that loads from that bootfs
- 一个带了bootfs内容的文件系统服务
- 一个从bootfs启动的启动服务

After preparing these services, it launches one program from the bootfs.  The
program may be selected with a [kernel command line argument](/docs/reference/kernel/kernel_cmdline.md)
`bootsvc.next` (this default to `bin/component_manager` currently).  The
launched program is provided with the bootfs mounted at `/boot` and the loader
service. `bootsvc.on_next_process_exit` controls whether bootsvc reboots or
shuts down the device when the process it starts exits.  The kernel command
line arguments are provided to it via `envp`.  See the documentation in
[//src/bringup/bin/bootsvc](/src/bringup/bin/bootsvc/) for more details.

当准备了这些服务之后，从bootfs启动一个程序。
这个程序可能带内核命令行参数（/docs/reference/kernel/kernel_cmdline.md）
`bootsvc.next`(当前默认为`bin/component_manager`)。这个启动的程序由挂载
在`/boot`的bootfs和加载器服务提供。`bootsvc.on_next_process_exit`控制了
当开始退出时，bootsvc是重启还是关闭设备。内核命令行参数通过运行`envp`获取。
更新信息见文档[//src/bringup/bin/bootsvc](/src/bringup/bin/bootsvc/) 。
