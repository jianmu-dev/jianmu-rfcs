# 概述

* 在全局/节点定义中，增加on-failure字段，用于配置流程或节点执行失败时的处理方式。

# 问题描述

* 存在节点错误后仍需继续执行后续节点的场景。

* 当前无法利用节点内置的execution_status输出参数和条件网关进行失败告警等配置。

# 约束条件

无  

# 解决方案
  
在全局/节点添加`on-failure`字段，优先级：节点>全局。  
语法：  
on-failure: terminate （自动，默认值）。  
on-failure: ignore （自动），具体选哪个先要确定任务状态机。  
on-failure: manual （手动，可人工操作terminate / ignore / retry）。   

* 引用示例：
全局：  
```
global:
  on-failure: xxx
```
节点：  
```
pipeline:
  git_clone:
    on-failure: xxx
    type: xxx:xxx
```

# 待讨论问题

无

# 已解决问题

无

# 后果

无
