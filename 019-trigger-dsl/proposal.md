提案实现进度，见[Issue I4HL00](https://gitee.com/jianmu-dev/jianmu-ci-server/issues/I4HL00)

# 概述

在现有的DSL中新增一个trigger定义，统一概念，包含webhook和cron等不同类型并为未来扩展留下余地

# 问题描述

当前的EventBridge机制使用过于复杂且没有DSL化，无法实现代码驱动。与Cron为分离概念，不便于理解

# 约束条件

无

# 解决方案

在当前的流程DSL语法中提供类似如下语法：

Cron类型的trigger定义：
```
trigger:
    type: cron
    schedule: 0 0 10 * * ?
```

Webhook类型的trigger定义：
```
trigger:
    type: webhook
    param:
          - name:  xxx
             type: STRING
             exp: $.xxx.xxx
    auth: 
          token: ${trigger.xxx}
          value: ((xxx.xxx))
    only: ${trigger.xxx} == false
```


# 待讨论问题

无

# 已解决问题

无

# 后果

之前版本如果使用了cron或eb语法，需要转换为trigger语法
