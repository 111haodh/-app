# 康伴儿 - 老年人智能用药管理助手

## 项目简介

康小助是一款专为老年人设计的用药管理应用，帮助老年人按时服药、管理健康记录，并提供AI健康助手陪伴功能。

## 技术架构

```
药小助/
├── 前端 (React + TypeScript + Vite)
│   ├── App.tsx              # 主应用组件
│   ├── components/          # UI 组件
│   ├── services/            # API 服务层
│   └── types.ts             # 类型定义
│
├── 后端 (Node.js + Express)
│   └── server/
│       ├── src/
│       │   ├── index.ts     # 服务入口
│       │   ├── routes/      # API 路由
│       │   ├── services/    # OAuth 服务
│       │   ├── middleware/  # 认证中间件
│       │   └── config/      # 配置文件
│       └── package.json
│
└── 数据库 (Supabase PostgreSQL)
    └── supabase/schema.sql  # 数据库结构
```

## 快速开始

### 1. 安装前端依赖

```bash
npm install
```

### 2. 安装后端依赖

```bash
cd server
npm install
```

### 3. 配置环境变量

复制环境变量模板并填写配置：

**前端 (.env.local)**:
```bash
VITE_API_URL=http://localhost:3001/api
VITE_SUPABASE_URL=your-supabase-url
VITE_SUPABASE_ANON_KEY=your-anon-key
```

**后端 (server/.env)**:
```bash
# 复制 .env.example 为 .env
cp server/.env.example server/.env
# 然后编辑填写 Supabase 和 OAuth 配置
```

### 4. 设置数据库

在 Supabase 控制台的 SQL Editor 中运行 `supabase/schema.sql`

### 5. 启动开发服务器

**启动后端**:
```bash
cd server
npm run dev
```

**启动前端** (新终端):
```bash
npm run dev
```

## 功能特性

### 🏠 首页看板
- 今日服药提醒
- 快捷操作按钮
- 紧急呼叫功能

### 💊 智能药箱
- 药品信息管理
- 库存追踪与预警
- OCR 识别药品

### ❤️ 健康数据
- 血压/血糖/心率记录
- 数据可视化图表
- 症状记录

### 👤 个人中心
- 用户信息管理
- 监护人设置
- 微信/QQ 账号绑定

### 🤖 AI 健康助手
- 智能语音交互
- 健康问答陪聊
- 服药语音提醒

## OAuth 登录配置

### 微信登录
1. 注册 [微信开放平台](https://open.weixin.qq.com) 账号
2. 创建移动应用/网站应用
3. 获取 AppID 和 AppSecret
4. 填入 `.env` 配置

### QQ 登录
1. 注册 [QQ 互联平台](https://connect.qq.com) 账号
2. 创建应用
3. 获取 App ID 和 App Key
4. 填入 `.env` 配置

## API 接口文档

### 认证接口
- `POST /api/auth/demo-login` - 演示登录
- `GET /api/auth/wechat/url` - 获取微信授权URL
- `POST /api/auth/wechat/callback` - 微信登录回调
- `GET /api/auth/qq/url` - 获取QQ授权URL
- `POST /api/auth/qq/callback` - QQ登录回调
- `GET /api/auth/me` - 获取当前用户
- `PUT /api/auth/me` - 更新用户信息

### 药品接口
- `GET /api/medications` - 获取药品列表
- `POST /api/medications` - 添加药品
- `PUT /api/medications/:id` - 更新药品
- `POST /api/medications/:id/take` - 标记已服用
- `DELETE /api/medications/:id` - 删除药品

### 健康记录接口
- `GET /api/health` - 获取健康记录
- `POST /api/health` - 添加健康记录
- `GET /api/health/statistics` - 获取统计数据
- `DELETE /api/health/:id` - 删除记录

## 开发说明

- 前端使用 Vite 构建，支持热更新
- 后端使用 tsx 运行 TypeScript
- 建议使用 Node.js 18+ 版本

## 许可证

MIT License
