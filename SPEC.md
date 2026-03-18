# 动漫交友论坛 - ANIFORUM

## 1. Concept & Vision

一个充满二次元氛围的动漫爱好者交友社区。设计融合了霓虹灯光与和风元素，营造出深夜追番的温馨感。用户可以分享自己喜爱的动漫、发布动态、结识同好，找到志同道合的朋友。整体氛围活泼但不吵闹，实用但不冰冷。

## 2. Design Language

### 色彩方案
- **Primary**: `#FF6B9D` (樱花粉 - 主按钮、强调)
- **Secondary**: `#7C5CFF` (紫罗兰 - 次要元素、标签)
- **Accent**: `#00D4AA` (薄荷绿 - 在线状态、成功提示)
- **Background**: `#0F0F1A` (深夜蓝黑 - 主背景)
- **Surface**: `#1A1A2E` (卡片背景)
- **Surface-light**: `#252540` (悬停状态)
- **Text-primary**: `#FFFFFF`
- **Text-secondary**: `#A0A0B8`

### 字体
- **标题**: "Noto Sans SC", sans-serif (700)
- **正文**: "Noto Sans SC", sans-serif (400)
- **装饰文字**: "Comic Neue", cursive

### 空间系统
- 基础单位: 8px
- 卡片圆角: 16px
- 按钮圆角: 24px
- 头像圆角: 50% (圆形)

### 动效哲学
- 页面切换: 淡入淡出 300ms ease
- 卡片悬停: scale(1.02) + box-shadow增强 200ms
- 按钮点击: scale(0.95) 100ms
- 弹窗: 从底部滑入 400ms cubic-bezier(0.16, 1, 0.3, 1)
- 加载动画: 脉冲呼吸效果

### 视觉资产
- 图标库: Lucide Icons (线性风格)
- 装饰: 樱花花瓣粒子动画、星星闪烁效果
- 头像默认: 动漫风格占位图

## 3. Layout & Structure

### 页面架构

#### 首页/动态广场
- 顶部导航栏 (固定)
- 搜索栏 + 发帖按钮
- 瀑布流式动态卡片
- 右侧边栏 (热门话题、在线用户)
- 底部标签栏 (移动端)

#### 个人主页
- 封面图 + 头像区
- 基础信息卡 (ID、签名、喜欢的动漫标签)
- 动态列表
- 好友列表
- 收藏/关注板块

#### 论坛板块
- 板块分类卡片
- 帖子列表 (支持排序)
- 帖子详情 + 评论

#### 消息中心
- 对话列表
- 聊天窗口

### 响应式策略
- Desktop (>1024px): 三栏布局
- Tablet (768-1024px): 两栏布局
- Mobile (<768px): 单栏 + 底部导航

## 4. Features & Interactions

### 用户系统
- **注册**: 用户名、密码、喜欢的动漫类型 (至少选3个标签)
- **登录**: 用户名 + 密码
- **个人资料**: 可编辑头像(预设)、昵称、签名、喜欢的动漫列表
- **访客浏览**: 无需登录可浏览，点赞需登录

### 动态发布
- 支持文字 + 图片 (最多9张)
- 可添加话题标签 (#番名#)
- 发布后显示在广场
- 支持删除自己的动态

### 互动功能
- **点赞**: 点击心形图标 +1，支持取消
- **评论**: 显示评论列表，支持回复
- **收藏**: 收藏感兴趣的帖子
- **关注**: 关注其他用户

### 站内消息
- 用户之间可互发消息
- 显示未读消息数量
- 消息列表按最近会话排序

### 论坛功能
- 板块按动漫类型分类
- 帖子支持置顶、精华标记
- 回复楼层显示
- 按时间/热度排序

## 5. Component Inventory

### 导航栏 (Navbar)
- Logo + 标题
- 搜索输入框
- 消息图标 + 未读数红点
- 用户头像下拉菜单
- 状态: 滚动时背景加深

### 动态卡片 (PostCard)
- 用户头像 + 昵称 + 发布时间
- 文字内容 (超出3行折叠)
- 图片网格 (1张单图/4格/9格布局)
- 话题标签
- 点赞/评论/分享按钮栏
- 状态: 默认、悬停(阴影增强)、加载中(骨架屏)

### 用户卡片 (UserCard)
- 头像 (圆形，带在线状态指示器)
- 昵称 + 签名
- 喜欢的动漫标签 (最多显示3个)
- 关注按钮
- 状态: 默认、已关注(按钮变灰)、悬停

### 按钮 (Button)
- Primary: 粉色渐变背景
- Secondary: 透明背景 + 紫色边框
- Ghost: 透明背景 + 文字色
- 状态: 默认、悬停(亮度+10%)、点击(scale 0.95)、禁用(opacity 0.5)

### 输入框 (Input)
- 圆角矩形
- 聚焦时边框高亮
- 错误状态: 红色边框 + 错误提示

### 标签 (Tag)
- 圆角胶囊形状
- 各分类不同颜色
- 可点击跳转筛选

### 弹窗 (Modal)
- 半透明黑色遮罩
- 白色圆角内容区
- 关闭按钮 (右上角X)
- 动画: 从底部滑入

### 空状态 (EmptyState)
- 装饰性插图
- 引导文案
- 操作按钮

## 6. Technical Approach

### 技术栈
- 纯前端: HTML5 + CSS3 + Vanilla JavaScript
- 无框架依赖，单文件实现
- LocalStorage 模拟数据持久化

### 数据模型

```javascript
// 用户
User {
  id: string,
  username: string,
  password: string (简化存储),
  nickname: string,
  avatar: number (1-20预设头像索引),
  bio: string,
  favoriteAnimes: string[],
  followers: string[],
  following: string[],
  createdAt: timestamp
}

// 动态
Post {
  id: string,
  userId: string,
  content: string,
  images: string[],
  tags: string[],
  likes: string[] (用户id数组),
  comments: Comment[],
  createdAt: timestamp
}

// 评论
Comment {
  id: string,
  userId: string,
  content: string,
  createdAt: timestamp
}

// 消息
Message {
  id: string,
  fromId: string,
  toId: string,
  content: string,
  read: boolean,
  createdAt: timestamp
}
```

### 路由设计 (Hash路由)
- `#/` - 首页/动态广场
- `#/profile/:userId` - 个人主页
- `#/forum` - 论坛板块
- `#/forum/:category` - 板块帖子列表
- `#/post/:postId` - 帖子详情
- `#/messages` - 消息中心
- `#/settings` - 设置页

### 关键实现
- 模块化组件函数
- 事件委托处理动态元素
- 防抖搜索
- 图片懒加载
- 虚拟滚动 (大数据列表)
