# 版本控制的演变

<img src="E:\GitMind\版本控制的演变历史.png" alt="版本控制的演变历史" style="zoom: 200%;" />





### 分布式 `VCS`

- 服务端和客户端都有完整的版本库
- 脱离服务端客户端照样可以管理版本
- 查看历史和版本比较等多数操作，都不需要访问服务器，比集中式 `VCS` 更能提高版本控制效率

### Git的特点

- 最优的存储能力
- 非凡的性能
- 开源的
- 很容易做备份
- 支持离线操作
- 很容易制定工作流

# 最小配置

### 配置USER信息

**配置`user.name`和`user.email`**

```shell
$ git config --global user.name 'your_name'
$ git config --global user.email 'your_email'
```

**`config`的三个作用域**

```shell
$ git config --local	#只针对某个仓库有效
$ git config --global	#对当前用户的所有仓库有效
$ git config --system	#对系统所登陆的账户有效
# 缺省等同于 local

# 显示 config 的配置，加 --list
$ git config --list --local
$ git config --list --global
$ git config --list --system
```

# 建Git仓库

1. 把已有的项目代码纳入`Git`管理

```shell
$ cd 项目代码所在的文件夹
$ git init
```

2. 新建的项目直接用`Git`管理

```shell
$ cd 某个文件夹
$ git init your_project #会在当前路径下创建和项目同名的文件夹
$ cd your_project
```

![image-20240829081029076](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829081029076.png)

对新仓库创建 `--local` 信息

![image-20240829082515466](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829082515466.png)

向新仓库中添加文件

![image-20240829082555622](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829082555622.png)

`git add` 将内容写入暂存区

![image-20240829084408908](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829084408908.png)

创建 `commit`

![image-20240829084520851](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829084520851.png)

查看日志 `git log`

![image-20240829084650266](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20240829084650266.png)

> [!IMPORTANT]
>
> **备注：**`local`的优先级要高于`global`,如果初始设置过`global`参数，在新建仓库中使用`local`参数，则当前仓库的配置将覆盖掉`global`

# 向仓库中添加文件

<img src="E:\GitMind\工作流程.png" alt="工作流程" style="zoom:60%;" />

**示例：通过四次提交，形成一个静态页面**

1. 加入`index.html`和`git-logo`
2. 加入`style.css`
3. 加入`script.js`
4. 修改`index.html`和`style.css`

