# n8n技术栈及开发文档

本文档列举了n8n项目使用的主要技术栈，并提供了相应的开发者文档链接，方便开发者进行二次开发时参考。

## 目录

- [后端技术栈](#后端技术栈)
- [前端技术栈](#前端技术栈)
- [构建和部署工具](#构建和部署工具)
- [测试框架](#测试框架)
- [监控和日志](#监控和日志)
- [项目根目录文件说明](#项目根目录文件说明)

## 后端技术栈

### 核心框架和语言

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| TypeScript | ^5.7.2 | [文档](https://www.typescriptlang.org/docs/) |
| Node.js | v20.15+ | [文档](https://nodejs.org/docs/latest-v20.x/api/) |
| Express.js | 4.21.1 | [文档](https://expressjs.com/en/4x/api.html) |

### 数据库和ORM

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| TypeORM | 0.3.20-12 (自定义版本) | [文档](https://typeorm.io/) |
| PostgreSQL | 8.12.0 | [文档](https://www.postgresql.org/docs/) |
| MySQL | 3.11.0 | [文档](https://dev.mysql.com/doc/) |
| SQLite | 5.1.7 | [文档](https://www.sqlite.org/docs.html) |

### API相关

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| REST API | - | [Express REST API指南](https://expressjs.com/en/guide/routing.html) |
| WebSocket | 8.17.1 | [文档](https://github.com/websockets/ws) |
| OpenAPI/Swagger | 5.0.1 | [文档](https://swagger.io/docs/) |

### 工作流引擎

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Bull | 4.12.1 | [文档](https://github.com/OptimalBits/bull/blob/master/REFERENCE.md) |
| cron | 3.1.7 | [文档](https://github.com/kelektiv/node-cron) |

### 认证与安全

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| JWT (jsonwebtoken) | 9.0.2 | [文档](https://github.com/auth0/node-jsonwebtoken) |
| bcryptjs | 2.4.3 | [文档](https://github.com/dcodeIO/bcrypt.js) |
| CSRF | 3.1.0 | [文档](https://github.com/pillarjs/csrf) |

### 其他重要库

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| axios | 1.7.4 | [文档](https://axios-http.com/docs/intro) |
| lodash | 4.17.21 | [文档](https://lodash.com/docs/) |
| luxon | 3.4.4 | [文档](https://moment.github.io/luxon/) |
| winston | 3.14.2 | [文档](https://github.com/winstonjs/winston) |
| zod | 3.24.1 | [文档](https://zod.dev/) |

## 前端技术栈

### 核心框架

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Vue.js | ^3.5.13 | [文档](https://vuejs.org/guide/introduction.html) |
| TypeScript | ^5.6.2 | [文档](https://www.typescriptlang.org/docs/) |
| Vite | ^6.0.2 | [文档](https://vitejs.dev/guide/) |

### 状态管理

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Pinia | ^2.2.4 | [文档](https://pinia.vuejs.org/) |
| Vue Router | ^4.5.0 | [文档](https://router.vuejs.org/) |

### UI组件和样式

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| n8n-design-system | 自研 | 内部文档 |
| SASS/SCSS | - | [文档](https://sass-lang.com/documentation/) |
| Vue Flow | ^1.42.1 | [文档](https://vueflow.dev/) |

### 图表和可视化

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Chart.js | ^4.4.0 | [文档](https://www.chartjs.org/docs/latest/) |
| vue-chartjs | ^5.2.0 | [文档](https://vue-chartjs.org/) |

### 编辑器和代码相关

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| CodeMirror | ^6.x | [文档](https://codemirror.net/docs/) |
| Prettier | ^3.3.3 | [文档](https://prettier.io/docs/en/) |

### 工具库

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| axios | 1.7.4 | [文档](https://axios-http.com/docs/intro) |
| lodash-es | ^4.17.21 | [文档](https://lodash.com/docs/) |
| luxon | 3.4.4 | [文档](https://moment.github.io/luxon/) |
| uuid | 10.0.0 | [文档](https://github.com/uuidjs/uuid) |

## 构建和部署工具

### 包管理和构建

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| pnpm | - | [文档](https://pnpm.io/motivation) |
| Turbo | 2.3.3 | [文档](https://turbo.build/repo/docs) |
| Vite | ^6.0.2 | [文档](https://vitejs.dev/guide/) |

### CI/CD

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| GitHub Actions | - | [文档](https://docs.github.com/en/actions) |
| Docker | - | [文档](https://docs.docker.com/) |

### 代码质量

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| ESLint | - | [文档](https://eslint.org/docs/latest/) |
| Biome | ^1.9.0 | [文档](https://biomejs.dev/guides/) |
| Husky (lefthook) | ^1.7.15 | [文档](https://github.com/evilmartians/lefthook) |

## 测试框架

### 单元测试

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Jest | ^29.6.2 | [文档](https://jestjs.io/docs/getting-started) |
| Vitest | ^3.0.2 | [文档](https://vitest.dev/guide/) |

### E2E测试

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Testing Library | ^6.6.3 | [文档](https://testing-library.com/docs/) |

### API测试

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Supertest | ^7.0.0 | [文档](https://github.com/ladjs/supertest) |

## 监控和日志

| 技术 | 版本 | 文档链接 |
|------|------|----------|
| Winston | 3.14.2 | [文档](https://github.com/winstonjs/winston) |
| Sentry | ^8.52.1 | [文档](https://docs.sentry.io/platforms/node/) |
| Prometheus | 13.2.0 | [文档](https://prometheus.io/docs/introduction/overview/) |

## 项目根目录文件说明

n8n项目根目录下包含多个配置文件和目录，以下是对这些文件的详细说明：

### 配置文件

| 文件名 | 用途 |
|--------|------|
| `package.json` | 项目的主配置文件，定义了项目依赖、脚本命令和元数据 |
| `pnpm-workspace.yaml` | pnpm工作区配置，定义了monorepo中包含的子包路径 |
| `pnpm-lock.yaml` | pnpm依赖锁定文件，确保团队成员使用相同的依赖版本 |
| `tsconfig.json` | TypeScript主配置文件，定义了项目的TypeScript编译选项 |
| `tsconfig.backend.json` | 后端特定的TypeScript配置，继承自主配置文件 |
| `tsconfig.build.json` | 构建时使用的TypeScript配置 |
| `turbo.json` | Turborepo配置文件，定义了构建管道和缓存策略 |
| `vitest.workspace.ts` | Vitest测试框架的工作区配置 |
| `jest.config.js` | Jest测试框架配置文件 |
| `lefthook.yml` | Lefthook Git钩子配置，用于代码提交前的检查 |
| `biome.jsonc` | Biome代码格式化和检查工具的配置文件 |
| `codecov.yml` | Codecov代码覆盖率报告工具的配置文件 |
| `.npmrc` | npm/pnpm配置文件，定义了包管理器行为 |
| `.npmignore` | 定义发布npm包时要忽略的文件 |
| `.gitignore` | 定义Git版本控制要忽略的文件 |
| `.gitattributes` | 定义Git如何处理特定文件类型 |
| `.git-blame-ignore-revs` | 定义在git blame中要忽略的提交 |
| `.prettierrc.js` | Prettier代码格式化工具配置 |
| `.prettierignore` | 定义Prettier要忽略的文件 |
| `.editorconfig` | 跨编辑器的代码风格配置 |

### 目录结构

| 目录名 | 用途 |
|--------|------|
| `packages/` | 包含所有n8n的子包，采用monorepo结构管理 |
| `scripts/` | 包含各种构建、发布和维护脚本 |
| `cypress/` | 包含Cypress端到端测试代码 |
| `assets/` | 包含项目的静态资源文件 |
| `.vscode/` | VS Code编辑器配置，包括推荐的扩展和调试配置 |
| `.github/` | GitHub相关配置，包括Issue模板、PR模板和GitHub Actions工作流 |
| `.turbo/` | Turborepo缓存目录 |
| `node_modules/` | 项目依赖安装目录 |

### 特殊文件

| 文件名 | 用途 |
|--------|------|
| `.editorconfig` | 定义编辑器通用配置，确保不同编辑器使用相同的代码风格 |
| `vitest.workspace.ts` | 配置Vitest测试框架的工作区，用于前端测试 |
| `jest.config.js` | 配置Jest测试框架，主要用于后端测试 |
