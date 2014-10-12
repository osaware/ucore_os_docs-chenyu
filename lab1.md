# 实验一：系统软件启动过程

ucore OS源码与机器码的语句和地址等的对应关系。


断门描述符的宏SETGATE（在练习6中会用到）

![段描述符结构](./lab1/image003.png "段描述符结构")

![段选择子结构](./lab1/image004.png "段选择子结构")

- DPL：描述符特权（Descriptor Privilege Level） 存储在段描述符中的权限位，用于描述对应段所属的特权等级，也就是段本身真正的特权级。





|  栈底方向		| 高位地址








```

<tr><td>trapasm.S</td><td>trap.c</td></tr>
<tr>
<td width="50%">
1)产生中断后，CPU 跳转到相应的中断处理入口 (vectors)，并在桟中压入相应的 error_code（是否存在与异常号相关） 以及 trap_no，然后跳转到 alltraps 函数入口：
<br>
注意：此处的跳转是 jmp 过程
<table>
<tr><td>(high)</td><td>...</td></tr>
</table>
<br>
在栈中保存当前被打断程序的 trapframe 结构(参见过程trapasm.S)。设置 kernel (内核) 的数据段寄存器，最后压入 esp，作为 trap 函数参数(struct trapframe * tf) 并跳转到中断处理函数 trap 处：
<table>
<tr>
<td width="50%">
Struct trapframe<br>
</td>
<td width="50%">
观察 trapframe 结构与中断产生过程的压桟顺序。<br>
</td></tr>
</table>
<br>
<br>
<br>
进入 trap 函数，对中断进行相应的处理：
</td>
<td></td>
</tr>
<td></td>
<td>
2)详细的中断分类以及处理流程如下：
<br>
</td>
<tr>
<td>
3)结束 trap 函数的执行后，通过 ret 指令返回到 alltraps 执行过程。
</td>
<td></td>
</tr>
<tr>
</tr>

![键盘控制器8042的逻辑结构图](./lab1/image012.png "键盘控制器8042的逻辑结构图")

<tr><td>bit</td><td>meaning</td></tr>