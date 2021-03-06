# mongodb
### 基础教程

- 安装配置
    + 首先下载mongodb
        * [下载地址](https://www.mongodb.com/download-center/community)
    + 配置环境变量
        * 打开下载的mongodb文件，打到bin目录下，复制路径
        * 找到 环境变量-系统变量-Path,复制进去，注意分号，确认
    + 验证是否配置成功
        * `win+R` -- `cmd` -- 输入 `mongo`

- mongodb的常用指令
    + 启动运行mongodb
        * 命令行中输入 `mongod --dbpath 文件夹路径`
        * 命令行中输入 `mongod --dbpath 文件夹路径 --part 27018`即可更改端口为27018
    + 保持启动的命令行窗口，启动新的命令行窗口进行操作（相当于开启了一个数据库，对它操作时需要保持它是启动的）
    + 新窗口中首先进入mongo
    + 输入`show dbs`显示当前数据库
    + 连接到具体的数据库  `use 数据库名`
        + 如果你要连接的数据库不存在，会自动建立并连接

- mongodb的常用函数
    + 插入文档
        * `db.集合名.insert(文档)`
        * 其中db就是指已经连接的数据库
        * 集合名就是你要插入数据的集合的名字  例如：班级
        * 文档的格式是JSON  例如：`{name: 'hjw',sex: '男'}`
        * 系统会给文档自动添加`id`
        * 插入的文档归根结底是对象，就是可以插入一个数组，但数组中的项必须是对象
    + 查询文档
        * 查询该集合中的全部文档  `db.集合名.find()`
        * 查询某些特殊文档  例如性别为男  `db.集合名.find({sex: '男'})`
        * 查询某个特殊文档  `db.集合名.findOne({sex: '男'})`
        * 查询特定范围内的文档 `db.集合名.find({'age':{'gt':'10','lt':'30'}})`
        * 多条件查询   `db.集合名.find({$or:[{name:'xiaom'}],{age:'23'})`
    + 删除文档
        * 删除多个文档  `db.集合名.remove()`
        * 删除某个文档  `db.集合名.remove(条件,1)`
            * 如果相同条件有多个文档，会先删除较早生成的
    + 修改文档
        * 修改某个文档  `db.集合名.update({name:'hjw'},{$set:{name: '黄金文'}})`
        * 修改多个文档  `db.集合名.update({name:'hjw'},{$set:{name: '黄金文'}},{multi:true})`
    
- REPL环境（光标闪烁）
    + 定义： read eval print loop  即读一行 计算一行 打印一行 循环执行
    
- mongodb数据库的组成
    + 集合：相当于表，一个数据库包含多个集合，集合中包含许多文档
    + 文档：类似MySQL中的一条数据
    