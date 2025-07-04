# 微信爬虫工具 - 可执行版本使用说明

## 📦 打包结果

本项目已成功打包为可执行文件，包含两个版本：

### macOS 版本
- **应用程序**：`dist/微信爬虫工具.app` （推荐）
- **可执行文件**：`dist/微信爬虫工具` （41MB）

### Windows 版本
- 如需Windows版本，请在Windows系统上运行：
  ```bash
  pyinstaller build_exe.spec
  ```

## 🚀 使用方法

### macOS 系统

#### 方法一：使用.app应用程序（推荐）
1. 双击 `微信爬虫工具.app` 启动应用
2. 如果系统提示"无法验证开发者"：
   - 右键点击应用 → 选择"打开"
   - 在弹窗中点击"打开"确认
   - 或在系统偏好设置 → 安全性与隐私 → 通用 → 点击"仍要打开"

#### 方法二：使用命令行
```bash
# 进入dist目录
cd dist

# 直接运行可执行文件
./微信爬虫工具
```

### Windows 系统
1. 双击 `微信爬虫工具.exe` 启动应用
2. 如果Windows Defender提示，选择"仍要运行"

## ✨ 功能特性

### 🔐 自动登录
- 一键获取微信公众号平台token和cookie
- 自动化浏览器登录，无需手动操作
- 登录信息本地缓存，避免重复登录

### 📊 批量爬取
- 支持多个公众号同时爬取
- 自定义时间范围筛选
- 智能进度显示和状态监控
- 多线程处理，提升爬取效率

### 💾 数据管理
- SQLite数据库存储
- 支持文章搜索和筛选
- 数据导出为Markdown格式
- 智能查询和数据分析

### 🎨 图形界面
- 现代化PyQt5界面设计
- 直观的操作流程
- 实时日志显示
- 专业的应用图标

## 🔧 系统要求

### macOS
- macOS 10.13 或更高版本
- 64位系统
- 500MB 可用存储空间

### Windows
- Windows 10 或更高版本
- 64位系统
- 500MB 可用存储空间

## 📂 文件结构

```
dist/
├── 微信爬虫工具.app/          # macOS应用程序包
│   └── Contents/
│       ├── MacOS/             # 可执行文件
│       ├── Resources/         # 资源文件
│       ├── Frameworks/        # 依赖库
│       └── Info.plist         # 应用信息
└── 微信爬虫工具               # 可执行文件
```

## ⚠️ 注意事项

### 安全性
- 首次运行时系统可能提示安全警告，这是正常现象
- 应用已包含所有必要的依赖，无需安装Python环境
- 建议从官方渠道下载使用

### 使用限制
- 请遵守微信公众号平台使用条款
- 合理设置爬取间隔，避免过于频繁的请求
- 仅用于合法的数据收集和研究用途

### 性能优化
- 应用大小约41MB，包含完整的Python运行环境
- 首次启动可能需要几秒钟时间
- 建议关闭不必要的安全软件监控以提升性能

## 🐛 故障排除

### 应用无法启动
1. **macOS**：检查系统版本是否符合要求
2. **权限问题**：确保应用有执行权限
3. **防火墙**：确保防火墙允许应用网络访问

### 登录失败
1. 检查网络连接状态
2. 确认微信公众号平台账号密码正确
3. 尝试清除缓存重新登录

### 爬取异常
1. 检查token和cookie是否过期
2. 降低爬取频率
3. 检查目标公众号是否存在

## 📞 技术支持

如遇到问题，请提供以下信息：
- 操作系统版本
- 具体错误信息
- 操作步骤

## 🔄 更新说明

- **版本**：v2.0
- **构建时间**：2024/12/20
- **Python版本**：3.13.2
- **PyQt版本**：5.15.7

---

**感谢使用微信爬虫工具！** 🎉 