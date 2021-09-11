# mysqldump
mysqldump 源码修改，基于5.7.35
修改实现的功能：
1. 为 -A,--all-databases 选项增加数据库过滤（排除）功能
2. 为 -w,--where 选项增加条件扩展，当指定的条件以#打头时，表示后面跟的是存储过程，由存储过程返回当前表的筛选条件。存储过程包含两个固定参数：dbname,tbname
3. 扩展--master-data选项值，增加3、4，功能对应原始的1。2，区别在于使用3,4时，如果未开启binlog，则不会报错
4. 增加使用环境变量MYSQLUSER、MYSQLPASSWORD获取用户名和密码的功能。如果未指定-u,--user，则使用MYSQLUSER；如果未指定-p,--password，则使用MYSQLPASSWORD

代码中使用 // zoujian.zjcxc --> 标记出修改的部分

编译方法：
1. 从mysql官网下载源码
2. 使用修改后的 mysqldump.c 文件覆盖源码中的文件，文件位于 client 子目录
3. 参考官网说明，对mysql源码进行编译
