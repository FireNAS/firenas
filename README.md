# FireNAS

## 客户端

### 开发语言

- Dart
- Kotlin
- JavaScript

### 前端框架

- flutter 用于跨平台客户端开发
- Compose Multiplatform 给 flutter 提供调用不同平台的原生接口
- SolidJS 网页端开发

## 服务端

### 开发语言

- Go

### 数据库

- Sqlite

- Postgresql + Citus 可扩展数据库集群

- ClickHouse 提供数据分析支持

### 消息平台

- NSQ 轻量消息平台

### 文件系统

- Ceph 分布式文件系统

## 构建

- makefile

## 服务端项目结构

目前使用破产版领域模型，业务稳定后可能会添加 CQRS+事件溯源+聚合。

### Application

应用层

- 接收请求DTO，或响应DTO。
- 简单的数据校验。
- 可组合不同的service。
- 对service返回的models转换成DTO，或调用service把DTO转换为model

### Services

领域层

- 实现核心业务
- 可组合不同的repository

### Models

领域模型

- 作为application与service的交互模型
- 作为repository与service的交互模型

### DTO

数据传输对象

- 用于定义如何通过网络发送的数据，例如：http 请求的数据或者响应的数据。
- 具有序列化功能。例如：对响应数据序列化成 json，对请求数据序列化成对象。
- [ 可选 ]请求数据需具有数据校验功能。

### Repositories

数据源适配层

- 抽象对数据源的操作，对不同的数据源统一接口。
- 实现对数据源的操作，例如：数据库读写，http，rpc 等。
