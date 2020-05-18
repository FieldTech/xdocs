# 规范化代码提交

X-Developer 构建了 `simple-conventional-changelog` 提交规范的开源工具，通过这个工具，您可以自动化地生成一行标准的注释，描述了需求编号、提交类型和提交说明。如下所示：

```
#123 feat 中文交互式支持
```

## 安装

`commitizen` 提供了交互式命令行，来生成格式化的 `Git` 注释，运行以下命令进行安装。

```bash
npm install -g commitizen
```

## 配置

进入您的 Git 仓库目录，如果不是 `node.js` 项目，需运行以下命令创建一个 `package.json` 文件。

```bash
npm init --yes
```

随后运行以下命令即启用 `simple-conventional-changelog` 提交规范，自动化地生成提交注释。

```bash
commitizen init @fieldtech/simple-conventional-changelog --save --save-exact
```

检查 `package.json` 可看到下面的生成项。

```json
{
    "config": {
        "commitizen": {
            "path": "./node_modules/@fieldtech/simple-conventional-changelog"
        }
    }
}
```

## 提交代码

安装 `commitizen` 后，使用 `git cz` 来替代 `git commit` 提交代码。

```bash
git cz
```

随后您将看到交互式操作界面，根据提示即可完成规范的注释提交。

![](_media/add-commit.png)

---

## 个性化配置

此为可选项，可以通过更改以下的 `key` 值进行个性化配置。

- maxHeaderWidth：注释行的最大长度
- defaultType：默认的提交类型
- defaultSubject：默认注释
- defaultIssues：默认任务编号


```json
{
    "config": {
        "commitizen": {      
            "path": "./node_modules/@fieldtech/simple-conventional-changelog",
            "maxHeaderWidth": 100,
            "defaultType": "",     
            "defaultSubject": "",
            "defaultIssues": ""
        }
    }
}
``` 

## 参考

- [Conventional Commits 1.0](https://conventionalcommits.org)
- [commitizen](https://github.com/commitizen/cz-cli)
- [Simple Conventional Changelog](https://github.com/FieldTech/simple-conventional-changelog)