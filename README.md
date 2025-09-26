# edu

一个基于 Spring Boot 3.3 + Vue 3 + Element Plus 的现代化教务务课程网站，支持学生选课、教师授课、管理员管理等功能。

## 🚀 技术栈

### 后端
- **Java 21** - 编程语言
- **Spring Boot 3.3.5** - 应用框架
- **Spring Security** - 安全框架
- **Spring Data JPA** - 数据访问层
- **MySQL 8** - 数据库
- **JWT** - 身份认证
- **Maven** - 项目管理
- **Swagger** - API文档

### 前端
- **Vue 3** - 前端框架
- **TypeScript** - 类型支持
- **Element Plus** - UI组件库
- **Pinia** - 状态管理
- **Vue Router** - 路由管理
- **Axios** - HTTP客户端
- **Vite** - 构建工具

## 📁 项目结构

```
edu-system/
├── backend/                 # 后端项目
│   ├── src/main/java/com/edu/
│   │   ├── EduApplication.java
│   │   ├── config/         # 配置类
│   │   ├── security/       # 安全相关
│   │   ├── common/         # 通用类
│   │   ├── auth/           # 认证模块
│   │   ├── modules/        # 业务模块
│   │   └── ws/             # Web服务
│   ├── src/main/resources/
│   │   └── application.yml
│   └── pom.xml
├── frontend/               # 前端项目
│   ├── src/
│   │   ├── api/           # API接口
│   │   ├── components/    # 组件
│   │   ├── views/         # 页面
│   │   ├── stores/        # 状态管理
│   │   ├── router/        # 路由
│   │   ├── utils/         # 工具函数
│   │   └── styles/        # 样式
│   ├── package.json
│   └── vite.config.ts
├── database/              # 数据库脚本
│   └── init.sql
└── README.md
```

## 🛠️ 快速开始

### 环境要求

- Java 21+
- Node.js 20.19+ 或 22.12+
- MySQL 8.0+
- Maven 3.6+

### 1. 数据库准备

1. 确保MySQL服务正在运行，账号密码为 `root/root`

2. 创建数据库（如果不存在）：
```sql
CREATE DATABASE lzh CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci;
```

3. 导入初始化数据：
```bash
mysql -u root -p lzh < database/init.sql
```

4. 验证数据库连接：
启动后端服务后，查看控制台日志，应该看到 "✅ 数据库连接成功！" 的提示

### 2. 后端启动

1. 进入后端目录：
```bash
cd backend
```

2. 修改数据库配置（如需要）：
编辑 `src/main/resources/application.yml` 中的数据库连接信息

3. 启动应用：
```bash
mvn spring-boot:run
```

后端服务将在 http://localhost:8080 启动

### 3. 前端启动

1. 进入前端目录：
```bash
cd frontend
```

2. 安装依赖：
```bash
npm install
```

3. 启动开发服务器：
```bash
npm run dev
```

前端应用将在 http://localhost:3000 启动

## 👥 默认账号

| 角色 | 用户名 | 密码 | 说明 |
|------|--------|------|------|
| 管理员 | admin@edu.local | Admin@1234 | 系统管理员 |
| 教师 | teacher@edu.local | Teacher1 | 教师账号 |
| 学生 | student@edu.local | Student1 | 学生账号 |

## 🎯 功能特性

### 学生功能
- ✅ 课程浏览和选课
- ✅ 作业查看和提交
- ✅ 成绩查询
- ✅ 资料下载
- ✅ 公告查看

### 教师功能
- ✅ 课程管理
- ✅ 学生名单管理
- ✅ 作业发布和批改
- ✅ 成绩录入
- ✅ 资料上传

### 管理员功能
- ✅ 用户管理
- ✅ 课程管理
- ✅ 开课管理
- ✅ 公告管理
- ✅ 报表统计
- ✅ 系统设置

### 学生处功能
- ✅ 学生信息批量导入
- ✅ 导入任务管理

## 🔧 配置说明

### 后端配置

主要配置文件：`backend/src/main/resources/application.yml`

```yaml
# 数据库配置
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/lzh
    username: root
    password: root

# JWT配置
jwt:
  secret: edu-system-jwt-secret-key-2024-very-long-and-secure
  access-token-ttl-minutes: 30
  refresh-token-ttl-days: 7

# 文件存储配置
file:
  storage:
    type: local
    local:
      upload-path: uploads/
```

### 前端配置

环境变量文件：`frontend/.env`

```env
VITE_API_BASE=/api
VITE_WS_BASE=/ws
VITE_USE_MOCK=false
```

## 📚 API文档

启动后端服务后，访问以下地址查看API文档：

- Swagger UI: http://localhost:8080/api/swagger-ui.html
- API文档: http://localhost:8080/api/v3/api-docs

## 🗄️ 数据库设计

### 主要数据表

- `user` - 用户表
- `role` - 角色表
- `user_role` - 用户角色关联表
- `course` - 课程表
- `section` - 开课表
- `enroll` - 选课表
- `assignment` - 作业表
- `submission` - 作业提交表
- `grade_detail` - 成绩详情表
- `material` - 资料表
- `announcement` - 公告表
- `student_profile` - 学生档案表
- `audit_log` - 审计日志表

## 🔒 安全特性

- JWT身份认证
- 基于角色的访问控制（RBAC）
- 密码加密存储
- 请求限流
- 审计日志
- CORS跨域支持

## 🚀 部署说明

### 生产环境部署

1. **后端部署**：
```bash
cd backend
mvn clean package -DskipTests
java -jar target/edu-backend-1.0.0.jar
```

2. **前端部署**：
```bash
cd frontend
npm run build
# 将dist目录部署到Web服务器（如Nginx、Apache等）
```

3. **数据库配置**：
确保MySQL服务运行正常，并导入初始化脚本：
```bash
mysql -u root -p lzh < database/init.sql
```

## 🤝 贡献指南

1. Fork 项目
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 📞 联系方式

如有问题或建议，请通过以下方式联系：

- 项目Issues: [GitHub Issues](https://github.com/your-repo/edu-system/issues)
- 邮箱: your-email@example.com

## 🙏 致谢

感谢以下开源项目的支持：

- [Spring Boot](https://spring.io/projects/spring-boot)
- [Vue.js](https://vuejs.org/)
- [Element Plus](https://element-plus.org/)
- [MySQL](https://www.mysql.com/)

---

⭐ 如果这个项目对你有帮助，请给它一个星标！
