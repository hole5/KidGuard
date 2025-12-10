# Landing Page 管理后台使用说明

## 功能概述

这是一个专门用于管理 `index.html` 主页的后台系统，可以实时编辑和更新主页内容。

## 访问方式

1. **确保后端服务运行**
   ```bash
   cd kidguard-config-backend
   npm run dev
   ```

2. **访问管理后台**
   - 直接访问：`http://localhost:3000/KidGuard/landing-page/admin.html`
   - 或通过后端服务：`http://localhost:3000/landing-page/admin.html`（如果配置了静态文件服务）

3. **登录认证**
   - 需要先登录管理后台获取 Token
   - 访问 `http://localhost:3000/admin.html` 登录
   - Token 会自动保存到 localStorage

## API 端点

### 获取配置
```
GET /api/v1/landing-page/config
Headers: Authorization: Bearer {token}
```

### 保存配置
```
POST /api/v1/landing-page/config
Headers: 
  Authorization: Bearer {token}
  Content-Type: application/json
Body: {配置对象}
```

## 功能模块

### 1. 主页内容管理
- Hero 区域：标题、描述、标签语
- 特性标签：5个特性标签编辑

### 2. 视频设置
- 视频 URL
- 封面图片
- 播放参数（自动播放、静音、循环）

### 3. 下载链接
- 家长端：APK、更新日志、二维码
- 儿童端：APK、安装指引、二维码

### 4. 定价信息
- 个人/家庭订阅价格
- 设备扩展包价格

### 5. 协议内容
- 用户协议
- 隐私政策

### 6. 多语言管理
- 中文翻译
- 英文翻译

### 7. 主题设置
- 颜色配置（主色调、背景色、文本色等）

## 使用流程

1. **登录系统**
   - 访问管理后台登录页面
   - 输入管理员账号密码

2. **编辑内容**
   - 选择左侧菜单进入对应模块
   - 修改表单内容
   - 点击"保存更改"按钮

3. **预览效果**
   - 点击右下角预览按钮
   - 在新窗口查看主页效果

4. **备份配置**
   - 点击导出按钮下载 JSON 配置文件
   - 需要时可以通过导入功能恢复

## 注意事项

1. **文件备份**
   - 每次保存时会自动创建备份文件（`.backup.{timestamp}`）
   - 备份文件保存在 `index.html` 同目录

2. **权限要求**
   - 需要 `config:read` 权限查看配置
   - 需要 `config:write` 权限保存配置

3. **路径配置**
   - 默认路径：`KidGuard/landing-page/index.html`
   - 可通过环境变量 `LANDING_PAGE_PATH` 自定义路径

4. **浏览器兼容性**
   - 建议使用 Chrome、Edge 或 Firefox 最新版本
   - 需要启用 JavaScript

## 环境变量配置

在 `.env` 文件中添加：

```env
# Landing Page 路径（可选）
LANDING_PAGE_PATH=/path/to/landing-page/index.html
```

## 故障排除

### 问题：无法加载配置
- 检查后端服务是否运行
- 检查 Token 是否有效
- 检查文件路径是否正确

### 问题：保存失败
- 检查文件权限
- 检查磁盘空间
- 查看后端日志

### 问题：预览页面无变化
- 清除浏览器缓存
- 检查 HTML 文件是否已更新
- 确认保存操作成功

## 技术支持

如有问题，请查看：
- 后端日志：`kidguard-config-backend/logs/`
- API 文档：`kidguard-config-backend/docs/API_DOCUMENTATION.md`


