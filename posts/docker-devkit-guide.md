# 🐳 Docker 开发环境配置太复杂？我整理了一套即开即用的模板

> 从"docker-compose 写半天"到"一行命令启动"，docker-devkit 让容器化开发变得简单

## 痛点：Docker 配置是个体力活

想搭建一个开发环境，你需要：

1. 写 Dockerfile（基础镜像、依赖安装、端口暴露）
2. 写 docker-compose.yml（服务编排、网络、卷挂载）
3. 配置环境变量
4. 调试网络连通性
5. 处理热重载
6. ...

**耗时：2-4 小时** 😫

而且每个项目都要重复一遍！

---

## 解决方案：docker-devkit

**GitHub**: [KEBANJILONG/docker-devkit](https://github.com/KEBANJILONG/docker-devkit)

### 核心理念

**复制 → 粘贴 → 启动**

```bash
# 克隆模板库
git clone https://github.com/KEBANJILONG/docker-devkit.git

# 进入需要的模板
cd docker-devkit/templates/node-react

# 一键启动
docker-compose up -d

# 开始开发！
```

---

## 可用模板

### 🚀 Node.js + React

```yaml
# docker-compose.yml
version: '3.8'
services:
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    volumes:
      - ./frontend:/app
      - /app/node_modules
    environment:
      - CHOKIDAR_USEPOLLING=true
  backend:
    build: ./backend
    ports:
      - "5000:5000"
    volumes:
      - ./backend:/app
      - /app/node_modules
```

**特性**：
- ✅ 热重载（代码改完自动刷新）
- ✅ 依赖隔离（node_modules 不冲突）
- ✅ 生产优化（多阶段构建）

### 🐍 Python + Django

```yaml
services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    depends_on:
      - db
      - redis
  db:
    image: postgres:15
    environment:
      POSTGRES_DB: myapp
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
  redis:
    image: redis:7-alpine
```

**特性**：
- ✅ PostgreSQL + Redis 预配置
- ✅ 数据库迁移自动执行
- ✅ 静态文件收集

### 🎯 Go + PostgreSQL

```yaml
services:
  api:
    build:
      context: .
      target: dev
    ports:
      - "8080:8080"
    volumes:
      - .:/app
    environment:
      - DATABASE_URL=postgres://user:pass@db:5432/myapp?sslmode=disable
  db:
    image: postgres:15-alpine
    volumes:
      - postgres_data:/var/lib/postgresql/data
  pgadmin:
    image: dpage/pgadmin4
    ports:
      - "5050:80"
```

**特性**：
- ✅ Air 热重载
- ✅ pgAdmin 管理界面
- ✅ 生产优化构建

---

## 快速开始

### 1. 安装依赖

```bash
# Docker 20.10+
docker --version

# Docker Compose 2.0+
docker-compose --version
```

### 2. 选择模板

```bash
git clone https://github.com/KEBANJILONG/docker-devkit.git
cd docker-devkit

# 查看可用模板
ls templates/
# devops/  fullstack/  go-postgres/  node-react/  python-django/
```

### 3. 启动开发环境

```bash
cd templates/node-react
docker-compose up -d

# 查看日志
docker-compose logs -f

# 停止
docker-compose down
```

---

## 模板对比

| 模板 | 服务 | 适用场景 | 启动时间 |
|------|------|----------|----------|
| **node-react** | Node + React | 前端开发 | 30s |
| **python-django** | Django + PostgreSQL + Redis | Python Web | 45s |
| **go-postgres** | Go + PostgreSQL + pgAdmin | Go API | 35s |
| **fullstack** | FE + BE + DB + Cache | 全栈开发 | 60s |
| **devops** | Jenkins + Nexus + Registry | CI/CD | 90s |

---

## 高级用法

### 自定义配置

```bash
# 复制模板
cp -r templates/node-react my-project

# 修改配置
vim my-project/docker-compose.yml

# 启动
cd my-project && docker-compose up -d
```

### 多环境支持

```bash
# 开发环境
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up

# 生产环境
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up
```

### 数据持久化

```yaml
volumes:
  postgres_data:
    driver: local
  redis_data:
    driver: local
```

---

## 最佳实践

### 1. 使用 .env 文件

```bash
# .env
DATABASE_URL=postgres://user:pass@db:5432/myapp
REDIS_URL=redis://redis:6379
SECRET_KEY=your-secret-key
```

### 2. 健康检查

```yaml
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:8080/health"]
  interval: 30s
  timeout: 10s
  retries: 3
```

### 3. 资源限制

```yaml
deploy:
  resources:
    limits:
      cpus: '2'
      memory: 2G
    reservations:
      cpus: '1'
      memory: 1G
```

---

## 常见问题

### Q: 端口冲突怎么办？

```yaml
ports:
  - "3001:3000"  # 主机 3001 映射到容器 3000
```

### Q: 如何进入容器调试？

```bash
docker-compose exec backend bash
```

### Q: 数据会丢失吗？

使用命名卷持久化：
```yaml
volumes:
  - postgres_data:/var/lib/postgresql/data
```

---

## 参与贡献

```bash
git clone https://github.com/KEBANJILONG/docker-devkit.git

# 添加新模板
cd templates
mkdir my-awesome-template
# 添加 Dockerfile + docker-compose.yml
# 提交 PR
```

---

## 相关工具

| 工具 | 用途 | 链接 |
|------|------|------|
| **DevEnv-Setup** | 本地环境搭建 | [GitHub](https://github.com/KEBANJILONG/DevEnv-Setup) |
| **git-aliases-pro** | Git 效率工具 | [GitHub](https://github.com/KEBANJILONG/git-aliases-pro) |
| **dotfiles-manager** | 配置同步 | [GitHub](https://github.com/KEBANJILONG/dotfiles-manager) |

---

**让 Docker 开发像呼吸一样自然！** 🐳

**GitHub**: [KEBANJILONG/docker-devkit](https://github.com/KEBANJILONG/docker-devkit)

**License**: MIT
