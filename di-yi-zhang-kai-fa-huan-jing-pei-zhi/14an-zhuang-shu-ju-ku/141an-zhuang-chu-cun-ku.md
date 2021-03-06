## 1.4.1 存储库的安装

在之前我们介绍了几个数据库的安装方式，但这仅仅是用来存储数据的数据库，但如果想要和 Python 操作的话也同样需要安装一些 Python 存储库，如 MySQL 需要安装 PyMySQL、mysqlclient，MongoDB 需要安装 PyMongo 等等，这里节我们来说明一下这些库的安装方式。

### 1、pip安装储存库

`pip3 install pymysql pymongo redis`

### 2、Python 数据库驱动 SQLAlchemy
如果觉得用 pymysql 操作数据库不方便的话，我们还可以尝试一下使用SQLAlchemy，这是一款用Python语言编写的数据库工具集，并且实现了对象关系映射（ORM）功能，同时提供了一套无需编写SQL语句便能执行数据库命令的通用接口。
而且，SQLAlchmey不仅是只包含了ORM—它也提供了另一组件（SQLAlchemy Core）来执行抽象于具体数据库（如PostgreSQL,SQLite等）实现的数据库操作。在某些方面来说，ORM只是一种相对于Core来说自动化执行创建，读取，更新和删除操作的额外功能而已。
同时，它的安装也很简单,直接使用 pip 安装即可：

`pip3 install sqlalchemy`

### 3、RedisDump的安装
RedisDump 是一个用于 Redis 数据导入导出的工具，是基于 Ruby 实现的，所以要安装 RedisDump 需要先安装Ruby。

首先，我们先安装ruby:

`sudo yum install ruby`

安装ruby完成之后，我们就可以执行 gem 命令(注意：使用gem可能需要配置科学上网环境)，它类似于 Python 中的 pip 命令，利用 gem 我们可以安装 RedisDump，执行完毕之后即可完成 RedisDump 的安装，命令如下：

`gem install redis-dump`

安装成功后就可以执行如下两个命令验证安装：

```
redis-dump
redis-load
```

在命令行下输入这两个命令，如果可以成功调用，则证明安装成功。

### 4. bsddb3 的安装
bsddb3 是用于 python 与 Berkeley DB交互的一个驱动，这里我们推荐使用 pip 安装：

`sudo BERKELEYDB_DIR=/usr/local/berkeleydb/ YES_I_HAVE_THE_RIGHT_TO_USE_THIS_BERKELEY_DB_VERSION=yes pip install bsddb3`

BERKELEYDB_DIR 是 本机 Berkeley BD 的安装路径，添加 sudo 是为避免权限问题。也可以通过下载源码手工安装 python setup.py install,　但要注意添加相应的环境变量，不然会因为版权问题无法安装。

#### 测试

```
import bsddb3 as db

db2 = db.btopen('spam.db', 'c')
for i in range(10):
    db2['%d'.encode('utf8') %i] = '%d'% (i*i)

db2.keys()
```

运行结果：

`[b'0', b'1', b'2', b'3', b'4', b'5', b'6', b'7', b'8', b'9']`

这样，我们就完成了 bsddb3 的安装。