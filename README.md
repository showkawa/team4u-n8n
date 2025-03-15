# n8n 二次开发指南

本文档提供了关于如何进行n8n二次开发的详细指导，包括环境搭建、开发流程、常见开发场景和最佳实践。

## 目录

- [项目简介](#项目简介)
- [环境搭建](#环境搭建)
- [项目结构](#项目结构)
- [开发流程](#开发流程)
- [常见开发场景](#常见开发场景)
- [调试技巧](#调试技巧)
- [测试](#测试)
- [部署](#部署)
- [常见问题](#常见问题)
- [参考资源](#参考资源)
- [项目命令](#项目命令)

## 项目简介

n8n是一个强大的工作流自动化平台，允许用户通过可视化界面连接各种服务和API，实现数据流和工作流的自动化。n8n支持280+种集成，包括常见的SaaS服务、数据库、API等。

主要特点：

- 开源且可扩展
- 支持自托管部署
- 可视化工作流编辑器
- 丰富的节点库
- 强大的表达式引擎
- 支持企业级功能

## 环境搭建

### 系统要求

- Node.js (v20.15 或更高版本)
- pnpm (v9.15 或更高版本)
- Git

### 开发环境搭建步骤

1. **克隆仓库**

```bash
git clone https://github.com/n8n-io/n8n.git
cd n8n
```

2. **安装依赖**

n8n使用pnpm作为包管理器：

```bash
# 全局安装pnpm
npm install -g pnpm

# 安装项目依赖
pnpm install
```

3. **构建项目**

```bash
pnpm build
```

4. **启动开发服务器**

```bash
# 同时启动前端和后端（推荐）
pnpm dev

# 或者分别启动
# 只启动后端
pnpm dev:be

# 只启动前端
pnpm dev:fe
```

5. **访问应用**

默认情况下，n8n将在 <http://localhost:5678> 运行

### 环境变量配置

在项目根目录创建 `.env` 文件，常用环境变量：

```
N8N_PORT=5678
N8N_PROTOCOL=http
N8N_HOST=localhost
N8N_PATH=/
N8N_EDITOR_BASE_URL=http://localhost:5678
```

### 数据库配置

默认使用SQLite数据库，如需使用其他数据库，在 `.env` 文件中配置：

```
DB_TYPE=postgresdb
DB_POSTGRESDB_HOST=localhost
DB_POSTGRESDB_PORT=5432
DB_POSTGRESDB_DATABASE=n8n
DB_POSTGRESDB_USER=your-user
DB_POSTGRESDB_PASSWORD=your-password
```

## 项目结构

n8n采用monorepo结构，主要包含以下包：

- `/packages/cli` - 命令行接口和后端服务
- `/packages/core` - 核心功能
- `/packages/design-system` - UI组件库
- `/packages/editor-ui` - 前端编辑器
- `/packages/nodes-base` - 基础节点
- `/packages/workflow` - 工作流引擎

## 开发流程

### 代码风格和规范

n8n使用ESLint和Prettier进行代码格式化和检查。在提交代码前，确保代码符合项目规范：

```bash
# 运行代码检查
pnpm lint

# 自动修复代码风格问题
pnpm lintfix
```

### 分支管理

- `master` - 主分支，包含最新稳定版本
- `release/*` - 发布分支
- `feature/*` - 功能开发分支
- `bugfix/*` - 错误修复分支

开发新功能时，应从master分支创建新的feature分支：

```bash
git checkout -b feature/your-feature-name
```

## 常见开发场景

### 1. 创建自定义节点

自定义节点是n8n二次开发最常见的场景。节点开发步骤：

1. **创建节点目录结构**

在 `/packages/nodes-base/nodes/YourNodeName/` 目录下创建以下文件：

- `YourNodeName.node.ts` - 节点主类
- `YourNodeName.node.json` - 节点元数据
- `GenericFunctions.ts` - 通用函数
- `descriptions/` - 操作描述文件

2. **实现节点类**

节点类需要继承 `INodeType` 接口：

```typescript
import { INodeType, INodeTypeDescription } from 'n8n-workflow';

export class YourNodeName implements INodeType {
    description: INodeTypeDescription = {
        displayName: 'Your Node Name',
        name: 'yourNodeName',
        icon: 'file:yourNodeName.svg',
        group: ['transform'],
        version: 1,
        description: 'Your node description',
        defaults: {
            name: 'Your Node Name',
        },
        inputs: ['main'],
        outputs: ['main'],
        properties: [
            // 节点属性定义
        ],
    };

    async execute() {
        // 节点执行逻辑
    }
}
```

3. **注册节点**

在 `/packages/nodes-base/package.json` 中添加节点引用。

4. **重新构建**

```bash
pnpm build
```

### 2. 修改前端UI

1. **修改编辑器UI**

编辑器UI代码位于 `/packages/editor-ui/src/` 目录：

- `/components/` - Vue组件
- `/views/` - 页面视图
- `/stores/` - Pinia状态管理
- `/mixins/` - Vue混入

2. **修改设计系统**

设计系统代码位于 `/packages/design-system/` 目录。

3. **重新构建前端**

```bash
pnpm build:frontend
```

### 3. 扩展后端API

1. **添加新的API端点**

在 `/packages/cli/src/controllers/` 目录下创建或修改控制器：

```typescript
import { RestController, Get, Post } from '@/decorators';

@RestController('your-endpoint')
export class YourController {
    @Get('/')
    async getItems() {
        // 实现获取逻辑
    }

    @Post('/')
    async createItem() {
        // 实现创建逻辑
    }
}
```

2. **添加新的服务**

在 `/packages/cli/src/services/` 目录下创建服务类：

```typescript
import { Service } from '@n8n/di';

@Service()
export class YourService {
    // 实现服务方法
}
```

## 调试技巧

### 后端调试

使用VS Code调试配置（`.vscode/launch.json`）：

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Debug n8n",
            "skipFiles": ["<node_internals>/**"],
            "program": "${workspaceFolder}/packages/cli/bin/n8n",
            "outFiles": ["${workspaceFolder}/packages/*/dist/**/*.js"],
            "env": {
                "NODE_ENV": "development"
            }
        }
    ]
}
```

### 前端调试

1. 使用Vue Devtools浏览器扩展
2. 在代码中添加 `console.log` 或 `debugger` 语句
3. 使用浏览器开发者工具的Sources面板设置断点

## 测试

### 单元测试

```bash
# 运行所有测试
pnpm test

# 运行特定包的测试
pnpm test --filter=n8n-workflow
```

### E2E测试

```bash
# 运行E2E测试
pnpm test:e2e
```

## 部署

### Docker部署

```bash
# 构建Docker镜像
docker build -t your-n8n-image .

# 运行容器
docker run -p 5678:5678 your-n8n-image
```

### 生产环境配置

生产环境推荐配置：

```
N8N_ENCRYPTION_KEY=your-secure-encryption-key
N8N_USER_MANAGEMENT_DISABLED=false
N8N_DIAGNOSTICS_ENABLED=false
DB_TYPE=postgresdb
```

## 常见问题

### 构建错误

如果遇到构建错误，尝试清理缓存：

```bash
pnpm clean:all
pnpm install
pnpm build
```

### 依赖问题

如果遇到依赖冲突，尝试：

```bash
pnpm install --force
```

### 数据库迁移问题

如果遇到数据库迁移问题：

```bash
n8n migrate
```

## 项目命令

n8n项目提供了多种命令来帮助开发、构建和测试。以下是package.json中定义的主要命令及其功能：

### 构建命令

| 命令 | 描述 |
|------|------|
| `pnpm build` | 构建整个项目（前端和后端） |
| `pnpm build:backend` | 只构建后端部分 |
| `pnpm build:frontend` | 只构建前端部分 |
| `pnpm build:nodes` | 构建节点包 |

### 开发命令

| 命令 | 描述 |
|------|------|
| `pnpm dev` | 同时启动前端和后端开发服务器（主要开发命令） |
| `pnpm dev:be` | 只启动后端开发服务器 |
| `pnpm dev:fe` | 只启动前端开发服务器 |
| `pnpm dev:ai` | 启动AI相关服务（LangChain节点） |
| `pnpm dev:e2e` | 启动E2E测试环境 |
| `pnpm dev:e2e:v1` | 启动V1版本的E2E测试环境 |
| `pnpm dev:e2e:server` | 启动E2E测试服务器 |

### 代码质量命令

| 命令 | 描述 |
|------|------|
| `pnpm format` | 格式化代码 |
| `pnpm format:check` | 检查代码格式 |
| `pnpm lint` | 运行所有代码检查 |
| `pnpm lintfix` | 自动修复代码问题 |
| `pnpm lint:backend` | 只检查后端代码 |
| `pnpm lint:nodes` | 只检查节点代码 |
| `pnpm lint:frontend` | 只检查前端代码 |
| `pnpm typecheck` | 运行TypeScript类型检查 |

### 测试命令

| 命令 | 描述 |
|------|------|
| `pnpm test` | 运行所有测试 |
| `pnpm test:backend` | 运行后端测试 |
| `pnpm test:frontend` | 运行前端测试 |
| `pnpm test:nodes` | 运行节点测试 |

### 运行命令

| 命令 | 描述 |
|------|------|
| `pnpm start` | 启动n8n服务（生产模式） |
| `pnpm start:tunnel` | 使用隧道启动n8n（用于外部访问） |
| `pnpm webhook` | 启动webhook服务 |
| `pnpm worker` | 启动worker服务 |

### 维护命令

| 命令 | 描述 |
|------|------|
| `pnpm clean` | 清理构建文件 |
| `pnpm reset` | 重置项目（清理所有构建文件和依赖） |
| `pnpm watch` | 监视文件变化并重新构建 |
| `pnpm optimize-svg` | 优化SVG图标文件 |

### 特殊命令

| 命令 | 描述 |
|------|------|
| `pnpm prepare` | 在安装后自动运行的准备脚本 |
| `pnpm preinstall` | 安装前运行的脚本（阻止npm安装） |

## 参考资源

- [n8n官方开发文档](https://docs.n8n.io/)
- [n8n API文档](https://docs.n8n.io/api/)
- [n8n GitHub仓库](https://github.com/n8n-io/n8n)
- [n8n社区论坛](https://community.n8n.io/)
