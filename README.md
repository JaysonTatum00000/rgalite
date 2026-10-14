# 用户认证有两个体系

# 项目架构
## 前后不分离，服务端渲染
- 用户认证一般用会话 session

## 前后端分离，客户端渲染
- 用户认证一般用jwt



def __truediv__(self, key):
        try:
            return self.with_segments(self, key)
        except TypeError:
            return NotImplemented

可以使用__truediv__魔术方法重写/运算符     


 def __rtruediv__(self, key):
        try:
            return self.with_segments(key, self)
        except TypeError:
            return NotImplemented

# 当python遇到a/b
先尝试a.__truediv__(b) 也就是执行a的正常除法方法
如果a没有实现      __truediv__
再尝试 b.  __rtruediv__(a),也就是说尝试执行b的批向除法方法  


# sqlalchemy版本区别
语法对比
定义列的时候
方面        老写法    新写法
基础        Column    Mapped[]+mapped_column()
类型指定    作为参数   作为类型注解 
主键        primary_key=True  primary_key=True
默认值      default=value default=value
可空性      nullable=True    nullable=True



https://dev.mysql.com/downloads/mysql/
MySQL Community Server 8.4.7 LTS
Select Version:
8.4.7 LTS


https://www.navicat.com.cn/download/navicat-premium-lite


#id为什么不用自增？用这种随机数会不会有概率一样？ 不用自增是否为了安全？

# 一般来说如果你的系统支持分布式的，一般不使用自增
# 现在用的可不是随机数，用的是UUID 可以保证这个值是真正唯一的任何地方产生的任意一个UUID都不会有相同的值

旧版本
https://ai.docs-hub.com/html/sqlalchemy.html

新版本
https://rag.docs-hub.com/html/sqlalchemy.html

session={}
kb={a:1,b:2}
#将kb添加到session中，对象会进入挂起的状态，等待处理
session.add(kb)
# 发送SQL到数据库里 执行 insert update delete等语句，获取数据库生成生成的自增ID和默认值等 对象状态为持久
session.flush(kb) 执行flush以后kb已经最新的了，正常来说 不需要再执行refresh
# 从数据库中加载最新的数据 强制从数据库中重新加载对象的所有的属性，确保对象的状态和数据库完全同步，可以获取其它用户最新的修改
session.refresh(kb)
# refresh指的是从数据库中查询加载最新的数据 加载到内存中的kb对象中

#flush之后是不是需要refresh
大部分情况是不需要的

什么时候需要再次调用refresh
- 数据库里非常复杂的触发器
- 有其它的进行在同步修改数据
- 要百分百确定数据完全一致




# sqlalchemy 不能自动更改表吗？
SQLAclchemy默认不会自动更改表结构，这是它的默认行为，是为了安全
- 自动更改表结构可能会
  - 数据丢失
  - 生产环境意外修改
  - 难以回滚
  - 破坏现有数据完整性

  alembic是SQLAclchemy作者开发的数据库迁移工具
  

# 你可以认为refresh就是 执行SQL语句
而执行的SQL语句需要commit才能真正写入数据库


这里可以在哪里拦截所有请求，给所有接口添加接口鉴权，免得一一添加鉴权装饰器

request.endpoint 就是当前的路径

# 鉴权方式  哪种方式较为常用的
- 什么时候集中管理路由权限
- 什么分散管理路由权限

Nest课程是详细讲了bootstrap5



1. 普通聊天
messages = [
    ('system','你是一个乐于助人的好助手，请热心的回答用户的问题'),
    ('human',"1+1=?")
]
2. 知识库聊天

messages = [
    ('system','你是一个关于利用知识加回答问题的好助手，请热心的回答用户的问题'),
    ('human',"
    文件内容如下：
    {context}
    用户的问题如下
    {question}1+1=?

    请基于文档回答问题，如果文档中没有相关的答案，则回答不知道
    
    ")
]