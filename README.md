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
工程文件夹下创建子文件夹
* 第二步：确定芯片型号<br>
根据芯片型号下载相应的官方固件库，解压后分析各个文件的作用。<br>

