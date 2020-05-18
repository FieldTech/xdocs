# Jenkins

如果您使用 Jenkins 来完成持续集成工作，可利用 Jenkins 插件 X-Developer Client Plugin ，简单地安装配置，即可完成集成。
点此下载 X-Developer Jenkins 插件（后缀名为.hpi）。

## 安装配置

### 插件安装

进入Jenkins管理界面-->管理插件-->高级，上传插件界面中，选择您下载的插件文件，上传后将自动安装，无须重新启动。

### 全局配置

进入Jenkins管理界面，您将看到 X-Developer Client Plugin 配置项，填写 APP ID 和 APP KEY，点击 Test connection，如果正确将返回“X-Developer 认证成功”。

![](../_media/jenkins-global-config.png)

### 流水线配置

在团队的构建流水线上，添加“构建后操作”，选择 X-Developer 团队效能分析。

![](../_media/jenkins-pipeline.png)

填写 TEAM ID，展开高级选项（可选）：

- 如果此构建任务是主干分支，请勾选“主干”；如果是开发测试分支，此项请勿勾选。
- 如果您需要每次构建后都执行分析，请勾选“强制分析”。默认情况下，X-Developer 每天 17:00 ~ 20:00 执行分析任务。

![](../_media/jenkins-pipeline-team.png)

## 运行流水线

每次 Jenkins 完成构建任务后，会触发 X-Developer Client 并执行数据传输和分析任务，执行结果将会打印在构建日志中。

## 查看分析结果

X-Developer 在每日 17:00 ~ 20:00 会启动分析，如果你希望立即运行分析，可以在流水线“X-Developer 团队效能分析”高级设置中勾选“强制分析”。

分析成功的邮件将会自动发送到团队创建者邮箱中，点击立即查看即可查看到最新的报告。

![](../_media/analysis-notice.png)