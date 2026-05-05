# 🚀 我开源了一套开发环境一键搭建工具，让新电脑配置从 2 小时缩短到 5 分钟

> 从反复折腾到一键搞定，DevEnv-Setup 让开发环境配置不再痛苦

## 痛点：每次换电脑都是一场灾难

作为开发者，你是否经历过这些场景：

- 🔥 **新电脑到手**：安装 Node.js、Python、Git、VS Code... 折腾 2 小时+
- 😤 **团队协作**："我这能跑啊"，环境差异导致 bug 无法复现
- 😵 **重装系统**：所有配置丢失，从头再来
- 🤯 **多设备切换**：Mac 和 Windows 来回切换，配置不统一

我曾经也是受害者。直到我受够了，决定写一套工具彻底解决这个问题。

---

## 解决方案：DevEnv-Setup

**GitHub**: [KEBANJILONG/DevEnv-Setup](https://github.com/KEBANJILONG/DevEnv-Setup)

### 核心能力

```bash
# 一行命令，检测当前环境
devenv check

# 一键安装全套 Web 开发环境
devenv install web-full

# 快速创建新项目
devenv new react my-app
```

### 功能特性

| 功能 | 说明 |
|------|------|
| 🔍 环境检测 | 自动检测 9 种开发工具的安装状态 |
| 📦 一键安装 | 支持 10+ 工具，带版本选择 |
| 🎯 预设方案 | Web、后端、DevOps、移动端 7 种预设 |
| 🆕 项目模板 | React、Vue、Next.js、Express、FastAPI、Django |
| ⚙️ 智能配置 | Git、VS Code 扩展自动配置 |
| 💾 备份恢复 | 环境配置一键备份/恢复 |
| 🔧 问题诊断 | `devenv doctor` 自动修复常见问题 |

---

## 实战演示

### 场景 1：新电脑初始化

```bash
# 安装 DevEnv-Setup
pip install devenv-setup

# 检查环境
devenv check

# 安装 Web 开发全套
devenv install web-full

# 配置 Git
devenv config git --name "你的名字" --email "your@email.com"

# 安装 VS Code 扩展
devenv extensions web
```

**耗时：5 分钟**（原本 2 小时+）

### 场景 2：创建新项目

```bash
# 创建 React + TypeScript 项目
devenv new react my-dashboard

# 创建 FastAPI 后端
devenv new fastapi my-api
```

自动生成：
- ✅ 项目结构
- ✅ 配置文件
- ✅ 开发脚本
- ✅ Git 忽略规则

### 场景 3：环境诊断

```bash
devenv doctor
```

自动检测并修复：
- Python 版本过旧
- PATH 配置问题
- Git 未配置
- Windows 开发者模式

---

## 技术亮点

### 跨平台支持

- **Windows**: PowerShell + winget/choco
- **macOS**: Homebrew
- **Linux**: apt/yum/pacman

### 智能检测

```python
# 自动识别操作系统
self.os_type = platform.system().lower()  # windows / darwin / linux

# 检测工具安装状态
shutil.which("node")  # 检查 Node.js
subprocess.run(["python", "--version"])  # 检查 Python
```

### 错误恢复

每个操作都有详细的错误处理和用户提示：

```python
try:
    subprocess.run(cmd, check=True)
except subprocess.CalledProcessError:
    print("❌ 安装失败，尝试备用方案...")
    fallback_install()
```

---

## 配套工具生态

我还开源了相关工具，形成完整工作流：

| 工具 | 用途 | 链接 |
|------|------|------|
| **git-aliases-pro** | 100+ Git 别名 | [GitHub](https://github.com/KEBANJILONG/git-aliases-pro) |
| **docker-devkit** | Docker 开发模板 | [GitHub](https://github.com/KEBANJILONG/docker-devkit) |
| **dotfiles-manager** | 配置同步 | [GitHub](https://github.com/KEBANJILONG/dotfiles-manager) |

---

## 用户反馈

> "以前配环境要半天，现在 5 分钟搞定，太爽了！" —— 某前端开发者

> "团队新人入职，一键配置，省了大量时间" —— 某技术负责人

---

## 如何参与

### 使用

```bash
pip install devenv-setup
devenv --help
```

### 贡献

```bash
git clone https://github.com/KEBANJILONG/DevEnv-Setup.git
cd DevEnv-Setup
# 提交 PR，共同完善
```

### 反馈

- 🐛 Bug 报告：[Issues](https://github.com/KEBANJILONG/DevEnv-Setup/issues)
- 💡 功能建议：[Discussions](https://github.com/KEBANJILONG/DevEnv-Setup/discussions)

---

## 未来规划

- [ ] GUI 界面（PyQt/Tauri）
- [ ] 更多预设（AI/ML、区块链、游戏开发）
- [ ] 云端配置同步
- [ ] CI/CD 集成

---

## 写在最后

开发环境配置不应该成为开发者的负担。DevEnv-Setup 的目标是让每个人都能在 5 分钟内准备好开发环境，把时间和精力集中在真正重要的事情上——**写代码**。

如果你也受够了反复配置环境，试试 DevEnv-Setup，欢迎 Star ⭐ 和反馈！

---

**GitHub**: [KEBANJILONG/DevEnv-Setup](https://github.com/KEBANJILONG/DevEnv-Setup)

**License**: MIT
