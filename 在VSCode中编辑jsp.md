# 准备

1. jdk（Java develop kit）
2. VSCode（visual studio code）
3. Maven
4. Tomcat

# 安装软件

1. 安装jdk
2. 配置环境
   1. JAVA_HOME
   2. Path
      1. %JAVA_HOME%\bin
      2. %JAVA_HOME%\jre\bin
   3. CLASSPATH
      1. .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar; 

3. 安装VSCode
4. 下载并解压Maven
5. 下载并解压Tomcat
6. 配置Maven与Tomcat的环境变量Path
   1. D:\Users\apache-maven-3.8.8-bin\apache-maven-3.8.8\bin
   2. D:\Users\apache-tomcat-10.1.28\bin

# 为`VSCode`安装必要插件

1. Extension Pack for Java
2. 设置Maven for Java插件的配置文件路径
   1. 在设置中搜索Maven，找到`Java>Configratuin>Maven:Global Settings`
   2. 添加配置文件路径 D:\Users\apache-maven-3.8.8-bin\apache-maven-3.8.8\conf
3. 安装Tomcat for Java插件（已弃用），官方推荐：Community Server Connectors

# 初始化项目

### 新建Project

1. `ctrl+shift+P`，输入maven，从Maven原型创建新项目
2. 选择maven-archetype-webapp
3. 选择1.4
4. Group Id直接Enter
5. artifact Id直接Enter
6. 选择一个无用的文件夹即可
7. 然后下方命令行需要Enter两次
8. 显示绿色的BUILD SUCCESS就创建完毕了，可以点击右下角蓝色按钮打开project

### 修改`pom.xml`

1. 1.7修改为1.8

```java
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>
```

2. `ctrl+shift+P`，输入maven，点击添加依赖，输入`servlet`然后enter，选择一个`javax.servlet`即可