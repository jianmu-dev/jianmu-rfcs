提案实现进度，见[Issue I4GTGW](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4GTGW)

# 概述

* 优化**全局参数**声明方式
* 优化**输出参数**引用方式

# 问题描述

* 全局参数声明方式：

```
param:
  v2: xxx
```

* 参数引用方式：

```
# 事件参数v1
${event.v1}
# 全局参数v2
${global.v2}
# 名为Build1的节点输出参数v3
${Build1.v3}
```

问题： 引用的参数scope与yml的层次结构不匹配，导致理解和应用门槛的提升

# 约束条件

* 已有的项目中，全局参数的声明方式均失效

# 解决方案

* 全局参数声明方式：

```
global:
  param:
    v2: xxx
```

* 参数引用方式：

```
# 事件参数v1，保持不变
${event.v1}
# 全局参数v2，保持不变
${global.v2}
# 名为Build1的节点输出参数v3，兼容当前用法
${Build1.v3} => ${pipeline.Build1.v3} | ${workflow.Build1.v3} | ${Build1.v3}（此为快捷方式，缓解语法噪音）
```

# 待讨论问题

无

# 已解决问题

无

# 后果

* 引用的参数scope与yml的层次结构保持一致，降低理解和应用门槛