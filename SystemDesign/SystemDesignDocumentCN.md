# System Design Document


描述项目的技术方案和技术选型。

目前项目分三个部分
- vault ai client bot(Alis:VAC):
  - WinForms(C#) + react.js
    - 用于在 vault 中实现侧边栏聊天机器人的功能
- vault ai server api(Alis:VAS):
  - fastAPI(python) + LangChain(ollama/azure openai)
      - 阅读现有的 api description，使得 ai 理解起来更加容易（用来支持 VAC）。
- vault api(Alis:VA):
    - 规范现有的 api description，使得 ai 理解起来更加容易（用来支持 VAS）。

技术选型
servers [fastAPI(python) + LangChain(ollama/azure openai)] + client[WinForms(C#) + react.js]
- servers
  - OpenAI 官方 SDK 是 Python，此开发语言首选 Python
  - FastAPI 是 Python 语言编写的高性能的现代化 Web 框架
  - LangChain 是 AI 应用开发的主流框架，能方便的组合各种 AI 技术进行应用开发
- client
  - vault 是基于 .NET 的产品，所以客户端开发语言选择 C#
  - WinForms 是 .NET 的 GUI 开发框架，适合快速开发桌面应用
  - react.js 是前端开发的主流框架，适合开发 Web 应用

## 1. 引言
### 1.1 项目背景
简要描述项目的背景和目标。

### 1.2 项目范围
描述项目的范围和边界。

## 2. 技术选型
### 2.1 编程语言
选择的编程语言及其原因。

### 2.2 框架和库
选择的框架和库及其原因。

### 2.3 工具和平台
选择的开发工具和平台及其原因。

## 3. 系统架构
### 3.1 架构概述
描述系统的整体架构。

### 3.2 模块划分
描述系统的模块和组件划分。

## 4. 详细设计
### 4.1 模块1
详细描述模块1的设计，包括类图、时序图等。

### 4.2 模块2
详细描述模块2的设计，包括类图、时序图等。

## 5. 数据库设计
### 5.1 ER图
描述数据库的ER图。

### 5.2 表结构
描述数据库的表结构。

## 6. 接口设计
### 6.1 内部接口
描述系统内部的接口设计。

### 6.2 外部接口
描述系统与外部系统的接口设计。

## 7. 安全设计
### 7.1 认证
描述系统的认证设计。

### 7.2 授权
描述系统的授权设计。

### 7.3 数据加密
描述系统的数据加密设计。

## 8. 性能设计
### 8.1 性能优化
描述系统的性能优化设计。

### 8.2 负载均衡
描述系统的负载均衡设计。

## 9. 技术难点和解决方案
### 9.1 技术难点
描述项目可能遇到的技术难点和挑战。

### 9.2 解决方案
描述针对技术难点的解决方案。