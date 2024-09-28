## 关于python 3.12.6 ModelNotFound

![image-20240924102916968](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240924102916968.png)

升级 pip 

```cmd
python -m ensurepip --upgrade
```

如果你在使用 Python 3.12.6，那么`distutils`应该已经自带了。你可以尝试在 Python 3.12.6 中导入`distutils`，看看是否可以成功导入。

如果你在使用的是 Python 2.x，那么`distutils`在 Python 2.7.9 及更高版本中已被移除。在这种情况下，你需要使用`pip`来安装`distutils`。在终端中运行以下命令：

```
pip install distutils
```

如果你在使用的是 Python 3.x，并且仍然遇到这个问题，那么可能是你的 Python 环境配置有问题。你可以尝试重新安装 Python，或者在不同的 Python 环境中尝试安装`distutils`。

==该问题通常是由于安装问题==

