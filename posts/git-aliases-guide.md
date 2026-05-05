# ⚡ 我整理了 100 个 Git 别名，让效率提升 300%

> 从 `git status` 到 `gst`，每天节省 30 分钟

## 为什么需要 Git 别名？

每天敲几十次 `git status`、`git commit`、`git push`？

**时间成本**：
- `git status` = 11 个字符 + 回车
- 每天 50 次 = 550 次按键
- 一年 = 200,000+ 次按键

**解决方案**：别名
- `gst` = 3 个字符
- 效率提升 **73%**

---

## 精选别名速查表

### 🚀 高频命令（每天使用）

| 别名 | 原命令 | 节省 |
|------|--------|------|
| `gst` | `git status -sb` | 73% |
| `gl` | `git log --oneline --graph -10` | 85% |
| `gd` | `git diff` | 75% |
| `gds` | `git diff --staged` | 80% |
| `gc` | `git commit` | 75% |
| `gcm` | `git commit -m` | 78% |
| `gp` | `git push` | 75% |
| `gpl` | `git pull` | 75% |

### 🌿 分支操作

| 别名 | 原命令 | 场景 |
|------|--------|------|
| `gb` | `git branch -a` | 查看分支 |
| `gco` | `git checkout` | 切换分支 |
| `gcb` | `git checkout -b` | 创建并切换 |
| `gbd` | `git branch -d` | 删除分支 |
| `gbD` | `git branch -D` | 强制删除 |
| `gm` | `git merge` | 合并分支 |

### 💾 提交管理

| 别名 | 原命令 | 场景 |
|------|--------|------|
| `gca` | `git commit --amend` | 修改上次提交 |
| `gcan` | `git commit --amend --no-edit` | 不改消息修改 |
| `gcp` | `git cherry-pick` | 挑拣提交 |
| `grs` | `git reset --soft HEAD~1` | 软回退 |
| `grh` | `git reset --hard HEAD~1` | 硬回退 |

### 🔄 远程操作

| 别名 | 原命令 | 场景 |
|------|--------|------|
| `gf` | `git fetch --all` | 获取更新 |
| `gpf` | `git push --force-with-lease` | 安全强制推送 |
| `gpu` | `git push -u origin` | 推送并关联 |
| `grv` | `git remote -v` | 查看远程 |

---

## 安装方法

### 一键安装（推荐）

```bash
curl -fsSL https://raw.githubusercontent.com/KEBANJILONG/git-aliases-pro/main/install.sh | bash
```

### 手动安装

```bash
git clone https://github.com/KEBANJILONG/git-aliases-pro.git
cd git-aliases-pro
./install.sh
```

### 效果验证

```bash
$ gst
## main...origin/main
 M README.md
?? new-file.txt
```

---

## 实际效率对比

### 日常操作（一天 50 次 Git 命令）

| 方式 | 平均耗时 | 日耗时 | 年耗时 |
|------|----------|--------|--------|
| 完整命令 | 3 秒 | 150 秒 | 15 小时 |
| 别名 | 1 秒 | 50 秒 | 5 小时 |
| **节省** | **67%** | **100 秒** | **10 小时** |

**一年节省 10 小时**，相当于多出一个工作日！

---

## 进阶技巧

### 自定义别名

```bash
# 添加自己的别名
git config --global alias.stash-unapply '!git stash show -p | git apply -R'

# 查看所有别名
git config --get-regexp alias
```

### 结合其他工具

```bash
# 配合 fzf 模糊搜索
alias gco='git checkout $(git branch -a | fzf)'

# 配合 peco 交互选择
alias gbd='git branch -d $(git branch | peco)'
```

---

## 完整列表

访问 GitHub 查看全部 100+ 别名：

**[KEBANJILONG/git-aliases-pro](https://github.com/KEBANJILONG/git-aliases-pro)**

包含：
- ✅ 基础别名（20+）
- ✅ 高级别名（30+）
- ✅ 工作流别名（25+）
- ✅ 调试别名（15+）
- ✅ 自定义扩展（10+）

---

## 用户反馈

> "从 11 个字符到 3 个字符，每天少敲几百次键盘" —— 某全栈开发者

> "团队统一别名后，代码审查效率提升明显" —— 某技术 Leader

---

## 参与贡献

```bash
git clone https://github.com/KEBANJILONG/git-aliases-pro.git
# 添加你的别名，提交 PR
```

---

**让 Git 操作飞起来！** ⚡

**GitHub**: [KEBANJILONG/git-aliases-pro](https://github.com/KEBANJILONG/git-aliases-pro)

**License**: MIT
