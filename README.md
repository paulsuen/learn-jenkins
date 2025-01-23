# Jenkins CI/CD 学习项目

这是一个用于学习Jenkins CI/CD流程的示例项目。项目包含一个简单的Web应用，并通过Docker进行容器化部署，使用Jenkins实现持续集成和持续部署。

## 项目目标

1. 学习Jenkins的基本使用
2. 理解CI/CD流程
3. 掌握Docker容器化部署
4. 了解GitHub工作流程

## 项目结构

```
learn-jenkins/
├── app/                    # Web应用源代码
│   ├── static/            # 静态文件
│   ├── templates/         # HTML模板
│   └── app.py            # Flask应用主文件
├── tests/                 # 测试文件
├── Dockerfile            # Docker构建文件
├── docker-compose.yml    # Docker编排文件
├── Jenkinsfile          # Jenkins流水线定义
└── requirements.txt     # Python依赖文件
```

## 学习路线

### 第一阶段：环境准备
1. 安装Docker和Docker Compose
2. 配置GitHub仓库
3. 设置Jenkins容器

### 第二阶段：Web应用开发
1. 创建基础Flask应用
2. 编写单元测试
3. 容器化应用

### 第三阶段：CI/CD配置
1. 配置Jenkins流水线
2. 设置GitHub Webhook
3. 实现自动化部署

## 技术栈

- 后端：Python Flask
- 容器化：Docker
- CI/CD：Jenkins
- 版本控制：GitHub
- 测试：Python unittest

## 使用说明

详细的使用说明将在项目开发过程中逐步完善。每个阶段完成后，这里都会更新相应的操作指南。
