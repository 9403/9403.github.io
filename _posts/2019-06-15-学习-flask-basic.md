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

##  模版

* Jinja2 模版引擎
- 变量

  ```HTML
  <p>{{mydict['key']}}</p>
  
  <p>{{mylist[1]}}</p>
  
  <p>{{mylist[myvariable]}}</p>
  ```

    

  ```python
  from flask import Flask,render_template
  app = Flask(__name__)
  
  @app.route('/')
  def index():
      mydict = {'key':'silence is gold'}
      mylist = ['Speech', 'is','silver']
      myintvar = 0
  
      return render_template('vars.html',
                             mydict=mydict,
                             mylist=mylist,
                             myintvar=myintvar
                             )
  if __name__ == '__main__':
      app.run(debug=True)
  ```

- 反向路由

  ```python
  @app.route('/index')
  def index():
      return render_template('index.html')
  
  @app.route('/user/')
  def redirect():
      return url_for('index',_external=True)
  ```



## web 表单





```html
#模板文件
<form method='post'>
    <input type="text" name="username" placeholder='Username'>
    <input type="password" name="password" placeholder='password'>
    <input type="submit">
</form>
```

```python
from flask import Flask,render_template,request

@app.route('/login',methods=['GET','POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        password = request.form['password']
        print(username,password)
    return render_template('login.html',method=request.method)
```



## 控制语句

```python
@app.route('/user')
def user():
    user = 'dongGe'
    return render_template('user.html',user=user)
```

```python
@app.route('/loop')
def loop():
    fruit = ['apple','orange','pear','grape']
    return render_template('loop.html',fruit=fruit)
```


## 数据库操作

## 邮件扩展

## image图片上传

## 部署




  