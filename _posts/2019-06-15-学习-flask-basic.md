---
layout: post
title:  "学习 flask basic"
date:   2019-06-16 20:51:11
categories: basic
tags: [flask, web，basic ]
---

# flask 轻量级，灵活框架

## hello flask

1. 安装  ` pip install flask`
2. 倒入 `from flask import Flask`
3.  hello flask      

```python
# 导入Flask类
from flask import Flask

#Flask类接收一个参数__name__
app = Flask(__name__)

# 装饰器的作用是将路由映射到视图函数index
@app.route('/')
def index():
    return 'Hello Flask'


```