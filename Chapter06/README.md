# [CHAPTER06] 基于知识库的问答

## RASA版本和项目依赖

本书所用代码均在RASA3.0.X版本中完成。读者可以使用：
```shell
pip install --no-deps -r ../full_requirements.txt
```

完成项目代码的依赖安装。

## 训练RASA模型

```bash
rasa train
```

## 启动RASA动作服务器

### 内置知识库

```shell
rasa run actions
```

### 使用自定义NEO4J知识库

#### 安装DOCKER

您需要DOCKER才能使用（可选）自定义NEO4J知识库功能.
您可以在[https://www.docker.com/](https://www.docker.com/)找到如何将DOCKER安装到您的系统。

#### 安装NEO4J库

为了使用（可选）自定义NEO4J知识库功能，你还需要安装`NEO4J`：

```bash
pip install neo4j~=4.1
```

这一步骤是可选的，因为在最开始的步骤中，已经安装了相关的依赖。

#### 启动NEO4J服务器

拉取DOCKER镜像：

```bash
docker pull neo4j:4.1
```

运行DOCKER：

```bash
docker run --rm --env=NEO4J_AUTH=none --publish=7474:7474 --publish=7687:7687 neo4j:4.1
```

保持这个NEO4J运行。

#### 将图插入到NEO4J

```bash
python ./data_to_neo4j.py
```

#### 使用自定义NEO4J知识库启动RASA动作服务器

```bash
USE_NEO4J=1 rasa run actions
```

## 启动RASA服务器

```bash
rasa run --cors "*"
```

## 启动网页客户端

```bash
python -m http.server
```

使用浏览器打开链接: [http://localhost:8000/](http://localhost:8000/)

尝试输入一些查询，例如“给我列出一些周杰伦的歌曲”并查看响应。

演示效果如下所示：

![](media/demo.png)

玩得开心！

## 探索GRAPH

启动NEO4J后，您可以使用NEO4J浏览器进行可视化和GRAPHQL调试.
访问[http://localhost:7474](http://localhost:7474) ，使用`NEO4J`作为用户名和密码。

演示效果如下所示：

![](media/demo2.png)
