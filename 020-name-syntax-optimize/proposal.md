提案实现见[Issue](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4JQUA)

# 概述

将当前在pipeline与workflow段中的name与description移到顶层

# 问题描述

当前的name与description描述的是整个项目，放在pipeline与workflow段中不清晰

# 约束条件

无

# 解决方案

修改为如下语法：

```
name: project-name
description: project-description
workflow or pipeline:
  xxx:
    - xx: xx
```


# 待讨论问题

无

# 已解决问题

无

# 后果

之前的DSL脚本需要修改
