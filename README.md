<div align="center">

# X-Developer 文档

介绍设计概念、路线图、功能与使用说明

</div>

> **V3.2最新发布：**基于继承关系的过滤器，创建指定范围的数据集，实现灵活的分析范围。

## 主要功能

X-Developer 定位于 **向技术组织管理者** 的研发数据分析平台，主要功能是向 Git 仓库及其它三方研发工具（如 Jira、SonarQube、Jenkins、Tempo Timesheet 等）自动化地完成数据采集，通过我们自主研发的效能分析引擎，为您生成研发管理、项目管理、工程管理、质量管理等多维度的指标和分析报表。

- **数据集成：**向导式、配置化的界面，轻松整合来自多个工具的数据，进行**目录式管理**，并可基于**自定义的过滤器**灵活地为分析项目筛选数据范围。
- **度量指标：**在 V2.0 各类敏捷精益指标的基础上，增加了多个复合型指标如 **人均代码产出率、千行代码债务率**，辅助您动态观测研发活动。
- **数据仪表板：**全面升级UI界面和体验，采用指标与图表组合展现方式，分类组织各类研发数据。

![交付洞察](_media/deep-insights.png)

## 3.0 新特性

升级为全新的仪表板，从 **时间跟踪、绩效考核、深度洞察和行业对比** 多维度地展示研发指标和图表。

|<nobr>编号</nobr> |<nobr>特性</nobr> |<nobr>类别</nobr>  | <nobr>说明</nobr>|
|:---:| :--- | :---: | :---
|1|<nobr>仪表板<nobr>|功能|UI全新升级，指标全面采用趋势线、当前值/环比值和环比变化率的组合展现方式，绝大多数图表支持直接的按时间分区（如日/周/月）点击查看。|
|2|<nobr>代码产出率</nobr>|<nobr>指标<nobr>|从多个仓库、分支中收集提交记录，合并、除重之后，基于统计方法平滑代码行数量，分析团队人均代码产出量的变化，包含主干与分支的统计，可下钻到人员。|
|3|<nobr>千行代码债务率</nobr>|<nobr>指标<nobr>|通过静态分析缺陷数量与代码产出量的综合分析，评估技术债务的密度，可下钻到人员。|
|4|<nobr>自定义过滤器</nobr>|<nobr>集成<nobr>|可配置集成过程中筛选的规则和范围，通过父级继承关系，可灵活地复用组织级、部门级、产品级、项目级的数据源。|
|5|<nobr>自定义数据源</nobr>|<nobr>集成<nobr>|支持在分析项目中指定过滤器及目标项目/仓库，来灵活地配置与更改数据范围。|

更多功能细节请访问 [版本更新](updates) 说明页面。

---

## 如何使用

X-Developer 提供 SaaS 服务、私有部署两种模式，支持客户定制化开发。SaaS 模式下，您只需要注册帐号、完成购买，即可开始使用度量分析服务。如果您需要私有部署，我们会为您提供包含部署、安装、内部培训等支持。

### 1. 免费体验

我们为每位用户提供 30 天免费体验服务，在期限内，您可以完成研发工具的集成、数据同步、分析并查看分析报告。

### 2. 企业试用

X-Developer 仅为签订《产品试用协议》的企业提供试用。如果您有比选采购意向或内部尝试的兴趣，可在 [申请企业试用](https://x-developer.cn/request) 页面提交请求，我们会在两个工作日内与您商谈。

!> X-Developer 是商业产品，并且价格亲民，试用仅面向企业。如果您是个人用户，有使用或学习效能分析的需求，请选择直接购买，勿通过企业试用通道申请。我们可为您开具个人或企业抬头的发票。

### 3. 购买产品

#### 2.1 购买 SaaS 服务

X-Developer SaaS 服务采用预付费模式，订购成功之后，以下两个计时期间我们不会向您收取任何费用：

**接入期间：**直至您成功接入 X-Developer 至生成数据报表的期间，您的预付费用不会产生任何的变动。在此期间，您可以向我们反馈使用期间的问题，获得技术支持与帮助。

**调整期间：**完成接入并生成报表后，您仍有 7 天的免费期限用于对数据进行一些调整。例如，您可以选择一个小范围的团队进行试运行，对一些重名的开发者（他们可能被多计费）进行名称合并等，并对这些项目进行删除或重建，以使数据分析的价值最大化。

在 7 天的调整期间之后，我们会视为正式运行期，在每月底将对您的帐户进行费用扣除。

#### 2.2 购买私有部署版本

购买之前如有试用需求，请在 [申请企业试用](https://x-developer.cn/request) 页面提交请求，我们将先与您签订试用合同，并提供 2 个 SaaS 试用许可证和约定的试用期限供您内部测试。

产品采购之后，将按照正式的《产品技术服务合同》履行相关的权利责任。

### 4. 定制化开发

X-Developer 支持在基础版和专业版之上进行定制开发，并可基于 SaaS 或私有部署进行交付，其中 SaaS 交付模式仅收取适当的费用。

> **30 天交付承诺：**通常情况下，我们会在 30 天内发布定制化需求，如果是较大的需求，我们会进一步与您商讨交付时间点和细节。

## 需要支持

如果您需要任何帮助与支持，可通过产品内部的反馈功能提交，或直接联系我们：[support@withfield.tech](mailto:support@withfield.tech)

## 版权声明

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br /><a xmlns:dct="http://purl.org/dc/terms/" href="https://fieldtech.github.io/xdocs" property="dct:title" rel="dct:type">X-Developer 产品文档</a> 由 <a xmlns:cc="http://creativecommons.org/ns#" href="https://withfield.tech" property="cc:attributionName" rel="cc:attributionURL">场量科技</a> 采用 <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">知识共享 署名-非商业性使用-禁止演绎 4.0 国际 许可协议</a> 进行许可。

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.
