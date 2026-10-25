# Cmake 与 Catkin学习笔记

## 背景
- 计算机只能看懂二进制代码，所以我们写的高级语言就需要编译器转化成机器语言。Makefile就像一本自动编译说明书，告诉make工具那些文件要编译、编译的顺序是什么、需要哪些命令。这样，在我们每一次编写修改好代码之后只需敲一次make命令就能得到目标程序。
## 一、 为什么需要 CMake？（背景与演进）
- **CMake 的诞生**：当工程体量的增大，Makefile规则也越来越多，不能满足需求，于是出现了Cmake。CMake 是一个**更高层、跨平台的编译工具**。我们只需要写简单的配置文件，CMake 就能自动帮我们生成各个平台对应的 Makefile。

## 二、 Catkin：ROS 的专属编译系统
- **什么是 Catkin**：ROS 对 CMake 进行了扩展，形成了 Catkin 编译系统，专门用来管理 ROS 的庞大工程。
- **工作空间（Workspace）结构**：
  - `src`：存放源代码。
  - `build`：编译过程中的中间文件。
  - `devel`：开发空间，存放最终生成的可执行文件和环境变量。
- **功能包（Package）**：
  - 包含 `CMakeLists.txt`（编译规则）和 `package.xml`（描述信息）。
  - 创建包的命令（同时指明依赖）：`catkin_create_pkg test_pkg std_msgs rospy roscpp`。

## 三、 关于使用大模型辅助学习的思考
- **“你老是依赖棒棒糖，迟早会吃亏的。”**
- AI 是非常厉害的老师，它可以帮我解释报错、梳理概念。但如果我直接让 AI 帮我写完整的代码和笔记自己连读下去的耐心都没有，那就是失去了思考的能力对自己不会有任何进步。所以必须保持自己的独立性，把 AI 当工具。

## 四、 Catkin 工作空间实操流程
在 ROS 中，所有的代码都必须放在特定的工作空间中进行编译。

```bash
# 1. 检查系统是否安装了 catkin
catkin --help

# 2. 创建主文件夹，并进入
mkdir catkin_ws
cd catkin_ws

# 3. 创建存放源代码的 src 文件夹
mkdir src

# 4. 进入 src 文件夹并初始化工作空间
cd src
catkin_init_workspace

# 5. 退回工作空间根目录
cd ..

# 6. 编译整个工作空间
catkin build 
```

