提案实现进度，见[Issue I4FPVL](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4FPVL)

# 概述

在现有的DSL中新增一个Shell脚本节点，可以直接执行Shell命令

# 问题描述

当前需要提供一种简化的在任务容器内直接执行shell命令的能力，而不是执行一条命令也需要自定义节点。

# 约束条件

无

# 解决方案

在当前的流程DSL语法中提供类似下面的语法：
```
shell_node:
    image: ubuntu:18.04
    environment:
        ABC: abc666
    script: 
        - echo $ABC
        - npm install
```
当执行到该节点时，可以直接进入指定镜像启动的容器中执行shell命令

# 待讨论问题

无

# 已解决问题

无

# 后果

使用该节点时无法同时使用输入输出参数，但在`environment`段中可以使用表达式，引用全局参数、事件参数或上游节点的输出参数
