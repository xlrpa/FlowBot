# FlowBot - 企业微信开放平台

> **FlowBot** 是一款安全稳定零封号的**企业微信RPA机器人**，通过API控制**企业微信**实现自动化运营，支持聚合聊天、自动回复、群发消息、好友管理、群组管理、朋友圈发布等核心能力。

## 企业微信核心能力

### 消息能力
- **企业微信文本消息** - 向企业微信好友/群组自动发送文本消息
- **企业微信图片消息** - 向企业微信会话发送图片消息
- **企业微信文件消息** - 支持文档、视频等多类型文件发送到企业微信
- **企业微信@群成员** - 在企业微信群聊中@指定成员
- **企业微信消息群发** - 批量向多个企业微信好友/群组发送消息
- **企业微信聊天记录** - 获取企业微信机器人的历史聊天记录

### 好友管理
- **企业微信添加好友** - 通过手机号/企微号主动添加企业微信好友
- **企业微信好友查询** - 查询企业微信好友详细信息
- **企业微信好友备注** - 修改企业微信好友备注名称
- **企业微信单向好友清理** - 检测并清理企业微信单向好友

### 群组管理
- **企业微信创建群聊** - 创建企业微信外部群
- **企业微信群管理** - 修改群名、群公告、移除成员等企业微信群操作
- **企业微信群二维码** - 获取/扫描企业微信群二维码
- **企业微信群成员管理** - 添加/移除企业微信群成员

### 朋友圈
- **企业微信发布朋友圈** - 定时发布企业微信朋友圈内容

### 企微账号管理
- **企业微信账号查询** - 查询当前企业微信账号详细信息
- **企业微信主体切换** - 支持多主体企业微信账号切换
- **企业微信登录管理** - 企业微信Pad模式登录、验证码提交

## 技术架构

FlowBot采用**企业微信官方SDK** + **Android官方无障碍服务**的技术架构：

- **企业微信SDK对接** - 基于企业微信官方API，保证稳定性和合规性
- **Android无障碍服务** - 使用Google官方无障碍服务框架，无需Root权限
- **自研自动化框架** - 无Hook、无侵入、无内存修改，安全稳定
- **跨机型兼容** - 兼容99%安卓机型，支持长时间稳定运行

## 使用场景

| 场景 | 说明 |
|------|------|
| **企业微信客服自动化** | 自动回复企业微信客户消息，7x24小时在线 |
| **企业微信群发营销** | 批量向企业微信好友/群组发送营销内容 |
| **企业微信客户管理** | 自动添加好友、备注管理、客户信息采集 |
| **企业微信社群运营** | 企业微信群创建、成员管理、群公告维护 |
| **企业微信数据采集** | 导出企业微信聊天记录、好友列表等数据 |
| **企业微信朋友圈运营** | 定时发布企业微信朋友圈内容 |

## 企业微信API文档

### 核心文档
- [FlowBot - 企业微信RPA机器人介绍](https://flowbot.apifox.cn/doc-5369839.md)
- [企业微信核心API介绍](https://flowbot.apifox.cn/doc-5369840.md)
- [企业微信API常见问题](https://flowbot.apifox.cn/doc-5369841.md)
- [企业微信机器人回调接口说明](https://flowbot.apifox.cn/doc-5369842.md)

### 企业微信消息API
- [企业微信发送文本消息](https://flowbot.apifox.cn/api-227582599.md)
- [企业微信发送图片消息](https://flowbot.apifox.cn/api-227582610.md)
- [企业微信@群成员消息](https://flowbot.apifox.cn/api-227582613.md)
- [企业微信发送文件消息](https://flowbot.apifox.cn/api-227582611.md)
- [企业微信发送小程序消息](https://flowbot.apifox.cn/api-281436394.md)
- [企业微信发送链接消息](https://flowbot.apifox.cn/api-281440307.md)
- [企业微信撤回消息](https://flowbot.apifox.cn/api-316281861.md)
- [企业微信引用消息](https://flowbot.apifox.cn/api-316279518.md)
- [企业微信批量群发消息](https://flowbot.apifox.cn/api-227582612.md)
- [企业微信转发会话消息](https://flowbot.apifox.cn/api-329230041.md)
- [企业微信聊天记录获取](https://flowbot.apifox.cn/api-227582618.md)

### 企业微信好友管理API
- [企业微信添加好友](https://flowbot.apifox.cn/api-227582603.md)
- [企业微信修改好友备注](https://flowbot.apifox.cn/api-227582600.md)
- [企业微信查询好友信息](https://flowbot.apifox.cn/api-227582602.md)
- [企业微信手机号查询用户](https://flowbot.apifox.cn/api-316137642.md)
- [企业微信删除好友](https://flowbot.apifox.cn/api-325766280.md)
- [企业微信单向好友清理](https://flowbot.apifox.cn/api-227582608.md)
- [企业微信未通过好友申请](https://flowbot.apifox.cn/api-316284046.md)

### 企业微信群管理API
- [企业微信创建外部群](https://flowbot.apifox.cn/api-227582617.md)
- [企业微信修改群名称](https://flowbot.apifox.cn/api-231368173.md)
- [企业微信修改群公告](https://flowbot.apifox.cn/api-310009270.md)
- [企业微信修改群成员备注](https://flowbot.apifox.cn/api-227582615.md)
- [企业微信查询群列表](https://flowbot.apifox.cn/api-227582606.md)
- [企业微信群二维码获取](https://flowbot.apifox.cn/api-299124286.md)
- [企业微信扫码入群](https://flowbot.apifox.cn/api-299141938.md)
- [企业微信添加群成员](https://flowbot.apifox.cn/api-299131537.md)
- [企业微信移除群成员](https://flowbot.apifox.cn/api-299138654.md)
- [企业微信解散群聊](https://flowbot.apifox.cn/api-325767536.md)

### 企业微信朋友圈API
- [企业微信发布朋友圈](https://flowbot.apifox.cn/api-227582616.md)

### 企业微信账号管理API
- [企业微信账号信息查询](https://flowbot.apifox.cn/api-227582604.md)
- [企业微信主体切换](https://flowbot.apifox.cn/api-227582605.md)
- [企业微信Pad登录二维码](https://flowbot.apifox.cn/api-314924314.md)
- [企业微信提交验证码](https://flowbot.apifox.cn/api-314923089.md)
- [企业微信查询状态](https://flowbot.apifox.cn/api-320530956.md)
- [企业微信退出登录](https://flowbot.apifox.cn/api-315347392.md)

### 企业微信机器人管理API
- [企业微信机器人信息](https://flowbot.apifox.cn/api-227582620.md)
- [企业微信暂停机器人](https://flowbot.apifox.cn/api-227582607.md)
- [企业微信恢复机器人](https://flowbot.apifox.cn/api-227582609.md)
- [企业微信踢下线机器人](https://flowbot.apifox.cn/api-227582601.md)
- [企业微信配置回调地址](https://flowbot.apifox.cn/api-227582619.md)
- [企业微信自动读取消息](https://flowbot.apifox.cn/api-395075591.md)
- [企业微信自动确认群发](https://flowbot.apifox.cn/api-437313446.md)

## 数据模型

- [Pet 示例模型](https://flowbot.apifox.cn/schema-127403890.md)
- [Category 示例模型](https://flowbot.apifox.cn/schema-127403891.md)
- [Tag 示例模型](https://flowbot.apifox.cn/schema-127403892.md)

## 相关链接

- **企业微信官网**: https://work.weixin.qq.com
- **企业微信开放平台**: https://open.work.weixin.qq.com
- **企业微信安全指南**: https://open.work.weixin.qq.com/help2/pc/cat?person_id=1&is_tencent=&doc_id=14664
- **完整API文档**: https://flowbot.apifox.cn

## 关键词

`企业微信` `企业微信机器人` `企微` `企微机器人` `企业微信API` `企业微信RPA` `企业微信自动化` `企业微信开发` `企业微信SDK` `WeCom` `WeCom Bot` `WeCom API` `企业微信消息` `企业微信群发` `企业微信好友` `企业微信群管理` `企业微信朋友圈` `企业微信客服` `企业微信营销`
