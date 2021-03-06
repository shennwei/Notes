# 第21章 CLI
## 21.1 CLI的定义
C#生成的不是处理器能直接解释的指令，而是一种中间语言指令。这种中间语言就是**公共中间语言(Common Intermediate Language，CIL)**。第二个编译步骤通常在执行时发生。在这个步骤中，CIL被转换为处理器能理解的机器码。负责管理C#程序执行的代理是**虚拟执行系统(Virtual Execution System,VES)**，它就是“运行时”，负责加载和运行程序，并在程序运行时提供额外的服务(比如安全保障、垃圾回收等)。
CIL和“运行时”被包括在一项国际性标准中，即**公共语言基础结构(Common Language Infrastructure，CLI)**。
CLI包括：
* 虚拟执行系统(VES，即常说的“运行时”)
* 公共中间语言(CIL)
* 公共类型系统(Common Type System,CTS)
* 元数据(Metadata)
* 框架(Framework)
## 21.3 C#编译成机器码
C#编译需要两个步骤
1. C#编译器将C#转换为CIL
2. 将CIL转换为处理器能够执行的指令
“运行时”将CIL语句编译为机器码，称为**即时编译**
## 21.4 运行时
在“运行时”环境中执行的代码称为托管代码，在“运行时”控制下的执行过程则称为**托管执行**，执行的控制转向数据就成为了**托管数据**
公共语言运行时(CLR)从技术上讲并不是CLI的一个专业术语。CLR更像是微软专门针对.NET平台实现的“运行时”。
### 垃圾回收
垃圾回收是根据程序的需要自动分配和回收内存的过程。垃圾回收器只负责内存管理。
### .NET的垃圾回收
.NET平台实现的垃圾回收机制使用一个分代的(generational)、支持压缩的(compacting)以及基于mark-and-sweep(标记并清除)的算法。
## 21.5 应用程序域
应用程序域的行为类似于一个操作系统进程。有了应用程序域，能在一个进程内运行多个应用程序域，从而避免额外的花费。
## 21.6 程序集、清单和模块
编译输出的通常是一个程序集，除了CIL指令，程序集还包括一个清单(manifest)
清单包括：
* 程序集定义和导入的类型
* 程序集本身的版本信息
* 程序集依赖的其他文件
* 程序集的安全权限
清单本质上是程序集的一个标头(header)，提供了与程序集的构成有关的所有信息，另外还有对这个程序集进行唯一性标识的信息。
程序集可以是类库，也可以是可执行文件本身。一个程序集能引用其他程序集。
程序集是可以版本化和安装的最小单元。构成程序集的单独模块则不是最小单元。
## 21.7公共中间语言
CIL支持多种语言在同一个应用程序内的交互。
## 21.8 公共类型系统
CTS定义了类型的结构及其在内存中的布局，另外还规定了与类型有关的概念和行为。在CTS内部，类型分为值和对象。
## 21.9 公共语言规范
CLS，侧重于库的实现，提供编写库的标准。
## 21.10 基类库
提供了基本的类型和API，使程序能以一致的方式与“运行时”和底层操作系统进行交互。
## 21.11 元数据
元数据包括：
* 程序或类库中每一个类型的描述
* 清单信息，包括与程序本身有关的数据，以及它所依赖于的库
* 嵌入代码中的自定义特性，提供与特性所修饰的构造有关的额外信息。
