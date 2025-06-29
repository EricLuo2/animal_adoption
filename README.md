# 宠物领养系统 (Animal Adoption System)

## 项目简介

宠物领养系统是一个基于Spring Boot + Vue.js的现代化Web应用，旨在为流浪动物和爱心人士搭建一个安全、便捷的领养平台。系统提供完整的宠物领养流程管理，包括动物信息展示、领养申请、救助管理、用户互动等功能。

## 功能特性

### 🏠 核心功能
- **宠物领养管理** - 完整的领养流程，从申请到审核
- **流浪动物救助** - 救助站管理和救助记录
- **用户互动平台** - 论坛交流、评论互动
- **科普教育** - 宠物知识科普文章
- **活动管理** - 线下领养活动组织
- **捐赠管理** - 爱心捐赠物资管理

### 🔐 用户系统
- **多角色权限管理** - 管理员、普通用户权限分离
- **邮箱验证找回密码** - 安全的密码重置机制
- **个人信息管理** - 完整的用户资料维护
- **头像上传** - 支持用户头像个性化

### 📱 用户体验
- **响应式设计** - 适配多种设备屏幕
- **现代化UI** - 基于Element UI的美观界面
- **实时通知** - 系统消息和状态更新
- **搜索筛选** - 便捷的信息查找功能

## 技术架构

### 后端技术栈
- **Spring Boot 2.5.9** - 主框架
- **MyBatis Plus 3.5.1** - ORM框架
- **MySQL 8.0** - 数据库
- **JWT** - 身份认证
- **JavaMail** - 邮件服务
- **Swagger** - API文档
- **Hutool** - 工具库

### 前端技术栈
- **Vue.js 2.x** - 前端框架
- **Element UI** - UI组件库
- **Vue Router** - 路由管理
- **Vuex** - 状态管理
- **Axios** - HTTP客户端

### 开发工具
- **Maven** - 项目构建
- **Node.js** - 前端包管理
- **Git** - 版本控制

## 项目结构

```
animal_adoption/
├── animal-server/          # 后端服务
│   ├── src/main/java/
│   │   └── com/example/
│   │       ├── controller/     # 控制器层
│   │       ├── service/        # 服务层
│   │       ├── entity/         # 实体类
│   │       ├── mapper/         # 数据访问层
│   │       ├── config/         # 配置类
│   │       ├── utils/          # 工具类
│   │       └── common/         # 公共类
│   ├── src/main/resources/
│   │   ├── mapper/            # MyBatis映射文件
│   │   └── application.yml    # 配置文件
│   └── pom.xml               # Maven配置
├── animal-front/            # 前端应用
│   ├── src/
│   │   ├── components/       # 公共组件
│   │   ├── views/           # 页面组件
│   │   ├── router/          # 路由配置
│   │   ├── store/           # 状态管理
│   │   └── utils/           # 工具函数
│   ├── public/              # 静态资源
│   └── package.json         # 依赖配置
└── SQL/                     # 数据库脚本
    ├── db_animal.sql        # 主数据库脚本
    └── verification_code.sql # 验证码表脚本
```

## 核心模块

### 1. 用户管理模块
- 用户注册、登录、注销
- 角色权限管理
- 个人信息维护
- 密码安全重置

### 2. 宠物管理模块
- 流浪动物信息录入
- 动物状态跟踪
- 领养状态管理
- 绝育和疫苗记录

### 3. 领养申请模块
- 在线申请提交
- 申请状态跟踪
- 审核流程管理
- 领养结果通知

### 4. 救助管理模块
- 救助站信息管理
- 救助记录维护
- 喂养点管理
- 走失宠物登记

### 5. 社区互动模块
- 论坛发帖回复
- 评论互动系统
- 科普文章发布
- 活动信息发布

### 6. 捐赠管理模块
- 捐赠物资登记
- 捐赠记录管理
- 物资使用跟踪

## 数据库设计

### 主要数据表
- `sys_user` - 用户信息表
- `animal` - 动物信息表
- `applcation` - 领养申请表
- `article` - 论坛文章表
- `donate` - 捐赠记录表
- `verification_code` - 验证码表
- `sys_role` - 角色表
- `sys_menu` - 菜单表

## 安装部署

### 环境要求
- JDK 1.8+
- MySQL 8.0+
- Node.js 12+
- Maven 3.6+

### 后端部署
```bash
# 1. 克隆项目
git clone [项目地址]
cd animal_adoption

# 2. 配置数据库
mysql -u root -p
source SQL/db_animal.sql
source SQL/verification_code.sql

# 3. 修改数据库配置
# 编辑 animal-server/src/main/resources/application.yml

# 4. 编译运行
cd animal-server
mvn clean package
java -jar target/springboot-0.0.1-SNAPSHOT.jar
```

### 前端部署
```bash
# 1. 安装依赖
cd animal-front
npm install

# 2. 开发环境运行
npm run serve

# 3. 生产环境构建
npm run build
```

### 配置说明
```yaml
# application.yml 主要配置
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/db_animal
    username: your_username
    password: your_password

# 文件上传配置
files:
  upload:
    path: D:/animal_adoption/animal-server/file/
```

## 安全特性

### 身份认证
- JWT Token认证
- 密码加密存储
- 邮箱验证码找回密码
- 会话管理

### 权限控制
- 基于角色的访问控制(RBAC)
- 菜单权限动态加载
- 接口权限验证
- 数据权限隔离

### 数据安全
- SQL注入防护
- XSS攻击防护
- 文件上传安全验证
- 敏感信息加密

## API文档

系统集成了Swagger文档，启动后端服务后访问：
```
http://localhost:9090/swagger-ui.html
```

## 开发指南

### 代码规范
- 遵循阿里巴巴Java开发手册
- 使用统一的代码格式化工具
- 添加必要的注释和文档
- 遵循RESTful API设计规范

### 提交规范
```
feat: 新功能
fix: 修复bug
docs: 文档更新
style: 代码格式调整
refactor: 代码重构
test: 测试相关
chore: 构建过程或辅助工具的变动
```

## 测试

### 单元测试
```bash
cd animal-server
mvn test
```

### 集成测试
- API接口测试
- 数据库连接测试
- 邮件发送测试

### 前端测试
```bash
cd animal-front
npm run test:unit
```

## 部署方案

### 开发环境
- 本地开发服务器
- 热重载支持
- 调试工具集成

### 生产环境
- Docker容器化部署
- Nginx反向代理
- HTTPS安全传输
- 数据库主从复制

## 监控运维

### 日志管理
- 统一日志格式
- 日志级别配置
- 错误日志监控

### 性能监控
- 接口响应时间
- 数据库查询性能
- 内存使用情况

## 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 版本历史

### v2.0.0 (2024年)
- ✨ 新增邮箱验证找回密码功能
- 🔒 增强账户安全性
- 🎨 优化用户界面
- 🐛 修复已知问题



## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 联系方式

- 项目维护者：[Donghui Luo]
- 邮箱：[er1clu0296@gmail.com]

## 当前进展

邮箱验证功能还在开发中

## 致谢

感谢所有为这个项目做出贡献的开发者和用户！
感谢"https://github.com/YanSiPeng/db_animal"开源代码，本项目很多地方借鉴了该库中的代码

---

**注意**: 这是一个开源项目，欢迎社区贡献和改进。如果您发现任何问题或有改进建议，请通过Issue或Pull Request与我们联系。
