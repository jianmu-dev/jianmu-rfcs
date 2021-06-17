
# Jianmu RFCs

Jianmu(建木)使用RFC(request for comments)流程的工作方式来收集对Jianmu的重大功能变更或架构设计决策

RFC也可以理解成一种架构设计决策记录([Architecture Decision Records](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions))

通过RFC的方式协作可以使贡献者们在整个变更过程中更清晰的交流观点与设计思想

# 何时启动一个RFC

当一个重大的功能变更或架构设计决策，会对最终用户、操作人员或贡献者产生重大影响时，我们可以启动一个RFC来对该问题进行描述和讨论

### 如何定义“重大影响”？ 一般包括以下情况:

针对核心逻辑组件的修改，如流程编排方式、任务调度逻辑、触发器或加入新的逻辑组件时

修改Jianmu的打包、编译或配置分发方式时

重大的架构调整，如更新JDK版本、更改用户身份认证方式等时

新增或更改与其他第三方系统的接口或SDK的内置集成时

### 无需太多讨论的情况不需要启动RFC流程:

Bug修复和优化，没有产生逻辑语义上的修改时

对最终用户影响非常小的功能修改或优化


# 如何提交一个RFC

1、Fork本仓库

1、复制 `000-example` RFC模板，改为新提案的名字，例如： `000-my-proposal`

1、在 `000-my-proposal/proposal.md` 中写下你的提案

   *  参考建木的[设计原则](DESIGN_PRINCIPLES.md)

   *  在你的RFC目录下可以提交你需要的图片、示例代码等资源

1、提交Pull Request

   *  简单描述即可：详细信息应该在你的提案中

1、RFC将会被分配给核心团队的一名成员，他讲负责提供反馈直到该RFC通过或关闭。

# RFC评审

欢迎Jianmu用户与Jianmu核心团队一起对RFC进行评审。来自不同角度的反馈与看法对于确定提案的效果、影响与优先级非常有帮助。

同时，参与RFC评审也是早日加入Jianmu核心团队的最好方式。

评审应专注于解决悬而未决的问题、发现暴露的风险和缺点，并对整体方法提出建设性的意见。

评审应通过PR的评论功能在对应的行上留下问题和注释，以便讨论可以串联起来并跟踪状态。

# 实现一个RFC

# RFC修订流程
