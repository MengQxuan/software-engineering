# software-engineering

2025春 软件工程 “智慧海洋牧场可视化系统”

## 数据库建立：
```bash
mysql -u root -p
# 输入密码后运行，注意文件路径修改为你的电脑上的路径
source E:\Edesktop\software-engineering\DataBase_Setup\setup_database.sql
```
后面添加数据可以运行database_setup的目录下的python文件
现在已经成功实现数据库+后端+前端连通

---
## 项目启动：
```python
python run.py
```

## 目前进度
* 数据库的初步搭建并和项目连接，登录和跳转的前后端逻辑基本实现
* 注册功能初步实现
* 感觉可以注册和登录分离成两个页面
* 前后端已经调通了，数据库交互问题也不大
* 中期阶段应该就差可视化部分了
* 智能问答已实现
* 图片识别实现
* 体长预测实现

## 注意事项：
* 如果在后端配合的时候，页面跳转出现了类似404 NOT FOUND的提示，大概率是因为这个路由没有在蓝图中注册，在app/routes/这个目录下，找一个或者新建一个py文件（新建的话还要再init.py添加新的蓝图），添加对应的文件路径即可。
* 目前版本的项目结构管理和功能划分还处于能跑就行的阶段，后续有待完善。。。。
* 数据库目前的数据只有部分，后面有需要可以更新database_setup的sql文件，以便后续部署。
* 使用前记得配置一下修改一下config.py文件，毕竟我们的mysql的登录密码不太可能一样
* 注意使用自己的API，在.env那里替换