# C和C++编译器

要运行 C 或 C++ 代码，你只需要在你的计算机上安装一个有效的 C/C++ 编译器。如果你使用的是 Linux 操作系统，那么很有可能它已经安装在你的系统上了。但我们需要确保它已正确安装。

要检查你的系统上是否安装了编译器（GCC/G++/MinGW），你需要先检查编译器版本。

只需打开终端并使用 `gcc --version` 和 `g++ --version`。如果你得到版本号，那么说明编译器已经安装在你的系统上。

# 为VSCode安装必要扩展

进入扩展选项卡。搜索 “C” 或 “C++” 并安装第一个已被微软验证的扩展。

![image-20240828154821299](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828154821299.png)

还需要安装 **C/C++ Extension Pack**。这个扩展包同样应当由微软验证。

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828154939107.png" alt="image-20240828154939107" style="zoom: 80%;" />

接下来，搜索 **Code Runner** 并安装该扩展。

![image-20240828155105394](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828155105394.png)

现在，我们需要更改一些设置。

点击**齿轮**箱（它被称为管理部分），然后点击**设置**。或者，你也可以使用快捷键 `Ctrl` + `,`。对于 Mac 系统，需要将 `Ctrl` 键替换为 `Command` 键。

在搜索栏里输入 “Run code in terminal” 并按下 Enter 键。

向下滚动直到找到 `Code-runner: Run In Terminal`。确保该选项被勾选（✔）。

![image-20240828155259615](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240828155259615.png)