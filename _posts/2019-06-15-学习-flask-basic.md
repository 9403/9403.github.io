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
    
# Flask应用程序实例的run方法启动WEB服务器
if __name__ == '__main__':
    app.run()
```

4. Debug

   config.py 	` DEBUG=True`

   `app.config.from_object(config)`

   `app.debug = True`

5. port 默认5000

6. ```
   app.run(host='0.0.0.0',port=8030,debug=True)
   ```
## flask route 


- 路由器传参数

```python
# 路由传递的参数默认当做string处理，这里指定int，尖括号中冒号后面的内容是动态的
@app.route('/user/<int:id>')
def hello_itcast(id):
    return 'hello itcast %d' %id
```

- 返回状态码

  ```
  @app.route('/')
  def hello_itcast():
      return 'hello itcast',999
  ```
  
## 模版

- Jinja2 模版引擎

- 模版基本语法

  ```
  {% if user %}
      {{ user }}
  {% else %}
      hello!
  <ul>
      {% for index in indexs %}
      <li> {{ index }} </li>
      {% endfor %}
  </ul>
  ```

- 变量

  ```
  <p>{{mydict['key']}}</p>
  
  <p>{{mylist[1]}}</p>
  
  <p>{{mylist[myvariable]}}</p>
  ```


