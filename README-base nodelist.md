# n8n 节点分类列表

本文档按类别列出了n8n支持的所有集成节点，帮助您快速找到所需的节点类型。

## 目录

- [核心节点](#核心节点)
  - [流程控制](#流程控制)
  - [数据转换](#数据转换)
  - [辅助工具](#辅助工具)
  - [触发器](#触发器)
- [通信与消息](#通信与消息)
- [数据存储与处理](#数据存储与处理)
- [开发工具](#开发工具)
- [文件处理](#文件处理)
- [生产力工具](#生产力工具)
- [分析工具](#分析工具)
- [项目管理](#项目管理)
- [人工智能](#人工智能)
- [其他服务](#其他服务)

## 核心节点

核心节点是n8n工作流的基础组件，用于控制流程、转换数据和执行基本操作。

### 流程控制

这些节点用于控制工作流的执行流程。

- **CompareDatasets** - 比较两个数据集并执行相应操作
- **ExecuteWorkflow** - 执行另一个工作流
- **If** - 基于条件执行不同分支
- **Merge** - 合并来自多个分支的数据
- **Split In Batches** - 将数据分批处理
- **Start** - 工作流的起始点
- **Stop And Error** - 停止工作流并显示错误
- **Switch** - 基于条件执行多个分支
- **Wait** - 暂停工作流执行一段时间

### 数据转换

这些节点用于处理和转换数据。

- **Code** - 使用JavaScript代码处理数据
- **Function** - 对所有项目执行JavaScript函数
- **FunctionItem** - 对每个项目执行JavaScript函数
- **ItemLists** - 处理项目列表（聚合、去重、限制、排序等）
- **Markdown** - 转换Markdown和HTML
- **RenameKeys** - 重命名数据项的键
- **Set** - 设置数据项的值
- **Transform** - 转换数据结构

### 辅助工具

这些节点提供各种辅助功能。

- **DebugHelper** - 调试工作流
- **ExecutionData** - 获取当前执行的数据
- **NoOp** - 不执行任何操作（用于测试）
- **StickyNote** - 添加注释（不影响工作流）
- **n8n** - 与n8n实例交互

### 触发器

这些节点用于触发工作流的执行。

- **Cron** - 按时间表触发
- **ErrorTrigger** - 当其他工作流出错时触发
- **Form** - 通过表单提交触发
- **LocalFileTrigger** - 监控本地文件变化触发
- **ManualTrigger** - 手动触发
- **n8nTrigger** - 基于n8n事件触发
- **Schedule** - 按计划触发
- **SseTrigger** - 通过服务器发送事件触发
- **Webhook** - 通过HTTP请求触发
- **WorkflowTrigger** - 当其他工作流执行时触发

## 通信与消息

这些节点用于发送和接收各种通信和消息。

- **EmailReadImap** - 读取电子邮件
- **EmailSend** - 发送电子邮件

## 数据存储与处理

这些节点用于存储、检索和处理数据。

- **Airtable** - 数据库和电子表格混合工具
- **Baserow** - 数据库工具
- **CrateDb** - 分布式SQL数据库
- **Elasticsearch** - 搜索和分析引擎
- **MongoDB** - NoSQL数据库
- **MySQL** - 关系型数据库
- **NocoDB** - 开源Airtable替代品
- **Postgres** - 关系型数据库
- **QuestDb** - 时序数据库
- **Redis** - 内存数据结构存储
- **S3** - 对象存储服务
- **Snowflake** - 云数据仓库
- **Supabase** - Firebase替代品
- **TimescaleDb** - 时序数据库

## 开发工具

这些节点用于开发和测试。

- **Bitbucket** - 代码托管
- **CircleCi** - 持续集成服务
- **ExecuteCommand** - 执行命令行命令
- **Git** - 版本控制
- **GitHub** - 代码托管和协作
- **GitLab** - 代码托管和DevOps
- **GraphQL** - GraphQL API请求
- **HttpRequest** - 发送HTTP请求
- **Jenkins** - 持续集成服务
- **Npm** - Node包管理器
- **PostBin** - 测试HTTP请求
- **SentryIo** - 错误跟踪
- **Ssh** - SSH连接
- **TravisCi** - 持续集成服务

## 文件处理

这些节点用于处理文件和文档。

- **Box** - 云存储服务
- **Dropbox** - 云存储服务
- **EditImage** - 编辑图像
- **FileMaker** - 数据库软件
- **Files** - 文件操作
- **Ftp** - FTP文件传输
- **GoogleDrive** - 云存储服务
- **GoogleSheets** - 电子表格
- **MicrosoftOneDrive** - 云存储服务
- **ReadBinaryFile** - 读取二进制文件
- **ReadBinaryFiles** - 批量读取二进制文件
- **ReadPdf** - 读取PDF文件
- **SpreadsheetFile** - 处理电子表格文件
- **WriteBinaryFile** - 写入二进制文件
- **Xml** - 处理XML数据

## 生产力工具

这些节点用于提高工作效率。

- **Asana** - 项目管理
- **Calendly** - 日程安排
- **Clockify** - 时间跟踪
- **Coda** - 文档协作
- **Grist** - 数据管理
- **Microsoft365** - 办公套件
- **MicrosoftToDo** - 任务管理
- **Notion** - 工作空间
- **Todoist** - 任务管理
- **Toggl** - 时间跟踪
- **Trello** - 项目管理

## 分析工具

这些节点用于数据分析和监控。

- **Clearbit** - 商业数据
- **Google Analytics** - 网站分析
- **Metabase** - 商业智能工具
- **PostHog** - 产品分析
- **Splunk** - 数据分析
- **UptimeRobot** - 网站监控

## 项目管理

这些节点用于项目和任务管理。

- **ClickUp** - 项目管理
- **Jira** - 项目管理
- **Linear** - 项目管理
- **ServiceNow** - IT服务管理
- **Taiga** - 项目管理
- **Wekan** - 看板工具

## 人工智能

这些节点用于人工智能和机器学习。

- **AiTransform** - AI数据转换
- **DeepL** - 翻译服务
- **OpenAI** - AI服务

## 其他服务

这些节点提供各种其他服务。

- **Aws** - 云服务
- **Cloudflare** - 网络服务
- **Crypto** - 加密操作
- **DateTime** - 日期和时间操作
- **Grafana** - 监控和可视化
- **HomeAssistant** - 家庭自动化
- **ICalendar** - 日历格式
- **Jwt** - JSON Web Token
- **Ldap** - 目录服务
- **Mindee** - 文档解析
- **Okta** - 身份管理
- **PhilipsHue** - 智能照明
- **RabbitMQ** - 消息队列
- **RssFeedRead** - 读取RSS源
- **Shopify** - 电子商务平台
- **Totp** - 双因素认证
- **WooCommerce** - 电子商务平台
