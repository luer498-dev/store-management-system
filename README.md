# 门店员工管理系统（微信 H5 版）

这是一个适合门店和员工使用的轻量管理系统，基于 Python + Flask + MySQL，面向微信 H5 浏览器访问，适合员工打卡、销售录入、排名、客户管理和老板看板。

## 业务功能

- 员工登录与注册
- 员工打卡
- 销售录入与统计
- 产品上架与库存管理
- 客户信息备注与偏好管理
- 权限控制：员工 / 店长 / 老板 / 财务
- 老板看板与财务模块
- 微信 H5 页面适配

## 角色权限

- 员工：只能打卡、录入自己的销售、查看自己数据
- 店长：管理本门店产品和员工数据
- 老板：查看全门店数据，能管理产品和权限
- 财务：仅能查看财务和结算数据

## 技术栈

- 后端：Python 3 + Flask
- 数据库：MySQL
- 前端：微信 H5 页面
- 认证：Session / Flask

## 目录结构

```text
store-management-system/
├── app.py
├── config.py
├── requirements.txt
├── schema.sql
├── start.sh
├── .env.example
├── .gitignore
├── README.md
├── app/
│   ├── __init__.py
│   ├── auth.py
│   ├── models.py
│   ├── permissions.py
│   ├── routes.py
│   ├── static/
│   │   └── css/
│   │       └── style.css
│   └── templates/
│       ├── login.html
│       ├── register.html
│       ├── dashboard.html
│       ├── punch.html
│       ├── sales.html
│       ├── products.html
│       ├── customers.html
│       └── finance.html
└── .venv/
```

## 本地启动

### 1）准备 MySQL

Mysql 必须本地启动，并创建数据库：

```sql
CREATE DATABASE store_system CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 2）导入表结构

```bash
mysql -u root -p < schema.sql
```

### 3）安装依赖

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 4）复制环境变量

```bash
cp .env.example .env
```

### 5）启动程序

```bash
python app.py
```

或者直接运行：

```bash
bash start.sh
```

访问：

```text
http://localhost:5000
```

## 默认账号

在本地第一次启动后，可访问：

- http://localhost:5000/seed

生成演示账号：

- 用户名：admin
- 密码：123456

也可以手动注册员工账号。

## 微信端使用方式

- 这个项目是 H5 页面，不是小程序
- 只需要把服务部署到公网地址，员工用微信浏览器打开即可
- 推荐使用微信内置浏览器访问

## 免费部署方案

以下方案都适合你：

- Render（免费试用方案）
- Railway（免费托管）
- 阿里云/腾讯云学生或低成本云主机
- 自己的 VPS 服务器 + Nginx

### 渠道说明

如果你只想先快速验证：
- 用本地开发环境测试更方便
- 等功能稳定后再部署到免费云平台

## 未来升级建议

可继续加入：

- 销售排行榜图表
- 每日/每周/月报表
- 提成自动计算
- 微信提醒通知
- Excel 导出
- 老板管理看板增强版
- 门店对比数据分析

## 仓库地址

https://github.com/luer498-dev/store-management-system

如果你想继续扩展，我可以继续帮你补这些功能：
- 老板总看板
- 财务结算模块
- 提醒通知
- 商品销量排行榜
- 微信授权登录
