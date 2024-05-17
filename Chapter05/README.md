# [CHAPTER05] 基于规则的对话管理

## RASA版本和项目依赖

本书所用代码均在RASA3.0.X版本中完成。 读者可以使用：

```shell
pip install --no-deps -r ../full_requirements.txt
```

完成项目代码的依赖安装。

## 训练RASA模型

```shell
rasa train
```

## 使用API密钥启动RASA动作服务器

```shell
SENIVERSE_KEY=xxx rasa run actions
```

`XXX`是我们可以从[https://www.seniverse.com/](https://www.seniverse.com/)获取的API密钥。

对于WINDOWS用户，可以使用直接修改代码的方式，快速更改API密钥。具体操作如下：

1. 打开`service/weather.py`文件，定位到第9行，也就是：
   `KEY = os.getenv("SENIVERSE_KEY", "")  # APIKEY`这一行
2. 将其中的`""`替换成API密钥。代码修改效果如下：
   `KEY = os.getenv("SENIVERSE_KEY", "ThisIsYourKey")  # API key`

## 启动RASA服务器

```bash
rasa run --cors "*"
```

## 启动网页客户端

```bash
python -m http.server
```

使用浏览器打开链接: [http://localhost:8000/](http://localhost:8000/)

尝试输入一些查询，例如"上海今天的天气如何"并查看响应。

演示效果如下所示：

![](media/demo.png)

玩得开心！
