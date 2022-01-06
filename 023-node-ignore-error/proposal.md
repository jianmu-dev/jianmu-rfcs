# 概述

* 在节点定义中，增加ignore_error字段，用于忽略该节点的错误结果，继续执行流程后续部分。

# 问题描述

* 存在节点错误后仍需继续执行后续节点的场景。

* 当前无法利用节点内置的execution_status输出参数和条件网关进行失败告警等配置。

# 约束条件

无  

# 解决方案

为节点添加`ignore_error`字段，若不配置，则默认值为`false`，即不忽略错误结果，执行错误时流程终止。  
显式配置为`true`时，忽略该节点的执行错误，执行错误时流程继续向后执行。  

* 引用示例：
```
nodejs_build:
  ignore_error: "true"
  type: "nodejs_build:1.2.1-12.16.2"
  param:
    registry_url: "https://registry.npm.taobao.org"
    workspace: "/tmp"
    disturl_url: "https://npm.taobao.org/dist"
```

# 待讨论问题

无

# 已解决问题

无

# 后果

无
