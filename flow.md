# 开发流程

X-Developer 为您提供了基于 Git 的开发流程，包括开发纪律、分支管理策略、代码提交自动化工具，帮助您的团队形成良好、一致的提交规范，以便于清晰准确地记录代码变更、进行代码评审，也便于后期快速定位原始需求或缺陷。

## 开发纪律

- 每天工作的第一件事是从远程仓库更新代码，每天频繁更新和提交代码是优秀开发人员的习惯
- 每天工作的最后一件事是提交本地代码到远程仓库。如代码存在问题，可先提交到本地，即运行 `git commit`
- 使用GIT进行一切代码的变更管理，禁止把代码从一个文件夹拷贝出再拷贝入的方式暂存改动

## 管理策略

X-Developer 推荐使用 `master` `dev` `feature` 作为固定分支，方便快速的日常协同，`hotfix` 为线上修复临时分支，方便快速发布。各分支的创建和合并过程如下图所示：

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
commit
branch feature_no
checkout feature_no
commit
commit
checkout dev
commit
merge feature_no
checkout master
branch hotfix_no
checkout hotfix_no
commit
checkout master
commit
merge hotfix_no
merge dev
```

### 角色与权限

- 提交者 Commiter：已经养成良好的提交规范，并具有代码评审的能力。负责合并参与者的合并请求。
- 参与者 Contributor：尚未养成良好的提交规范，代码经常存在较多的不规范，需要通过合并请求向仓库正式提交代码。

### 角色与分支关系

如下表所示。

分支|	所有者|	使用说明|	构建频率|	发布目标
:--- |:---|:---|:---|:---
master |	技术负责人 |	主干，对应生产版本|	按需手动构建|	生产环境
dev	|提交者	|开发分支，对应测试版本	|周一至周五，早八点至下午七点自动构建	|测试环境
feature_{no}|	参与者	|特性分支，对应本地版本	|无自动化构建	|本地环境
hotfix_{no}|	指定解决者	|修复分支	|按合并构建	|测试环境

## 部署过程

#### 日常版本开发

从本地向 `dev` 分支提交，发布前开发人员向 `master` 提交合并请求，由技术负责人审核代码变更并完成 `master` 合并。

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
branch local_dev1
checkout local_dev1
commit
checkout dev
branch local_dev2
checkout local_dev2
commit
checkout dev
commit
merge local_dev1
commit
merge local_dev2
checkout master
commit
merge dev
```

#### 生产环境发布

合并 `master` 后，技术负责人在本地 `dry run` ，成功后根据 CI 策略自动化或手动发布生产环境，并测试生产环境主要功能。


`dev` 分支上的代码最终合并至 `master` 进行发布，如下图所示。

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
commit
checkout master
commit
checkout master
merge dev
```

#### 线上缺陷修复

从 `master` 建立 `hotfix_{no}` 分支，修改完成后提交向 `master` ，然后向 `dev` 合并。

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
commit
checkout master
branch hotfix_no
checkout hotfix_no
commit
checkout master
commit
merge hotfix_no
checkout dev
merge master
checkout master
commit
merge dev
```

## 使用规范

#### 第一步，配置Git用户名和邮箱

```bash
git config --global user.name "中文姓名"
git config --global user.email "公司邮箱"
```

#### 第二步，克隆项目仓库到本地

```bash
cd /folder/
git clone https://repourl/reponame.git
```

#### 第三步，检查本地分支

```bash
cd reponame
git branch
# 应输出：
* master
  dev
```

> 适用于提交者角色：dev分支使用规范

提交者只能使用 `dev` 分支进行任务开发。操作规范：

#### 第四步，切换工作分支到dev分支

```bash
git checkout dev
git pull
```

> 适用于参与者角色：feature分支使用规范

参与者只能使用 `feature` 分支进行单项任务开发。feature分支命名规则：`feature_{任务编号}` 。操作规范：

#### 第四步，基于dev分支创建feature分支

以下示例为将开发任务123，基于 `dev` 创建 `feature` 分支，命名为 `feature_123`

```bash
git checkout dev
git checkout -b feature_123`
# 检查当前工作分支
git status
# 应输出
On branch feature_123
```

`feature` 分支上的代码通过合并至 `dev` 进行评审和测试，最终由 `dev` 向 `master` 合并，完成发布。如下图所示：

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
commit
branch feature_123
checkout feature_123
commit
commit
checkout dev
commit
merge feature_123
checkout master
commit
merge dev
```

#### 第五步，工作过程中合并dev分支最新代码

为保证始终和团队代码一致，需要经常拉取和合并最新代码到本地，否则，等到完成 `feature` 时代码已经有很多的冲突了。操作如下：

```bash
git checkout dev #切换到dev分支
git pull #获取dev分支最新代码
git checkout feature_123 #切换到feature分支
git merge dev #合并团队的代码
```

未完成开发或未有发布计划的 `feature` 分支应每天从 `dev` 分支获取最新代码，如下图所示：

```mermaid
gitGraph:
options
{
  "nodeSpacing": 100,
  "nodeRadius": 10
}
end
commit
branch dev
checkout dev
commit
commit
branch feature_123
checkout feature_123
commit
commit
checkout dev
commit
checkout feature_123
merge dev
checkout master
commit
merge dev
```

合并过程中如果遇到冲突，可以使用 IDE 查看冲突，逐行解决，或请求高一级角色的员工协助解决。
