## tutorial 1
###  数据库简介
数据库出现之前数据持久化的常见手段是**将数据按照一定规则存放在 txt 格式等类似的文本文件中进行管理。**

这样做虽然能够解决持久化的问题，但是安全性、可移植性、一致性、性能、备份等功能非常难实现，并且也非常不利于数据的查询和修改，也很难通过日志追踪修改记录进行回滚或者中断。

![alt text](pic_1.png)

在各位大牛的耕耘下，诞生了数据库系统原理这门理论。一代又一代人不断的迭代，将这一门理论具象化为高级语言 + 存储引擎的方式。市面上有很多种数据库，从设计模式上主要分为两种 - `关系型数据库`、`非关系型数据库`。我们熟悉的`SQL`则是`关系型数据库`的操作语言，通过简单的一句话完成复杂的过程，这就是在川菜馆点一份水煮肉片，只需要玩会儿手机就能等到一碗热腾腾的水煮肉片的感觉！不同`关系型数据库`“说的语言”可能不一样，但这绝不是闽南语和朝鲜语的差别！他们更像美国南方和北方的口音差异，只有很少的部分不一样！接下来，我会介绍主流`关系型数据库`之一的 Mysql ，学会了怎么使用 Mysql 就相当于学会了使用绝大部分的 `关系型数据库` 比如 Oracle 、PostgreSQL 、MariaDB、SQLite... 

总之，学习`SQL`对于你来讲是绝对正确的事情，你能获得专业的技巧、逻辑能力的提升、还能共鸣前人在做这些事情时候激动的心情、最重要的，你能离理想中的自己更近一步！

###  docker简介
###  MacOS安装docker
首先，我们需要安装Homebrew。使用Command + Space打开搜索，输入`Terminal`打开终端，然后，输入如下指令进行安装：

如果你是`Intel`芯片，使用：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

如果你是`M`芯片，使用：

```bash
/bin/bash -c "$(curl -fsSL https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)"
```

我们可以把鼠标移到左上角苹果，点击`关于本机`查看自己Mac芯片的版本，然后在处理器一栏看关键字`Intel`或者`M~`。图中展示的是一台`Intel`芯片的Mac。

![alt text](image.png)

安装完毕后进入如下链接，根据自己的芯片版本选择对应的docker下载并安装：

```bash
https://dockerdocs.cn/docker-for-mac/install/#google_vignette
```

安装docker:

![alt text](image-1.png)

###  拉取 Mysql 镜像

打开docker，搜索并拉取 Mysql 镜像：

![alt text](image-2.png)

![alt text](image-3.png)

拉取完成后，使用Command + Space打开搜索，输入`Terminal`打开终端，输入下面的指令查看 Mysql 镜像是否被成功拉取：

```bash
docker images -a
```

**上述命令中：**

`-a` 表示展示所有容器

![alt text](image-6.png)

###  进入Mysql

**我们先使用指令创建 Mysql 实例：**

执行下面的指令创建一个 Mysql 示例，并且为这个示例设置账号密码：

```bash
docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
```

**上述命令中：**

`--name mysql-test` 表示创建实例`mysql-test` 

`-e MYSQL_ROOT_PASSWORD=123456` 表示`root`的密码是`123456`

`-p 3306:3306` 表示`宿主机ip:端口号`为`3306:3306`

`-d mysql` 表示为`mysql`开启一个`守护进程`

![alt text](image-8.png)

成功启动 Mysql 服务后，会生成一个哈希值，然后我们可以使用以下指令查询当前运行中的容器：

```bash
docker ps

or

docker ps -a
```
**上述命令中：**

`docker ps` 表示展示当前运行中的容器

`docker ps -a` 表示展示所有容器

![alt text](image-7.png)

接下来，我们通过下面命令执行该实例：

```bash
docker exec -it mysql-test bash -l
```

![alt text](image-9.png)

执行成功后，登陆 Mysql 的`root`用户：

```bash
mysql -uroot -p
```

能出现上述图片，证明 Mysql 启动成功！

![alt text](image-10.png)

你可以使用下面的指令退出 Mysql ：

```bash
exit
```

然后使用下面的指令退出 docker 实例：

![alt text](image-11.png)

```bash
exit
```

![alt text](image-12.png)
###  库表介绍
###  基础语句
###  小结
###  习题
```mysql
show databases; -- 显示所有的数据库

use sys; -- 使用sys这个数据库

show tables; -- 展示sys这个数据库所有的表

select * from host_summary; -- 查询host_summary这张表的所有字段

select * from host_summary where host = 'localhost'; -- 查询host_summary这张表host='localhost'的所有数据

show tables like '%host_summary'; -- 输出什么？

show tables like 'host_summary%'; -- 输出什么？

show tables like '%host_summary%'; -- 输出什么？

-- 得出什么？


-- 在host_summary中查找host为localhost且total_memory_allocated为76.91 MiB的数据的statements
select statements from host_summary where host = 'localhost' and total_memory_allocated = '76.91 MiB';

-- 题目
-- 创建一个名为test1数据库，一个名为test2数据库。

-- 删除名为test2数据库。

-- 在test1数据库创建一个名为test1_table的表，这张表有两个字段：name、id；name的数据类型是varchar 、id的数据类型是int
-- 示例如下
-- create table test_table(
--   stu_id VARCHAR,
--   age INT,
--   );
```
