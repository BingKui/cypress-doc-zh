# 安装 Cypress

> **你能学到**
> - 如何通过 `npm` 安装 Cypress。
> - 如何通过直接下载安装 Cypress。
> - 如何通过 `package.json` 控制版本和运行 Cypress。

## 系统要求

Cypress 是一个安装在你的电脑上的桌面应用程序。此桌面程序支持这些操作系统：

- **Mac OS**  10.9+，只提供 64 位的二进制文件。
- **Linux** Ubuntu 12.04+，Fedora21，Debian8
- **Windows** 7，只提供 32 位的二进制文件。

## 安装

### npm 安装

通过 `npm` 安装 Cypress 非常容易：

```
> cd /your_project_path
> npm install cypress --save-dev
```

这将把 Cypress 作为开发依赖安装进你的项目。

> 确保你已经运行了 `npm init` 或者在项目的更目录中有 `node_modules` 文件夹或者存在 `package.json` 文件，以确保 Cypress 能正确的安装到相应目录。

> 注意：Cypress 的 `npm` 软件包是 Cypress 二进制文件的封装。`npm` 软件包的版本决定了下载的二进制文件的版本。

> **最佳实践**
> 推荐方法是使用 `npm` 安装 Cypress，因为：
> - Cypress 的版本与其他所有版本相同
> - 它简化了持续集成中 Cypress 的运行。

### 直接下载

如果你的项目中没有使用 `node` 或者 `npm`，或者你只是想要尝试 Cypress ，则可以直接从我们的 CDN 直接下载 Cypress。

直接下载将始终获取最新的可用版本。会自动检测你的平台下载。

只需手动解压缩并双击即可。Cypress 不需要安装任何依赖即可运行。

### 持续集成

请阅读我们[持续集成]()的文档，以获取在 CI 中安装 Cypress 的帮助信息。 在 Linux 中运行时，你需要安装一些系统相关依赖关系，或者你也可以使用我们的 Docker 镜像，这些镜像具有你需要预建的所有功能。

## 打开 Cypress

如果你使用 `npm` 进行安装，Cypress 已经被安装到你的 `./node_modules` 目录，其二进制可执行文件在 `./node_modules/.bin`。 这意味着你可以通过以下方式在你的项目根目录中调用它：

通常的完整路径

```
> ./node_modules/.bin/cypress open
```

或者使用 `npm bin` 的快捷方式

```
> $(npm bin)/cypress open
```

或者使用 `npx`

注意：[npx](https://www.npmjs.com/package/npx) 在 `npm > v5.2` 中包含，或者可以单独安装。

```
> npx cypress open
```

片刻之后，Cypress 测试工具就会启动。

### 添加运行命令

虽然每次写出 Cypress 可执行文件的完整路径没有任何问题，但是将 Cypress 添加到 `package.json` 的 `script` 会更加快捷和方便。

```
{
  // package.json

  "scripts": {
    "cypress:open": "cypress open"
  }
}
```

现在你可以这样调用该命令：

```
> npm run cypress:open
```

Cypress 会为你打开。

## CLI 工具

通过 `npm` 安装 Cypress ，你还可以访问许多其他 CLI 命令。

在 `0.20.0` 版本中，Cypress 也是一个完整的 `node_modules` 模块，你可以在你的脚本标签中添加它。

你可以[查看更多 CLI 命令]()。

## 高级功能

### 环境变量

使用环境变量，你可以控制 Cypress 的安装方式。

这有助于你：

- 安装与默认npm软件包不同的版本
- 指定外部URL（绕过企业防火墙）
- 指定一个本地文件（在本地安装而不是使用互联网）

要覆盖已安装的内容，只需使用 `npm install` 命令设置 `CYPRESS_BINARY_VERSION` 即可。

例如：

1. 使用二进制 `1.0.1` 版本安装 `1.0.3` 版本的 Cypress。

```
> CYPRESS_BINARY_VERSION=1.0.1 npm install cypress@1.0.3
```
2. 从给定的 URL 安装 Cypress 二进制文件。

```
> CYPRESS_BINARY_VERSION=https://company.domain.com/cypress.zip npm install cypress
```

3. 从本地文件安装 Cypress 二进制文件。

```
> CYPRESS_BINARY_VERSION=/local/path/to/cypress.zip npm install cypress
```

以上所有情况，二进制文件从自定义位置安装的记录不会保存到 `package.json` 文件中。 每次重复安装都必须使用