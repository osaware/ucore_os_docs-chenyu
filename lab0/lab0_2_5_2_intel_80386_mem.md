
#### 2.5.2 Intel 80386内存架构

80386是32位的处理器，即可以寻址的物理内存地址空间为2^32=4G字节。在理解操作系统的过程中，需要用到三个地址空间的概念。地址是访问地址空间的索引。物理内存地址空间是处理器提交到总线上用于访问计算机系统中的内存和外设的最终地址。一个计算机系统中只有一个物理地址空间。线性地址空间是每个运行的应用程序看到的地址空间，在操作系统的虚存管理之下，每个运行的应用程序都认为自己独享整个计算机系统的地址空间，这样可让多个运行的应用程序之间相互隔离。处理器负责把线性地址转换成物理地址。一个计算机系统中可以有多个线性地址空间（比如一个运行的程序就可以有一个私有的线性地址空间）。线性地址空间的大小与物理地址空间的大小没有必然的连续。逻辑地址空间是应用程序直接使用的地址空间。这是由于80386中无法禁用段机制，使得逻辑地址一直存在。比如如下C代码片段：

	int boo=1;
	int *foo=&a;
 
这里的boo是一个整型变量，foo变量是一个指向boo地址的整型指针变量，foo中储存的内容就是boo的逻辑地址。逻辑地址由一个16位的段寄存器和一个32位的偏移量构成。Foo中放的就是32位的偏移量，而对应的段信息位于段寄存器中。

上述三种地址的关系如下：

- 分段机制启动、分页机制未启动：逻辑地址->段机制处理->线性地址=物理地址
- 分段机制和分页机制都启动：逻辑地址->段机制处理->线性地址->页机制处理->物理地址
