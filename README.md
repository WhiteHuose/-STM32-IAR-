# -STM32-IAR-
##  1.先学习如何编辑readme
----
#### 又名，论readme的重要性
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
#### 好了，至此妈妈再也不用担心看不懂我写的作业了，readme的学习先告一段落，进入正题。

---

## 2.开始创建IAR工程
----
* 第一步：创建工程文件夹<br>
工程文件夹下创建子文件夹<br>
  * COMSIS:<br>
  初始化堆栈指针；Cortex Microcontroller Software Interface Standard,此分组下的文件用来在启动时初始化向量表、配置系统时钟、定义片上外设寄存器等. <br>
  * APP:<br>
  用于用户外接的器件配置的函数定义的.h文件和.c文件.<br>
  * USER:<br>
  主函数及其它用户自编函数的.h或.c文件.<br>
  * DEVICE:<br>
  用于片上外设配置的函数的.h文件和.c文件.<br>
 
 
* 第二步：分析固件库文件<br>
根据芯片型号下载相应的官方固件库，解压后分析各个文件的作用。<br>
如:下载"STM32F0xx_StdPeriph_Lib_V1.5.0"。<br>
解压得到文件夹：<br>
  * "_htmresc"<br> 
  该文件夹下存放Logo文件。<br>
  * "Libraries"<br>
  该文件夹下是CMSIS库文件、STM32F0xx Standard Peripherals Firmware Library和STM32F0xx_CPAL_Driver.<br>
  * "Projects"<br>
  该文件夹下是一些工程模板和例程.<br>
  * "Utilities"<br>
  该文件夹下是ST公司评估板的应用Examples以及第三方支持工具补丁<br>
 * 第三步：根据芯片类型配置系统文件<br>
   * a.添加工程CMSIS文件.<br>
  打开stm32f0xx_stdperiph_lib_um.chm这个文件，查询STM32F0xx工程所需CMSIS文件，其中包括stm32f0xx.h，system_stm32f0xx.h，system_stm32f0xx.c和startup_stm32f072.s（以创建STM32F072工程为例）共四个文件，在库文件CMSIS文件夹下找到相应文件复制进工程文件的CMSIS文件夹下。<br>
   * b.添加工程USER文件.<br>
  在库文件的project文件夹下拷贝main.c、main.h、stm32f0xx_conf.h、stm32f0xx_it.c和stm32f0xx_it.h到User文件夹中。<br>
   * c.创建工程文件.<br>
  打开IAR，创建新的workspace，在该workspace下创建新的project，保存project和workspace于工程文件夹的根目录，在工程中添加group：CMSIS,DRIVER,APP,USER.在CMSISgroup中添加system_stm32f0xx.c和startup_stm32f072.s文件，在DRIVERgroup中添加工程文件夹->DEVICE->inc下的所有文件，在USERgroup中添加main.c和stm32f0xx_it.c文件。<br>
 * 第四步：设置工程选项.<br>
   * a.general options.<br>
  device选项选择我们所使用的芯片型号STM32F073CB，library configuration选项勾选USE CMSIS,设置完成点击OK以保存设置。<br>
   * b.c/c++ compiler.<br>
  preprocessor选项中添加文件路径，分别为工程文件的CMSIS,USER,APP\inc,DEVICE\inc，添加完成后再将绝对路径修改为相对路径。<br>
   * c.debugger.<br>
  setup选项driver选择为ST-LINK，download选项勾选USE FLASH LOADER.<br>
 * 第五步：修改系统文件。<br>
 将stm32f0xx.h文件中的如下代码行中的注释符去掉
 ```c
 #if !defined (STM32F030) && !defined (STM32F031) && !defined (STM32F051) && \
    !defined (STM32F072) && !defined (STM32F042) && !defined (STM32F091) && \
    !defined (STM32F070xB) && !defined (STM32F070x6) && !defined (STM32F030xC)
  /* #define STM32F030 */   
  /* #define STM32F031 */   
  /* #define STM32F051 */   
  /* #define STM32F072 *///找到我们需要的芯片型号，去掉注释符
  /* #define STM32F070xB */   
  /* #define STM32F042 */
  /* #define STM32F070x6 */   
  /* #define STM32F091 */
  /* #define STM32F030xC */  
#endif /* STM32F030 || STM32F031 || STM32F051 || STM32F072 || STM32F042 || STM32F091 ||
          STM32F070xB || STM32F070x6 || STM32F030xC */
 ```
 ```c
 /*#if !defined  USE_STDPERIPH_DRIVER*///还有这句
 ```
 ----
 至此，rebuild all，编译结果error：0，warning：0.这样我们的工程模板就创建完成了。<br>
 ### 在创建其他型号的芯片工程时基本步骤都大同小异，在遇到问题时可以根据错误提示耐心寻找解决办法哦.<br>
 <br><br>
希望能帮助到同在学习的你，转载请注明出处。
  

