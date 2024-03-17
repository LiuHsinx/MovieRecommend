# 基于协同过滤算法的电影推荐系统

**数据集**：MovieLens的**ml-latest-small**数据集（csv文件），有600多个用户，9700多部电影，10万条评分记录

**数据库信息**：ml-latest-small提供了一个CSV文件，存入数据库处理后得到系统需要的表：**movie_genre**（电影id对应的电影类别）、**movie**（电影id，电影名，imdb_id、发布时间、时长、简介、导演、编剧和主演等）、**movie_hot**（评分数目top100的电影id）、**movie_similarity**（电影与电影之间相似度，基于其类别做ItemCF，用于详情页——喜欢该电影的还喜欢）、**movie_rating**（用户对电影的评分数据）

**技术栈**：使用Django搭建web框架，数据库MySQL，使用Navicat操作数据库，前端用的bootstrap做渲染

**算法原理**：使用UserCF做推荐，具体的，基于用户对电影的评分数据，我们对其中两两用户都使用余弦相似度算法计算相似度（用户a和b共同喜欢的电影/用户a和b喜欢的电影总数），相似度矩阵建立好之后，为当前用户推荐与其相似度高的用户喜欢且自己没看过的的电影。

**环境：**

1. Django 3.2
2. Python 3.10

**运行方法：**

本项目运行需要数据库，database文件夹里面提供了我的数据库备份文件。你可以直接导入我的数据库

1. 进入setting.py——DATABASES 字段下设置数据库信息，命名必须为**movie_recommend_db**
2. 数据库可以先进行models的迁移：python manage.py migrate 然后直接导入sql文件，最后启动服务器 python manage.py runserver 即可打开链接

如果你想从头开始做并导入自己的数据，你必须先连接好数据库并迁移model到数据库上，然后可以用jupyter notebook对数据进行清洗用Navicat导入文件






