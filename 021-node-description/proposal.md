提案实现进度，建[issue I4LDS8](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4LDS8?from=project-issue)
# 概述

- 在节点定义中，增加一个alias字段，以便流程可视化界面展示该字段。

# 问题描述

- 有时需要在节点中设置中文名称，以便区更好的区分节点的含义。
- 目前流程可视化界面是根据节点名称显示的，通过修改节点名称为中文是可以做到的，但需要修改相关引用该节点地方，如果引用该节点的地方较多修改起来较为困难。

# 约束条件

无

# 解决方案

- 节点定义中新增alias字段：
```
pipeline:
  git_clone:
    type: git_clone:1.1.1
    alias: 拉取代码
    param:
      remote_url: XXX
```
- 流程可视化界面显示alias
- 如果没有设置alias，默认展示节点名称


# 待讨论问题

无

# 已解决问题

无

# 后果

无
