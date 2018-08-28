# 一 概述

# Apache POI PPT - 概述

由 xicity 创建，youj 最后一次修改 2016-12-27

很多时候，需要一个软件应用程序来生成Microsoft Office文件格式的报告。 有时，应用程序甚至希望接收MS- Office文件作为输入数据。

任何希望生成MS Office文件作为输出的Java程序员都必须使用预定义和只读API来执行此操作。

## **什么是Apache POI？**

Apache POI是一个流行的API，允许程序员使用Java程序创建，修改和显示MS-Office文件。 它是由Apache Software Foundation开发和发布的一个开源库。 它包含用于解码用户输入数据或将文件转换为MS Office文档的类和方法。

## Apache POI的组件

Apache POI包含用于MS-Office的所有OLE2复合文档的类和方法。 此API的组件列表如下:

- **POIFS(可疑混淆执行文件系统)**:此组件是所有其他POI元素的基本因素。 它用于显式读取不同的文件。
- **HSSF(可怕的SpreadSheet格式)**:用于读取和写入.xls格式的MS-Excel文件。
- **XSSF(XML SpreadSheet格式)**:用于MS-Excel的.xlsx文件格式。
- **HPSF(可怕属性集格式)**:用于提取MS-Office文件的属性集。
- **HWPF(可怕字处理器格式)**:用于读取和写入MS-Word的扩展文件 **.doc** 。
- **XWPF(XML字处理器格式)**:用于读取和写入MS-Word的.docx扩展文件。
- **HSLF(可怕的幻灯片布局格式)**:用于阅读，创建和编辑PowerPoint演示文稿。
- **HDGF(Horrible DiaGram格式)**:它包含MS-Visio二进制文件的类和方法。
- **HPBF(Horrible PuBlisher格式)**:用于读取和写入MS-Publisher文件。

本教程将指导您完成使用Java进行Microsoft PowerPoint演示文稿的过程。 因此，讨论限于 **XSLF组件。**

**注意**:旧版本的POI支持二进制文件格式，如doc，xls，ppt等。版本3.5起，POI支持MS- Office的OOXML文件格式，如docx，xlsx，pptx等。

# 二 Java PPT API 接口

本章将介绍Java PowerPoint API及其功能的一些风格。 有许多供应商提供Java PPT相关的API; 本章提供了部分API介绍。

## Aspose Slides for Java

用于Java的Aspose幻灯片是一个纯许可的Java PPT API，由供应商 **Aspose** 开发和发布。 这个API的最新版本是8.1.2，于2014年7月发布。它是一个丰富而重的API(纯Java类和AWT类的组合)，用于设计可以读取，写入和管理幻灯片的PPT组件。

此API的常见用途如下:

- Build dynamic presentations
- Render and print high-fidelity presentations
- Generate, edit, convert, and print presentations

## Apache POI

Apache POI是Apache Software Foundation提供的一个100％开源库。 大多数中小型应用程序开发人员严重依赖Apache POI(HSLF + XSLF)。 它支持PPT库的所有基本功能; 然而，渲染和文本提取是其主要特征。 下面给出了用于PPT的Apache POI的架构。

# 三 Apache POI PPT - 安装

本章将介绍在基于Windows和Linux的系统上设置Apache POI的过程。 Apache POI可以轻松地安装并与您当前的Java环境集成，遵循几个简单的步骤，没有任何复杂的设置过程。 安装需要用户管理。

## 系统要求

 

| JDK          | Java SE 2 JDK 1.5或更高版本 |
| ------------ | --------------------------- |
| 内存         | 1 GB RAM(推荐)              |
| 磁盘空间     | 无最低要求                  |
| 操作系统版本 | Windows XP或以上版本，Linux |

现在让我们继续安装Apache POI的步骤。

## 步骤1:验证Java安装

首先，您需要在系统上安装Java软件开发工具包(SDK)。 请根据您正在处理的平台执行以下两个命令，验证是否安装成功。

如果Java安装已正确完成，那么它将显示Java安装的当前版本和规范。 下表给出了样本输出。

| 平台    | 命令                                             | 示例输出                                                     |
| ------- | ------------------------------------------------ | ------------------------------------------------------------ |
| Windows | 打开命令控制台并键入:<br /> **//>java -version** | Java版本“1.7.0_60" <br /> Java TM SE运行时间 <br /> 环境(build 1.7.0_60-b19) <br /> Java Hotspot(TM)64位服务器 <br /> VM(构建24.60-b09，混合模式) |
| Linux   | 打开命令终端并键入: <br /> **$java -version**    | java版本“1.7.0_25" <br /> 打开JDK运行时环境(rhel-2.3.10.4.el6_4-x86_64) <br /> 打开JDK 64位服务器虚拟机(构建23.7-b01，混合模式) |

- 我们假设本教程的读者在他们的系统上安装了Java SDK 1.7.0_60版本。
- 如果您没有Java SDK，请从<http://www.oracle.com/technetwork/java/javase/downloads/index.html>并安装它。

## 步骤2:设置Java环境

将环境变量JAVA_HOME设置为指向计算机上安装Java的基本目录位置。 例如，

| 平台    | 描述                                               |
| ------- | -------------------------------------------------- |
| Windows | 将JAVA_HOME设置为 C:\ProgramFiles\java\jdk1.7.0_60 |
| linux   | 导出JAVA_HOME = /usr/local/java-current            |

将Java编译器位置的完整路径附加到系统路径。 

| 描述    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| Windows | 将字符串“C:\Program Files\Java\jdk1.7.0_60\bin"附加到系统变量PATH的结尾。 |
| Linux   | 导出PATH = $ PATH:$ JAVA_HOME / bin /                        |

如上所述，从命令提示符处执行命令 **java -version** 。 

## 步骤3:安装Apache POI库

从 [http://poi.apache.org/download](http://poi.apache.org/download.html) 下载最新版本的Apache POI。 html ，并将其内容解压缩到一个文件夹，从中可以将所需的库链接到Java程序。 让我们假设文件收集在C驱动器上的文件夹中。

以下图像显示已下载文件夹中的目录和文件结构:

![](1482806916810739.jpg)

![](1482806926469282.jpg)

将上述图片中突出显示的五个 **jars** 的完整路径添加到CLASSPATH。  

| 描述    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| Windows | 将以下字符串附加到用户变量CLASSPATH的结尾: <br /> “C:\poi-3.9\poi-3.9-20121203.jar;" <br /> “C:\poi-3.9\poi-ooxml-3.9-20121203.jar;" <br /> “C:\poi-3.9\poi-ooxml-schemas-3.9-20121203.jar;" <br /> “C:\poi-3.9\ooxml-lib\dom4j-1.6.1.jar;" <br /> “C:\poi-3.9\ooxml-lib\xmlbeans-2.3.0.jar;.;" |
| Linux   | 导出CLASSPATH = $ CLASSPATH: <br /> /usr/share/poi-3.9/poi-3.9-20121203.tar: <br />/usr/share/poi-3.9/poi-ooxml-schemas-3.9-20121203.tar:<br>/usr/share/poi-3.9/poi-ooxml-3.9-20121203.tar:<br>/usr/share/poi-3.9/ooxml-lib/dom4j-1.6.1.tar:<br>/usr/share/poi-3.9/ooxml-lib/xmlbeans-2.3.0.tar |

# 四 Apache POI PPT - 类和方法

在本章中，我们将了解Apache POI API下的几个类和方法，这些对于使用Java程序处理PPT文件至关重要。

## 介绍

要创建和管理演示文稿，您在包 *org.apache.poi.xslf.usermodel* 中有一个名为XMLSlideShow的类。 下面给出了一些重要的方法和这个类的构造函数。

**类**:XMLSlideShow

**包**:org.apache.poi.xslf.usermodel

| S.No | 构造函数和说明                                               |
| ---- | ------------------------------------------------------------ |
| 1    | **XMLSlideShow(java.io.InputStream inputStream)**<br /> 你可以通过传递一个inputstream类对象来实例化这个类。 |

| S.No | 方法和描述                                                   |
| :--- | ------------------------------------------------------------ |
| 1    | **int addPicture(byte [] pictureData，int format)** <br /> 使用此方法，您可以向演示文稿添加图片。 |
| 2    | **XSLFSlide createSlide()** <br /> 在演示文稿中创建空白幻灯片。 |
| 3    | **XSLFSlide createSlide(XSLFSlideLayout布局)** <br /> 创建具有给定幻灯片布局的幻灯片。 |
| 4    | **java.util.List< XSLFPictureData>** getAllPictures() <br /> 返回一个演示文稿中所有图片的数组。 |
| 5    | **java.awt.Dimension getPageSize()** <br /> 使用此方法，您可以了解当前页面大小。 |
| 6    | **XSLFSlideMaster [] getSlideMasters()** <br /> 返回演示文稿中所有幻灯片的数组。 |
| 7    | **XSLFSlide [] getSlides()** <br /> 返回演示文稿中的所有幻灯片。 |
| 8    | **XslFSlide removeSlide(int index)** <br /> 使用此方法，您可以从演示文稿中删除幻灯片。 |
| 9    | **void setPageSize(java.awt.Dimension pgSize)** <br /> 使用此方法，您可以重置页面大小。 |
| 10   | **void setSlideOrder(XSLFSlide slide，int newIndex)** <br /> 使用此方法，您可以重新排序幻灯片。 |

## 滑动

要在演示文稿中创建和管理幻灯片，请使用 **XSLFSlide** 类的方法。 这一类的一些重要方法如下所述。

**类**:XSLFSlide

**套件**:org.apache.poi.xslf.usermodel

 

| S.No | 描述                                                         |
| ---- | ------------------------------------------------------------ |
| 1    | **XSLFBackground getBackground()** <br /> 返回幻灯片母版的常用背景。 |
| 2    | **XSLFSlideLayout getLayout(SlideLayout type)** <br /> 返回XSLFSlideLayout对象。 |
| 3    | **XSLFSlideLayout [] getSlideLayouts()** <br /> 返回此幻灯片母版中的所有幻灯片布局。 |

## 幻灯片布局

POI库有一个名为 **XSLFSlideLayout** 的类，您可以使用它来管理幻灯片的布局。

**类**:XSLFSlideLayout

**套件**:org.apache.poi.xslf.usermodel

| 描述 | 方法和说明                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **void copyLayout(XSLFSlide幻灯片)** <br /> 此方法会将占位符从此布局复制到给定幻灯片。 |

## 文本段落

您可以使用 **XSLFTextParagraph** 类别将内容写入幻灯片。 下面提到这个类的一些重要方法。

**类**:XSLFTextParagraph

**套件**:org.apache.poi.xslf.usermodel

| S.No | 方法和描述                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **XSLFTextRun addLineBreak()** <br /> 在段落中插入换行符。   |
| 2    | **XSLFTextRun addNewTextRun()** <br /> 在段落中添加新的文本行。 |
| 3    | **void setBulletAutoNumber(ListAutoNumber scheme，int startAt)** <br />  将自动编号的项目符号点应用于段落。 |
| 4    | **void setIndent(double value)** <br /> 将缩进设置为段落中的文本。 |
| 5    | **void setLeftMargin(double value)** <br /> 此方法用于添加段落的左边距。 |
| 6    | **void setLineSpacing(double line spacing)** <br /> 此方法用于在段落中设置行间距。 |
| 7    | **void setTextAlign(TextAlign align)** <br /> 此方法用于设置要设置为段落的对齐方式。 |

## 文本运行

这是文本正文中文本分隔的最低级别。 您可以使用 **XSLFTextRun** 类来管理段落的文本运行。 下面提到这个类的一些重要方法。

**类**:XSLFTextParagraph

**套件**:org.apache.poi.xslf.usermodel

| S.No | 方法和描述                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **XSLFHyperlink createHyperlink()** <br /> 在演示文稿中创建超链接。 |
| 2    | **XSLFHyperlink getHyperlink()** <br /> 此方法用于获取超链接。 |
| 3    | **java.lang.String getText()** <br /> 以Java字符串形式返回此Text节点的值。 |
| 4    | **void setBold(boolean bold)** <br /> 此方法用于以粗体设置文本。 |
| 5    | **void setCharacterSpacing(double spc)** <br /> 设置文本运行中的字符之间的间距。 |
| 6    | **void setFontColor(java.awt.Color color)** <br /> 设置文本的字体颜色。 |
| 7    | **void setFontSize(double fontSize)** <br /> 设置文本的字体大小。 |
| 8    | **void setItalic(boolean italic)** <br /> 这个方法用于使段落斜体。 |
| 9    | **void setStrikethrough(boolean strike)** <br /> 此方法用于将一段文本格式化为删除线文本。 |
| 10   | **void setSubscript(boolean flag)** <br /> 此方法用于将文本格式化为下标。 |
| 11   | **void setSuperscript(boolean flag)** <br /> 此方法用于将此运行中的文本格式化为上标。 |
| 12   | **void setText(java.lang.String text)** <br /> 此方法用于在运行中设置文本。 |
| 13   | **void setUnderline(Boolean underline)** <br /> 此方法用于在文本运行中对文本加下划线。 |

## 文本形状

在PPT中，我们有可以在其中保存文本的形状。 我们可以使用 **XSLFTextShape** 类来管理这些。 下面提到这个类的一些重要方法。

**类**:XSLFTextShape

**套件**:org.apache.poi.xslf.usermodel

| S.No | 方法和描述                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **void setPlaceholder(Placeholder placeholder)** <br /> 使用此方法，您可以选择占位符。 |
| 2    | **Placeholder getTextType()** <br /> 返回当前占位符的类型。  |
| 3    | **void clearText()** <br /> 清除当前文本形状的文本区域。     |
| 4    | **XSLFTextParagraph addNewTextParagraph()** <br /> 向形状添加新的段落运行。 |
| 5    | **void drawContent(java.awt.Graphics2D graphics)** <br /> 此方法允许您在幻灯片上绘制任何内容。 |

## 超链接

POI库具有一个名为 **XSLFHyperlink** 的类，您可以使用它在演示文稿中创建一个超链接。 下面提到这个类的一些重要方法。

**类**:XSLFHyperlink

**套件**:org.apache.poi.xslf.usermodel

 

| S.No | 方法和描述                                                   |
| ---- | ------------------------------------------------------------ |
| 1    | **java.net.URI getTargetURL()** <br /> 返回演示文稿幻灯片中存在的网址。 |
| 2    | **void setAddress(java.lang.String address)** <br /> 此方法用于将地址设置为URL。 |
| 3    | **void setAddress(XSLFSlide幻灯片)** <br /> 将地址设置为演示文稿幻灯片中显示的网址。 |

# 五 Apache POI PPT - 演示

一般来说，我们使用MS-PowerPoint来创建演示文稿。 现在让我们看看如何使用Java创建演示文稿。 完成本章后，您将能够创建新的MS-PowerPoint演示文稿，并使用您的Java程序打开现有的PPT。

## 创建空的演示文稿

要创建空的演示文稿，您必须实例化 **org.poi.xslf.usermodel 包的 XMLSlideShow 类:**

```java
XMLSlideShow ppt = new XMLSlideShow();
```

使用 **FileOutputStream** 类将更改保存到PPT文档: 

```java
File file=new File("C://POIPPT//Examples//example1.pptx");
FileOutputStream out = new FileOutputStream(file);
ppt.write(out);
```

以下是创建空白MS-PowerPoint演示文稿的完整程序。 

```java
import java.io.FileOutputStream;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlide;

public class CreatePresentation {
   
   public static void main(String args[]) throws IOException{
   
      //creating a new empty slide show
      XMLSlideShow ppt = new XMLSlideShow();	     
      
      //creating an FileOutputStream object
      File file =new File("example1.pptx");
      FileOutputStream out = new FileOutputStream(file);
      
      //saving the changes to a file
      ppt.write(out);
      System.out.println("Presentation created successfully");
      out.close()
   }
}
```

将上面的Java代码保存为 **CreatePresentation.java** ，然后从命令提示符处编译并执行它，如下所示: 

```dockerfile
$javac CreatePresentation.java
$java CreatePresentation
```

如果您的系统环境配置有POI库，它将编译并执行，以在当前目录中生成名为 **example1.pptx** 的空白PPT文件，并在命令提示符下显示以下输出: 

```dockerfile
Presentation created successfully
```

空白PowerPoint文档显示如下: 

![](1482809595463893.jpg)

## 编辑现有演示文稿

要打开现有的演示文稿，请实例化 **XMLSlideShow** 类，并将要编辑的文件的 **FileInputStream** 对象作为 **XMLSlideShow** 构造函数的参数传递 。

```java
File file=new File(“C://POIPPT//Examples//example1.pptx");
FileInputstream inputstream =new FileInputStream(file);
XMLSlideShow ppt = new XMLSlideShow(inputstream);
```

您可以使用 **org.poi.xslf.usermodel 包中的XMLSlideShow类的 createSlide()方法将幻灯片添加到演示文稿。** 

```java
XSLFSlide slide1= ppt.createSlide();
```

下面给出了打开和添加幻灯片到现有PPT的完整程序: 

```java
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlide;

public class EditPresentation {

   public static void main(String ar[]) throws IOException{
	   
      //opening an existing slide show
      File file = new File("example1.pptx");
      FileInputStream inputstream=new FileInputStream(file);
      XMLSlideShow ppt = new XMLSlideShow(inputstream);
      
      //adding slides to the slodeshow
      XSLFSlide slide1 = ppt.createSlide();
      XSLFSlide slide2 = ppt.createSlide();
      
      //saving the changes 
      FileOutputStream out = new FileOutputStream(file);
      ppt.write(out);
      
      System.out.println("Presentation edited successfully");
      out.close();	
   }
} 
```

将上述Java代码另存为 **EditPresentation.java** ，然后从命令提示符处编译并执行，如下所示: 

```dockerfile
$javac EditPresentation.java
$java EditPresentation
```

它将编译并执行以生成以下输出: 

```dockerfile
slides successfully added
```

带有新添加的幻灯片的输出PPT文档如下所示: 

![](1482809608439971.jpg)

将幻灯片添加到PPT后，您可以在幻灯片上添加，执行，读取和写入操作。 

# 六 Apache POI PPT - 幻灯片布局

在上一章中，您已经了解了如何创建空白幻灯片以及如何向其添加幻灯片。 在本章中，您将学习如何获取可用幻灯片的列表，以及如何创建具有不同布局的幻灯片。

## 可用的幻灯片布局

PowerPoint演示文稿具有幻灯片布局，您可以选择所需的布局来编辑幻灯片。 首先，让我们找出所有可用的幻灯片布局的列表。

- 有不同的幻灯片母版，在每个幻灯片母版中，有几个幻灯片布局。
- 您可以使用 **XMLSlideShow** 类的 **getSlideMasters()**方法获取幻灯片主题列表。
- 您可以使用 **XSLFSlideMaster** 类的 **getSlideLayouts()**方法从每个幻灯片母带获取幻灯片布局的列表。
- 您可以使用 **XSLFSlideLayout** 类的 **getType()**方法从布局对象获取幻灯片布局的名称。

**注意**:所有这些类都属于 *org.poi.xslf.usermodel* 包。

下面给出的是获取PPT中可用幻灯片布局列表的完整程序:

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlideLayout;
import org.apache.poi.xslf.usermodel.XSLFSlideMaster;

public class SlideLayouts {

   public static void main(String args[]) throws IOException{
   
      //create an empty presentation
      XMLSlideShow ppt = new XMLSlideShow();
      System.out.println("Available slide layouts:")
   
      //getting the list of all slide masters
      for(XSLFSlideMaster master : ppt.getSlideMasters()){
   
         //getting the list of the layouts in each slide master
         for(XSLFSlideLayout layout : master.getSlideLayouts()){
   
            //getting the list of available slides
            System.out.println(layout.getType());
         } 
      }
   }
}
```

将上述Java代码保存为 **SlideLayouts.java** ，然后从命令提示符处编译并执行，如下所示: 

```dockerfile
$javac SlideLayouts.java
$java SlideLayouts
```

它将编译并执行以生成以下输出: 

```dockerfile
Available slide layouts:
TITLE
PIC_TX
VERT_TX
TWO_TX_TWO_OBJ
BLANK
VERT_TITLE_AND_TX
TITLE_AND_CONTENT
TITLE_ONLY
SECTION_HEADER
TWO_OBJ
OBJ_TX
```

下面显示的是MS-Office 360，2013版本提供的一些示例幻灯片布局。 

![](1482819512194362.jpg)

## 标题布局

让我们使用标题布局在PPT中创建幻灯片。 请按照以下步骤操作:

**步骤1** :通过实例化 **XMLSlideShow** 类创建一个空的演示文稿，如下所示:

```java
XMLSlideShow ppt = new XMLSlideShow();
```

**步骤2** :使用 **getSlideMasters()**方法获取幻灯片主题列表。 此后，使用索引选择所需的幻灯片母带，如下所示: 

```java
XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
```

这里我们得到的默认幻灯片母版是在幻灯片主数据的第0位置。

**步骤3** :使用 **XSLFSlideMaster** 类的 **getLayout()**方法获取所需的布局。 此方法接受一个参数，您必须传递 **SlideLayoutclass** 的静态变量之一，代表我们所需的布局。 这个类中有几个变量，每个变量代表一个幻灯片布局。

下面的代码片段显示了如何创建标题布局:

```java
XSLFSlideLayout titleLayout = slideMaster.getLayout(SlideLayout.TITLE);
```

**步骤4** :通过将幻灯片布局对象作为参数传递来创建新幻灯片。 

```java
XSLFSlide slide = ppt.createSlide(titleLayout);
```

**第5步**:使用 **XSLFSlide** 类的 **getPlaceholder()**方法选择占位符。 此方法接受整数参数。 通过传递0到它，你会得到 **XSLFTextShape** 对象，使用它可以访问幻灯片的标题文本区域。 使用setText()方法设置标题，如下所示: 

```java
XSLFTextShape title1 = slide.getPlaceholder(0);
//setting the title init
title1.setText("Tutorials point");
```

下面给出的是在演示文稿中创建带有标题布局的幻灯片的完整程序: 

```java
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.SlideLayout;
import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlide;
import org.apache.poi.xslf.usermodel.XSLFSlideLayout;
import org.apache.poi.xslf.usermodel.XSLFSlideMaster;
import org.apache.poi.xslf.usermodel.XSLFTextShape;

public class TitleLayout {

   public static void main(String args[]) throws IOException{
   
      //creating presentation
      XMLSlideShow ppt = new XMLSlideShow();	    	
      
      //getting the slide master object
      XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
      
      //get the desired slide layout 
      XSLFSlideLayout titleLayout = slideMaster.getLayout(SlideLayout.TITLE);
                                                     
      //creating a slide with title layout
      XSLFSlide slide1 = ppt.createSlide(titleLayout);
      
      //selecting the place holder in it 
      XSLFTextShape title1 = slide1.getPlaceholder(0); 
      
      //setting the title init 
      title1.setText("Tutorials point");
      
      //create a file object
      File file=new File("C://POIPPT//Examples//Titlelayout.pptx");
      FileOutputStream out = new FileOutputStream(file);
      
      //save the changes in a PPt document
      ppt.write(out);
      System.out.println("slide cretated successfully");
      out.close();  
   }
}
```

带有新添加的标题布局幻灯片的PPT文档如下所示: 

![](1482819541953509.jpg)

## 标题和内容布局

让我们使用标题和内容布局在PPT中创建幻灯片。 按照下面给出的步骤。

**步骤1** :通过实例化 **XMLSlideShow** 类创建一个空的演示文稿，如下所示:

```java
XMLSlideShow ppt = new XMLSlideShow();
```

**步骤2** :使用 **getSlideMasters()**方法获取幻灯片主题列表。 此后，使用索引选择所需的幻灯片母带，如下所示: 

```java
XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
```

这里我们得到的默认幻灯片母版是在幻灯片主数据的第0位置。

**步骤3** :使用 **XSLFSlideMaster** 类的 **getLayout()**方法获取所需的布局。 此方法接受一个参数，您必须传递 **SlideLayoutclass** 的静态变量之一，代表我们所需的布局。 这个类中有几个变量，每个变量代表一个幻灯片布局。

下面的代码片段显示了如何创建标题布局:

```java
XSLFSlideLayout titleLayout = slideMaster.getLayout(SlideLayout.TITLE);
```

**步骤4** :通过将幻灯片布局对象作为参数传递来创建新幻灯片。

```java
XSLFSlide slide = ppt.createSlide(titleLayout);
```

**第5步**:使用 **XSLFSlide** 类的 **getPlaceholder()**方法选择占位符。 此方法接受整数参数。 通过传递0到它，你会得到 **XSLFTextShape** 对象，使用它可以访问幻灯片的标题文本区域。 使用setText()方法设置标题，如下所示:

```java
XSLFTextShape title1 = slide.getPlaceholder(0);
//setting the title init
title1.setText("Tutorials point");
```

下面给出的是在演示文稿中创建带有标题布局的幻灯片的完整程序:

```java
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.SlideLayout;
import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlide;
import org.apache.poi.xslf.usermodel.XSLFSlideLayout;
import org.apache.poi.xslf.usermodel.XSLFSlideMaster;
import org.apache.poi.xslf.usermodel.XSLFTextShape;

public class TitleLayout {

   public static void main(String args[]) throws IOException{
   
      //creating presentation
      XMLSlideShow ppt = new XMLSlideShow();	    	
      
      //getting the slide master object
      XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
      
      //get the desired slide layout 
      XSLFSlideLayout titleLayout = slideMaster.getLayout(SlideLayout.TITLE);
                                                     
      //creating a slide with title layout
      XSLFSlide slide1 = ppt.createSlide(titleLayout);
      
      //selecting the place holder in it 
      XSLFTextShape title1 = slide1.getPlaceholder(0); 
      
      //setting the title init 
      title1.setText("Tutorials point");
      
      //create a file object
      File file=new File("C://POIPPT//Examples//Titlelayout.pptx");
      FileOutputStream out = new FileOutputStream(file);
      
      //save the changes in a PPt document
      ppt.write(out);
      System.out.println("slide cretated successfully");
      out.close();  
   }
}
```

带有新添加的标题布局幻灯片的PPT文档如下所示: 

![](1482819541953509 (1).jpg)



## 标题和内容布局

让我们使用标题和内容布局在PPT中创建幻灯片。 按照下面给出的步骤。

**步骤1** :通过实例化 **XMLSlideShow** 类创建一个空的演示文稿，如下所示:

```java
XMLSlideShow ppt = new XMLSlideShow();
```

**步骤2** :使用 **getSlideMasters()**方法获取幻灯片主题列表。 使用索引选择所需的幻灯片母带，如下所示:

```java
XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
```

这里我们得到的默认幻灯片母版是在幻灯片主数据的第0位置。

**步骤3** :使用 **XSLFSlideMaster** 类的 **getLayout()**方法获取所需的布局。 此方法接受一个参数，您必须传递代表我们所需布局的 **SlideLayout** 类的静态变量之一。 这个类中有几个变量代表幻灯片布局。

以下代码段显示如何创建标题和内容布局:

```java
XSLFSlideLayout contentlayout = slideMaster.getLayout(SlideLayout.TITLE_AND_CONTENT);
```

**步骤4** :通过将幻灯片布局对象作为参数传递来创建新幻灯片。

```java
XSLFSlide slide = ppt.createSlide(SlideLayout.TITLE_AND_CONTENT);
```

**第5步**:使用 **XSLFSlide** 类的 **getPlaceholder()**方法选择占位符。 此方法接受整数参数。 通过传递1给它，你会得到 **XSLFTextShape** 对象，使用它可以访问幻灯片的内容区域。 使用setText()方法设置标题，如下所示:

```java
XSLFTextShape title1 = slide1.getPlaceholder(1);
//setting the title init 
title1.setText("Introduction");
```

**步骤6** :使用 **XSLFTextShape** 类别的 **clearText()**方法清除投影片中现有的文字。

```java
body.clearText();
```

**步骤7** :使用 **addNewTextParagraph()**方法添加新段落。 现在使用 **addNewTextRun()**方法向段落中添加一个新的文本运行。 现在到文本运行，使用 **setText()**方法添加文本，如下所示:

```java
body.addNewTextParagraph().addNewTextRun().setText("this is  my first slide body");
```

下面给出的是在演示文稿中创建带有标题布局的幻灯片的完整程序:

```java
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;

import org.apache.poi.xslf.usermodel.SlideLayout;
import org.apache.poi.xslf.usermodel.XMLSlideShow;
import org.apache.poi.xslf.usermodel.XSLFSlide;
import org.apache.poi.xslf.usermodel.XSLFSlideLayout;
import org.apache.poi.xslf.usermodel.XSLFSlideMaster;
import org.apache.poi.xslf.usermodel.XSLFTextShape;

public class TitleAndBodyLayout {
   
   public static void main(String args[]) throws IOException{
   
      //creating presentation
      XMLSlideShow ppt = new XMLSlideShow();
      
      //getting the slide master object
      XSLFSlideMaster slideMaster = ppt.getSlideMasters()[0];
      
      //select a layout from specified list
      XSLFSlideLayout slidelayout = slideMaster.getLayout(SlideLayout.TITLE_AND_CONTENT);      
      
      //creating a slide with title and content layout
      XSLFSlide slide = ppt.createSlide(slidelayout);
      //selection of title place holder
      XSLFTextShape title = slide.getPlaceholder(0);
      
      //setting the title in it
      title.setText("introduction");
      
      //selection of body placeholder
      XSLFTextShape body = slide.getPlaceholder(1);
      
      //clear the existing text in the slide
      body.clearText();
      
      //adding new paragraph
      body.addNewTextParagraph().addNewTextRun().setText("this is  my first slide body");
      
      //create a file object
      File file=new File("contentlayout.pptx");
      FileOutputStream out = new FileOutputStream(file);
      
      //save the changes in a file
      ppt.write(out);
      System.out.println("slide cretated successfully");
      out.close();                
   }
}
```

![](1482819573818695.jpg)





https://www.w3cschool.cn/apache_poi_ppt/apache_poi_ppt_slide_layouts.html