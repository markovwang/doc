# 文件挂载

指的就是将设备文件中的顶级目录连接到 Linux 根目录下的某一目录（最好是空目录），访问此目录就等同于访问设备文件。

Linux 系统中“一切皆文件”，所有文件都放置在以根目录为树根的树形目录结构中。在 inux 看来，任何硬件设备也都是文件，它们各有自己的一套文件系统（文件目录结构）。

> 因此产生的问题是，当在 Linux 系统中使用这些硬件设备时，只有将Linux本身的文件目录与硬件设备的文件目录合二为一，硬件设备才能为我们所用。合二为一的过程称为“挂载”。

如果不挂载，通过Linux系统中的图形界面系统可以查看找到硬件设备，但命令行方式无法找到。

并不是根目录下任何一个目录都可以作为挂载点，由于挂载操作会使得原有目录中文件被隐藏，因此根目录以及系统原有目录都不要作为挂载点，会造成系统异常甚至崩溃，挂载点最好是新建的空目录。

##“挂载点”的目录要求：

- 目录事先存在，可以用mkdir命令新建目录
- 挂载点目录不可被其他进程使用到
- 挂载点下原有文件将被隐藏

##mount命令格式

```c++
//bash  mount [-t vfstype] [-o options] [设备名称] [挂载点]
int mount(const char *source, const char *target,
                 const char *filesystemtype, unsigned long mountflags,
                 const void *data);
/*
source: 文件系统所在设备名称（或网络文件系统的remote挂载点等）
target: 要挂载到的位置，一般是目录名。
filesystemtype: 文件系统名称。
mountflags: 文件系统通用挂载选项。
data: 文件系统特用挂载选项
*/
```
