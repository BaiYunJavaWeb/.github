# BaiYunJavaWeb

# 2023.05.06: 当前项目停止开发

## 来访者, 你好呀 😊

这是 JavaWeb 实训周作业 是一个商店管理系统

## 通过 Docker 部署

### 1. 数据库配置

- 当前目录新建`mysql`文件夹

将数据库脚本`shopping.sql`放入该文件夹

### 2. docker-compose 配置

- 当前目录新建`docker-compose.yml`

```yaml
version: "3.9"
services:
  shopping_frontend:
    build: frontend
    ports:
      - "5173:5173"
  shopping_backend:
    build: backend
    ports:
      - "1314:1314"
    environment:
      - SPRING_DATASOURCE_URL=jdbc:mysql://db/shopping?serverTimezone=UTC
      - SPRING_DATASOURCE_USERNAME=root
      - SPRING_DATASOURCE_PASSWORD=123456
    depends_on:
      - db
  db:
    image: mysql:latest
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=123456
      - MYSQL_DATABASE=shopping
    volumes:
      - ./mysql:/docker-entrypoint-initdb.d
```

### 3. 目录结构

```
> mysql
    > anime.sql
> backend
    > ...
> frontend
    > ...
> docker-compose.yml
```

### 4. 部署项目

当前路径下执行`docker-compose up --build`

## 订单管理:

![houtai](https://raw.githubusercontent.com/BaiYunJavaWeb/.github/main/profile/houtai.png)

## 商品管理:

![shangpin](https://raw.githubusercontent.com/BaiYunJavaWeb/.github/main/profile/shangpin.png)

## 前台:

![qiantai](https://raw.githubusercontent.com/BaiYunJavaWeb/.github/main/profile/qiantai.png)

## 订单:

![dingdan](https://raw.githubusercontent.com/BaiYunJavaWeb/.github/main/profile/dingdan.png)

## 购物车

![gouwuche](https://raw.githubusercontent.com/BaiYunJavaWeb/.github/main/profile/gouwuche.png)
