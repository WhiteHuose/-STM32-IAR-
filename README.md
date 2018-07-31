# -STM32-IAR-
##  1.先学习如何编辑readme
----
* 圆点<br>
*号加TAB加文本
  * 二级圆点<br>
  比上一级多一个TAB
    * 三级圆点<br>
    同上
* 图片<br>
![ ](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2375676017,2209238083&fm=27&gp=0.jpg "github logo")<br>
感叹号+中括号（中间要加一个空格）+括号（括号里加图片链接）
* 插入代码<br>
```C
int main(void)
{
  int num=520;
  return num;
}
```
## 2.开始创建IAR工程
----
* 第一步：创建工程文件夹<br>
工程文件夹下创建子文件夹<br>
  * COMSIS:<br>
  初始化堆栈指针；Cortex Microcontroller Software Interface Standard,此分组下的文件用来在启动时初始化向量表、配置系统时钟、定义片上外设寄存器等. <br>
  * HARDWARE:<br>
  用于用户外接的器件配置的函数定义的.h文件和.c文件.<br>
  * LIB:<br>
  STM32自带的片上外设的库函数.<br>
  * USER:<br>
  主函数及其它用户自编函数的.h或.c文件.<br>
  * DEVICE:<br>
  用于片上外设配置的函数的.h文件和.c文件.<br>
 
 
* 第二步：确定芯片型号<br>
根据芯片型号下载相应的官方固件库，解压后分析各个文件的作用。<br>
如:下载"STM32F0xx_StdPeriph_Lib_V1.5.0"。<br>
解压得到文件夹：<br>
  * "_htmresc"<br> 
  该文件夹下存放Logo文件。<br>
  * "Libraries"<br>
  * "Projects"<br>   
  * "Utilities".<br>

