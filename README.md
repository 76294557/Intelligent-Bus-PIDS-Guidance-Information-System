# 智能公交PIDS导向信息系统 - 项目介绍

## 项目概述

**智能公交PIDS（Passenger Information Display System）导向信息系统** 是一套完整的公交信息显示解决方案，用于公交站台和车内显示屏实时展示公交信息。

---

## 系统架构

项目采用前后端分离架构，包含三个核心子系统：

| 子系统 | 技术栈 | 用途 |
|--------|--------|------|
| **pids-frontend** | Vue 3 + TypeScript + Vite | 前端展示端（PIDS大屏） |
| **pids-admin** | Vue 3 + TypeScript + Element Plus + Vite | 管理后台 |
| **pids-server** | Node.js + Express + TypeScript | 后端服务 |
| **database** | MySQL 8.0 | 数据存储 |

---

## 核心功能

### 前端展示端（PIDS大屏）
- 📍 **站点时间轴** - 横向排列显示线路所有站点
- 🎯 **当前站点高亮** - 红色呼吸灯效果标识当前站点
- 🚌 **车辆位置标记** - 实时显示车辆在线路中的位置
- ⏱️ **到站倒计时** - 显示下一班车预计到达时间
- 📢 **滚动公告** - 从右向左匀速滚动显示通知

### 管理后台
- 🛤️ **线路管理** - 线路增删改查、站点顺序配置
- 🚏 **站点管理** - 站点信息编辑、坐标设置
- 🚌 **车辆管理** - 车辆信息、线路绑定
- 📅 **排班管理** - 发车时刻表设置
- 📢 **公告管理** - 公告发布、有效期设置
- 🔧 **设备管理** - PIDS设备注册、状态监控
- 📊 **实时监控** - 车辆位置地图展示、运行状态

---

## 数据库设计

核心数据表结构：

| 表名 | 说明 |
|------|------|
| `lines` | 线路表（线路编号、名称、起点/终点站） |
| `stations` | 站点表（站点名称、坐标、地址） |
| `line_stations` | 线路站点关联表（站点顺序、距离） |
| `buses` | 车辆表（车牌号、所属线路、当前位置） |
| `announcements` | 公告表（标题、内容、有效期） |
| `devices` | 设备表（设备编码、类型、状态） |
| `users` | 用户表（管理员账号） |

---

## 技术亮点

- ⚡ **实时通信** - 基于 Socket.io 实现 WebSocket 实时推送
- 🎨 **大屏优化** - 针对PIDS显示屏定制的深色主题UI
- 📱 **响应式布局** - 适配16:9大屏显示比例
- 🔒 **权限管理** - JWT认证 + 角色权限控制
- 🔄 **热重载** - 开发环境支持代码热更新

---

## 快速启动

```bash
# 1. 初始化数据库
mysql -u root -p < database/schema.sql
mysql -u root -p < database/seeds/init_data.sql

# 2. 启动后端服务
cd pids-server && npm run dev

# 3. 启动前端展示端
cd pids-frontend && npm run dev

# 4. 启动管理后台
cd pids-admin && npm run dev
```

**访问地址：**
- 前端展示端: http://localhost:5173
- 管理后台: http://localhost:5174
- 后端API: http://localhost:3000/api

**默认账号：** admin / admin123

---

## 项目状态

根据开发计划，项目已完成：
- ✅ 基础架构搭建
- ✅ 数据库设计
- ✅ 管理后台核心功能
- ⏳ PIDS展示端（开发中）
- ⏳ 实时WebSocket推送（开发中）
