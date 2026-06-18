# FlowBot 企业微信自动化开发指南

> **FlowBot** 是一款安全稳定的**企业微信RPA机器人**，基于Android官方无障碍服务，通过API控制**企业微信**实现自动化运营。本文档详细介绍**企业微信自动化**的开发流程和最佳实践。

## 目录

- [企业微信自动化简介](#企业微信自动化简介)
- [环境准备](#环境准备)
- [企业微信API接入](#企业微信api接入)
- [企业微信消息自动化](#企业微信消息自动化)
- [企业微信好友管理](#企业微信好友管理)
- [企业微信群管理](#企业微信群管理)
- [企业微信朋友圈](#企业微信朋友圈)
- [企业微信机器人配置](#企业微信机器人配置)
- [企业微信RPA最佳实践](#企业微信rpa最佳实践)

---

## 企业微信自动化简介

### 什么是企业微信自动化？

**企业微信自动化**是指通过技术手段自动执行**企业微信**的日常操作，包括：

- **企业微信消息自动发送** - 批量发送企业微信文本、图片、文件消息
- **企业微信自动回复** - 根据关键词自动回复企业微信好友消息
- **企业微信好友自动添加** - 批量添加企业微信好友
- **企业微信群自动管理** - 自动创建企业微信群、管理群成员
- **企业微信朋友圈定时发布** - 定时发布企业微信朋友圈内容

### 为什么选择 FlowBot？

| 特性 | 说明 |
|------|------|
| **企业微信官方SDK** | 基于企业微信官方API，稳定可靠 |
| **零封号风险** | 使用Android无障碍服务，非HOOK注入 |
| **无需Root** | 手机无需破解Root权限 |
| **跨机型兼容** | 兼容99%安卓机型 |
| **7x24小时运行** | 支持企业微信机器人长时间稳定运行 |

---

## 环境准备

### 1. 企业微信账号准备

- 注册**企业微信**账号并完成实名认证
- 确保企业微信账号状态正常，无封禁记录
- 准备一台可联网的安卓手机

### 2. FlowBot 安装

```bash
# 下载 FlowBot 企业微信机器人APP
# 下载地址: https://www.xcxwo.com/XhAZ9Wbg
```

### 3. 企业微信版本要求

目前支持的企业微信版本：
- 企业微信 4.1.32
- 企业微信 4.1.30
- 企业微信 4.1.28
- 企业微信 4.1.26

### 4. 权限配置

在手机设置中授予 FlowBot 以下权限：
- **无障碍服务权限** - 用于企业微信自动化操作
- **悬浮窗权限** - 用于企业微信机器人状态显示
- **后台运行权限** - 确保企业微信机器人持续运行

---

## 企业微信API接入

### 获取企业微信机器人ID

1. 打开 FlowBot APP
2. 按照提示绑定企业微信机器人 robotId
3. 记录您的 robotId 用于API调用

### 企业微信API基础配置

```javascript
// 企业微信API配置
const config = {
    robotId: 'YOUR_ROBOT_ID',  // 企业微信机器人ID
    baseUrl: 'https://api.flowbot.cn',  // 企业微信API地址
};

// 企业微信API请求示例
async function sendWeComMessage(receiver, content) {
    const response = await fetch(`${baseUrl}/api/v1/wecom/send`, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'Authorization': `Bearer ${config.robotId}`,
        },
        body: JSON.stringify({
            receiver: receiver,  // 企业微信接收人
            content: content,    // 消息内容
            msg_type: 'text',    // 企业微信消息类型
        }),
    });
    return response.json();
}
```

### 企业微信消息类型

| 类型 | 说明 | API接口 |
|------|------|---------|
| text | 企业微信文本消息 | /api/v1/wecom/send/text |
| image | 企业微信图片消息 | /api/v1/wecom/send/image |
| file | 企业微信文件消息 | /api/v1/wecom/send/file |
| video | 企业微信视频消息 | /api/v1/wecom/send/video |
| card | 企业微信名片消息 | /api/v1/wecom/send/card |
| link | 企业微信链接消息 | /api/v1/wecom/send/link |

---

## 企业微信消息自动化

### 发送企业微信文本消息

```javascript
// 企业微信发送文本消息API
// POST /api/v1/wecom/send/text

const message = {
    robot_id: 'YOUR_ROBOT_ID',
    receiver: '企业微信好友昵称',
    content: '这是一条企业微信自动发送的消息',
};

// 调用企业微信发送消息API
const result = await wecomAPI.sendText(message);
console.log('企业微信消息发送结果:', result);
```

### 发送企业微信图片消息

```javascript
// 企业微信发送图片消息API
// POST /api/v1/wecom/send/image

const imageMessage = {
    robot_id: 'YOUR_ROBOT_ID',
    receiver: '企业微信好友昵称',
    image_url: 'https://example.com/image.jpg',  // 企业微信图片URL
};

// 调用企业微信发送图片API
const result = await wecomAPI.sendImage(imageMessage);
```

### 企业微信消息群发

```javascript
// 企业微信群发消息API
// POST /api/v1/wecom/batch_send

const batchMessage = {
    robot_id: 'YOUR_ROBOT_ID',
    receivers: ['企业微信好友1', '企业微信好友2', '企业微信好友3'],
    content: '企业微信群发消息内容',
    interval: 1000,  // 企业微信消息发送间隔(毫秒)
};

// 调用企业微信群发API
const result = await wecomAPI.batchSend(batchMessage);
```

### 企业微信自动回复

```javascript
// 企业微信自动回复配置
const autoReplyConfig = {
    robot_id: 'YOUR_ROBOT_ID',
    rules: [
        {
            keyword: '价格',  // 企业微信消息关键词
            reply: '您好，这是企业微信自动回复：请查看价格表...',
        },
        {
            keyword: '咨询',
            reply: '您好，这是企业微信自动回复：请问有什么可以帮您？',
        },
        {
            keyword: '人工',
            reply: '企业微信自动回复：正在为您转接人工客服...',
        },
    ],
    default_reply: '企业微信自动回复：感谢您的消息，我们会尽快回复！',
};

// 企业微信自动回复监听
wecomAPI.onMessage(async (message) => {
    const reply = findReply(message.content, autoReplyConfig.rules);
    await wecomAPI.sendText({
        robot_id: 'YOUR_ROBOT_ID',
        receiver: message.sender,
        content: reply || autoReplyConfig.default_reply,
    });
});
```

---

## 企业微信好友管理

### 企业微信添加好友

```javascript
// 企业微信添加好友API
// POST /api/v1/wecom/friend/add

const addFriendParams = {
    robot_id: 'YOUR_ROBOT_ID',
    phone: '13800138000',  // 企业微信好友手机号
    verify_msg: '您好，我是企业微信机器人',  // 企业微信验证消息
};

// 调用企业微信添加好友API
const result = await wecomAPI.addFriend(addFriendParams);
```

### 企业微信批量添加好友

```javascript
// 企业微信批量添加好友
const phones = ['13800138001', '13800138002', '13800138003'];

for (const phone of phones) {
    await wecomAPI.addFriend({
        robot_id: 'YOUR_ROBOT_ID',
        phone: phone,
        verify_msg: '企业微信自动添加好友',
    });
    
    // 企业微信添加好友间隔，避免频繁操作
    await sleep(5000);
}
```

### 企业微信好友查询

```javascript
// 企业微信好友查询API
// GET /api/v1/wecom/friend/info

const friendInfo = await wecomAPI.getFriendInfo({
    robot_id: 'YOUR_ROBOT_ID',
    nickname: '企业微信好友昵称',
});

console.log('企业微信好友信息:', friendInfo);
```

### 企业微信单向好友清理

```javascript
// 企业微信单向好友检测API
// GET /api/v1/wecom/friend/check_one_way

const oneWayFriends = await wecomAPI.checkOneWayFriends({
    robot_id: 'YOUR_ROBOT_ID',
});

console.log('企业微信单向好友列表:', oneWayFriends);

// 企业微信删除单向好友
for (const friend of oneWayFriends) {
    await wecomAPI.deleteFriend({
        robot_id: 'YOUR_ROBOT_ID',
        nickname: friend.nickname,
    });
}
```

---

## 企业微信群管理

### 企业微信创建群聊

```javascript
// 企业微信创建群聊API
// POST /api/v1/wecom/group/create

const createGroupParams = {
    robot_id: 'YOUR_ROBOT_ID',
    group_name: '企业微信自动化测试群',
    members: ['企业微信好友1', '企业微信好友2', '企业微信好友3'],
};

// 调用企业微信创建群聊API
const group = await wecomAPI.createGroup(createGroupParams);
console.log('企业微信群创建成功:', group);
```

### 企业微信群成员管理

```javascript
// 企业微信添加群成员API
// POST /api/v1/wecom/group/add_member

await wecomAPI.addGroupMember({
    robot_id: 'YOUR_ROBOT_ID',
    group_name: '企业微信群名称',
    members: ['新成员1', '新成员2'],
});

// 企业微信移除群成员API
// POST /api/v1/wecom/group/remove_member

await wecomAPI.removeGroupMember({
    robot_id: 'YOUR_ROBOT_ID',
    group_name: '企业微信群名称',
    member: '要移除的成员',
});
```

### 企业微信群公告管理

```javascript
// 企业微信修改群公告API
// POST /api/v1/wecom/group/announcement

await wecomAPI.updateGroupAnnouncement({
    robot_id: 'YOUR_ROBOT_ID',
    group_name: '企业微信群名称',
    announcement: '这是企业微信群公告内容',
});
```

### 企业微信群消息发送

```javascript
// 企业微信群发送消息API
// POST /api/v1/wecom/group/send

await wecomAPI.sendGroupMessage({
    robot_id: 'YOUR_ROBOT_ID',
    group_name: '企业微信群名称',
    content: '企业微信群发消息内容',
});
```

---

## 企业微信朋友圈

### 企业微信发布朋友圈

```javascript
// 企业微信发布朋友圈API
// POST /api/v1/wecom/moments/publish

const momentsContent = {
    robot_id: 'YOUR_ROBOT_ID',
    content: '企业微信朋友圈文字内容',
    images: [
        'https://example.com/image1.jpg',
        'https://example.com/image2.jpg',
    ],
};

// 调用企业微信发布朋友圈API
const result = await wecomAPI.publishMoments(momentsContent);
```

### 企业微信定时发布朋友圈

```javascript
// 企业微信定时发布朋友圈
const schedule = {
    robot_id: 'YOUR_ROBOT_ID',
    content: '企业微信定时朋友圈内容',
    images: ['https://example.com/image.jpg'],
    publish_time: '2024-01-01 10:00:00',  // 企业微信发布时间
};

// 调用企业微信定时发布API
await wecomAPI.scheduleMoments(schedule);
```

---

## 企业微信机器人配置

### 企业微信机器人信息查询

```javascript
// 企业微信机器人信息API
// GET /api/v1/wecom/robot/info

const robotInfo = await wecomAPI.getRobotInfo({
    robot_id: 'YOUR_ROBOT_ID',
});

console.log('企业微信机器人信息:', robotInfo);
```

### 企业微信机器人回调配置

```javascript
// 企业微信机器人回调地址配置
// POST /api/v1/wecom/robot/callback

await wecomAPI.setCallback({
    robot_id: 'YOUR_ROBOT_ID',
    callback_url: 'https://your-server.com/webhook/wecom',
});

// 企业微信消息回调处理
app.post('/webhook/wecom', (req, res) => {
    const message = req.body;
    
    // 处理企业微信消息
    switch (message.msg_type) {
        case 'text':
            handleTextMessage(message);
            break;
        case 'image':
            handleImageMessage(message);
            break;
        // 更多企业微信消息类型...
    }
    
    res.json({ code: 0, msg: 'success' });
});
```

### 企业微信机器人暂停与恢复

```javascript
// 企业微信暂停机器人API
// POST /api/v1/wecom/robot/pause

await wecomAPI.pauseRobot({
    robot_id: 'YOUR_ROBOT_ID',
});

// 企业微信恢复机器人API
// POST /api/v1/wecom/robot/resume

await wecomAPI.resumeRobot({
    robot_id: 'YOUR_ROBOT_ID',
});
```

---

## 企业微信RPA最佳实践

### 1. 企业微信消息发送频率控制

```javascript
// 企业微信消息发送限流器
class WeComRateLimiter {
    constructor(maxPerSecond = 1) {
        this.maxPerSecond = maxPerSecond;
        this.queue = [];
        this.processing = false;
    }
    
    async add(message) {
        this.queue.push(message);
        if (!this.processing) {
            await this.process();
        }
    }
    
    async process() {
        this.processing = true;
        while (this.queue.length > 0) {
            const message = this.queue.shift();
            await wecomAPI.sendText(message);
            await sleep(1000 / this.maxPerSecond);
        }
        this.processing = false;
    }
}

// 使用限流器发送企业微信消息
const limiter = new WeComRateLimiter(1);  // 每秒1条企业微信消息
```

### 2. 企业微信好友添加策略

```javascript
// 企业微信好友添加策略配置
const addFriendStrategy = {
    daily_limit: 50,           // 企业微信每日添加上限
    interval: 10000,           // 企业微信添加间隔(毫秒)
    verify_messages: [         // 企业微信验证消息模板
        '您好，我是{company}的{name}',
        '企业微信好友申请，来自{company}',
    ],
    work_hours: {              // 企业微信工作时间
        start: 9,
        end: 18,
    },
};
```

### 3. 企业微信群管理规范

```javascript
// 企业微信群管理配置
const groupManagement = {
    max_members: 200,          // 企业微信群最大成员数
    auto_welcome: true,        // 企业微信群自动欢迎语
    welcome_message: '欢迎加入企业微信群！',
    auto_cleanup: true,        // 企业微信群自动清理不活跃成员
    inactive_days: 30,         // 不活跃天数阈值
};
```

### 4. 企业微信朋友圈发布技巧

```javascript
// 企业微信朋友圈发布策略
const momentsStrategy = {
    // 企业微信最佳发布时间
    best_times: [
        '08:00',  // 早上上班
        '12:00',  // 中午休息
        '18:00',  // 下班时间
        '21:00',  // 晚间活跃
    ],
    
    // 企业微信朋友圈内容类型
    content_types: [
        'product',   // 企业微信产品推广
        'knowledge', // 企业微信知识分享
        'activity',  // 企业微信活动通知
    ],
    
    // 企业微信朋友圈配图规范
    image_rules: {
        max_count: 9,           // 最多9张图
        min_resolution: '800x800',  // 最小分辨率
    },
};
```

---

## 企业微信自动化场景

### 场景一：企业微信智能客服

```javascript
// 企业微信智能客服系统
class WeComCustomerService {
    constructor(robotId) {
        this.robotId = robotId;
        this.knowledgeBase = new Map();
    }
    
    // 企业微信自动回复
    async autoReply(message) {
        const answer = this.searchKnowledge(message.content);
        await wecomAPI.sendText({
            robot_id: this.robotId,
            receiver: message.sender,
            content: answer || '企业微信客服：正在为您转接人工...',
        });
    }
    
    // 知识库查询
    searchKnowledge(query) {
        // 企业微信关键词匹配逻辑
        for (const [keyword, answer] of this.knowledgeBase) {
            if (query.includes(keyword)) {
                return answer;
            }
        }
        return null;
    }
}
```

### 场景二：企业微信社群运营

```javascript
// 企业微信社群运营机器人
class WeComGroupOperator {
    constructor(robotId) {
        this.robotId = robotId;
    }
    
    // 企业微信群定时推送
    async scheduledPush(groupName, content, schedule) {
        // 定时向企业微信群推送内容
        cron.schedule(schedule, async () => {
            await wecomAPI.sendGroupMessage({
                robot_id: this.robotId,
                group_name: groupName,
                content: content,
            });
        });
    }
    
    // 企业微信群活动管理
    async manageActivity(groupName, activity) {
        // 发送企业微信群活动通知
        await wecomAPI.sendGroupMessage({
            robot_id: this.robotId,
            group_name: groupName,
            content: `企业微信活动通知：${activity.name}\n时间：${activity.time}\n地点：${activity.location}`,
        });
    }
}
```

### 场景三：企业微信数据采集

```javascript
// 企业微信数据采集系统
class WeComDataCollector {
    constructor(robotId) {
        this.robotId = robotId;
    }
    
    // 采集企业微信聊天记录
    async collectChatHistory(contact) {
        const history = await wecomAPI.getChatHistory({
            robot_id: this.robotId,
            contact: contact,
        });
        return history;
    }
    
    // 导出企业微信好友列表
    async exportFriendList() {
        const friends = await wecomAPI.getFriendList({
            robot_id: this.robotId,
        });
        return friends;
    }
}
```

---

## 常见问题

### Q1: 企业微信机器人会被封号吗？

A: FlowBot 使用 Android 官方无障碍服务，**非HOOK注入**，符合工信部政策要求，正常使用不会导致企业微信封号。

### Q2: 企业微信API调用频率有限制吗？

A: 建议企业微信消息发送频率控制在每秒1条，企业微信好友添加每日不超过50人。

### Q3: 支持哪些企业微信版本？

A: 目前支持企业微信 4.1.26、4.1.28、4.1.30、4.1.32 版本。

### Q4: 企业微信机器人如何保持长时间运行？

A: 需要：
1. 手机保持充电状态
2. 关闭企业微信省电模式
3. 授予 FlowBot 后台运行权限

---

## 技术支持

- **企业微信官方文档**: https://work.weixin.qq.com
- **企业微信开放平台**: https://open.work.weixin.qq.com
- **FlowBot API文档**: https://flowbot.apifox.cn
- **企业微信安全指南**: https://open.work.weixin.qq.com/help2/pc/cat?person_id=1&is_tencent=&doc_id=14664

---

## 关键词

`企业微信` `企业微信机器人` `企业微信RPA` `企业微信自动化` `企业微信开发` `企业微信API` `企业微信SDK` `企微` `企微机器人` `WeCom` `WeCom Bot` `WeCom API` `企业微信消息` `企业微信群发` `企业微信好友` `企业微信群管理` `企业微信朋友圈` `企业微信客服` `企业微信营销` `企业微信数据采集` `企业微信智能客服` `企业微信社群运营` `Android自动化` `无障碍服务`
