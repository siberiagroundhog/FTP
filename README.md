# FTP

FTP 是一个基于 Python 的 FTP 通信实验项目，包含 FTP 服务端、命令式客户端封装以及 PyQt5 图形界面客户端。项目使用 `pyftpdlib` 搭建 FTP 服务端，使用 Python 标准库 `ftplib` 实现客户端通信，并通过 PyQt5 提供本地文件与服务器文件的双栏浏览、上传、下载、删除和刷新等操作。

## 项目简介

本项目用于学习和实践 FTP 协议通信、客户端/服务端交互以及桌面 GUI 开发。服务端提供用户认证、匿名访问、被动端口配置和日志记录能力；客户端封装常用 FTP 操作；图形界面提供登录窗口和文件管理窗口，便于进行上传下载测试。

## 主要功能

- FTP 服务端搭建
- 用户登录与匿名访问配置
- FTP 客户端连接封装
- 服务器目录遍历
- 文件上传与下载
- 文件删除与目录操作
- PyQt5 图形化登录界面
- 本地文件树与服务器文件树展示
- 操作状态提示与后台线程处理

## 技术栈

- Python
- ftplib
- pyftpdlib
- PyQt5
- QThread
- QFileSystemModel
- 自定义服务器文件模型

## 目录结构

```text
FTP/
├── FTPserver/
│   └── myftpserver.py
├── MyModel.py
├── ftp.svg
├── ftpPrompt.py
├── myftp.py
├── pyqt5.py
└── README.md
```

## 环境要求

- Python 3.x
- PyQt5
- pyftpdlib

安装依赖：

```bash
pip install PyQt5 pyftpdlib
```

## 启动服务端

服务端入口位于 `FTPserver/myftpserver.py`。

```bash
python FTPserver/myftpserver.py
```

默认配置包含：

- 监听地址：`0.0.0.0`
- 监听端口：`21`
- 被动端口范围：`2000-2332`
- 日志文件：`myftpserver.log`
- 普通用户：`user / user123`
- 管理用户：`root / 3946`
- 匿名用户目录：`/home/ftp/anonymous/`

注意：在 Linux 中监听 21 端口通常需要管理员权限。运行前请根据本机环境修改用户目录，例如 `/home/ftp/`、`/home/` 等路径。

## 启动图形客户端

图形客户端入口位于 `pyqt5.py`。

```bash
python pyqt5.py
```

启动后会先进入登录窗口，输入服务器 IP、用户名和密码后进入主界面。主界面左侧显示本地文件，右侧显示服务器文件，顶部按钮用于下载、上传、删除和刷新。

## 核心文件说明

- `FTPserver/myftpserver.py`: FTP 服务端配置与启动脚本。
- `myftp.py`: 基于 `ftplib.FTP` 的客户端操作封装。
- `pyqt5.py`: PyQt5 图形客户端，包括登录窗口、主窗口和后台线程。
- `MyModel.py`: 服务器文件树模型。
- `ftpPrompt.py`: 命令行或交互式 FTP 操作相关脚本。
- `ftp.svg`: 客户端图标资源。

## 使用建议

- 首次运行前先修改服务端目录和账号密码。
- 如果客户端图标路径无效，可将 `pyqt5.py` 中的图标路径改为项目内的 `ftp.svg`。
- 测试上传下载前，确认服务端目录存在并具备读写权限。
- 如果在本机测试，可将客户端登录地址改为 `127.0.0.1`。
- 对外开放 FTP 服务时，应避免使用示例密码，并限制用户目录权限。

## 后续优化方向

- 将服务端地址、端口、账号和目录改为配置文件管理。
- 为上传、下载和删除操作增加异常提示。
- 修复 GUI 中硬编码的图标路径。
- 增加目录创建、重命名、进度条和断点续传能力。
- 增加 README 截图和使用演示。

## 仓库地址

https://github.com/siberiagroundhog/FTP
