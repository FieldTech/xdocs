# 提交注释规范

在团队协作的项目中，良好、一致的提交规范不但更便于向团队清晰准确地说明代码变更、进行代码评审，也便于后期快速定位原始需求或缺陷。

## 注释规范与度量

### 以 Git 作为事实的唯一真实来源

Git 是现在几乎每个开发人员使用的工具。通过使用 Git 作为应用系统的事实来源，几乎可以操作所有东西。例如，版本控制，历史记录，评审和回滚都是通过 Git 进行的。

所以，X-Developer 选择了 Git 日志作为研发效能度量的事实数据，利用建立在事实之上的分析，帮助管理层进行更加有效的决策。而绝大多数开发团队，还没有形成对提交注释的规范化，这给数据分析带来了难点。

解决提交规范性问题，业界普遍采取的做法包括：

1. Git Hook，在代码提交时强制检查注释规范性，拒绝不规范的提交；
2. 可配置的注释规则，根据定义的配置分析文本再映射到数据规范。

在研究了业界的前沿实践之后，我们锁定了 `Conventional Commits` 标准，来作为标准数据输入的解决方案基础。

## Conventional Commits

[Conventional Commits]((https://conventionalcommits.org)) 由 Google Angular.js 项目团队发起，致力于构建人与机器能够共同理解的代码提交标准，以更好地利用语义化工具提升软件构建、部署和发布的工程效率：

- 自动化生成变更日志
- 根据提交类型，自动化地设置语义化版本
- 向团队成员、用户及其它利益相关者沟通产品功能变更
- 触发构建和发布流程
- 使新成员更容易加入到项目工作中来，因为他们可以通过注释了解代码变更的历史

X-Developer 基于 `Conventional Commits` 构建了一个更加 [简洁的提交风格](https://github.com/FieldTech/conventional-commit-types-zh-cn) 和 [代码提交工具](https://github.com/FieldTech/simple-conventional-changelog) ，适用于国内大规模的企业级开发。

### 工程师驱动的特点

开源组织和国外研发团队规模较小，产品经理往往是作为产品组合管理或产品线经理的角色存在，需求的实现由工程师驱动，围绕 **用户提交** 的 `issue` 和 `pull request` 进行单人开发；在提交时，提交者需要对 `issue` 的范围、内容进行说明，以便于评审者进行代码 `review` 。`issue` 的来源可能是一个新功能需求，也可能是一个线上缺陷。

`Conventional Commits 1.0` 标准要求详细说明改动的类型、影响范围、标题、内容和关联 `issue`（写在底部）：

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

### 企业级开发的特点

国内开发团队的规模和需求规模更大，改动更频繁，开发团队完成的是 **专职的产品经理、BA编写严格的需求文档** ，所以不适用于在单个 `pull request` 的提交注释中描述完整的需求。

X-Developer 的 `Simple Conventional Changelog` 使用一行带有需求编号、提交类型和说明的注释规范来说明提交变更，去掉了复杂的注释标题和正文描述。

```
<no> <type> <subject>
```

使用 `git` 的提交写法如下：

```bash
git commit -m "#123 fix 中文交互式支持"
```

## 提交类型说明

类型 | 类型说明 | 描述
:----------- | :----------- | :-----------
feat   |     Features   |      新功能
change    |   Changes  |      需求变更
fix   |     Bug Fixes    |      缺陷修复
test   |     Tests    |      新增或修改测试代码
docs  |     Documentation |      文档变更
style |     Styles     |      代码格式调整，未涉及功能修改（如对齐、补全分号）
refactor  |     Code Refactoring     |     代码重构，未涉及功能或缺陷修复
perf   |     Performance Improvements    |      性能优化
build   |     Builds  |     构建工具或依赖管理调整
ci   |    Continuous Integrations    |     自动化构建脚本变更
chore   |     Chores    |     其它非代码或测试的变更
revert   |     Reverts    |     恢复到上一次版本

在下一篇我们介绍如何使用提交工具自动生成 `Simple Conventional Changelog` 风格的标准注释。
