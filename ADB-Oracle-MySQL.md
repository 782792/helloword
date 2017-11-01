指标|	ADB	|Oracle|	MySQL
--|--|--|--
类型	|关系型数据库|	关系型数据库|	关系型数据库
架构|	分布式 share nothing|	集中式 share everything|	分布式 share nothing
多线程or多进程|	多进程|	多进程	|多线程
License费用|	社区版本开源，免费使用	|按照CPU核数收费，价格昂贵|	社区版本开源，免费使用。商业版本从Oracle公司购买授权
SLA	|7x24，一般问题不会过夜，重大严重问题不会超过两天|	一般用户MOS发起sr，高级用户联系SSC/ACS部门，现场服务每人日8000RMB（8小时，加班2倍，节假日3倍）|	社区版本无技术支持，商业版本联系Oracle公司销售代表获取技术支持
高可用|	hot standby	|Active Data Guard	|主从复制
容灾|	自研双向同步工具|	底层存储复制、flashcopy等	|PXC/基于proxy的多主方案
数据分片|	支持|	12.2版本开始提供，未发布，细节不详	|支持
导出导入|	pg_dump/pg_dumpall/pg_restore|	exp/expdp/imp/impdp	|mysqldump
备份恢复管理|	barman	|rman	|xrabackup
基于时间点的恢复(PITR)	|支持|	支持	|支持
归档|	支持|	支持|	支持
分布式事务控制|	支持|	支持|	支持
可视化监控展示	|ADBmonitor	|Oracle EM	|Percona Monitoring and Management
命令行客户端|	psql|	sqlplus	|mysql
官方图形化客户端|	pgadmin|	sqlpldeveloper	|MySQL GUI Tools
JDBC接口|	支持	|支持	|支持
C/C++接口|	libpq|OCI|	libmysql
功能扩展|	需要的功能几乎均能在社区找到相应的插件，非常方便|	不支持	|支持
Oracle迁移	|Oracle语法85%兼容，应用几乎无需改写代码| |		语法改动很多，对应用要求很高
稳定性|	普通x86上大量严格的暴力边界测试，
生产环境持续稳定的运行|	多年的商业数据库，稳定性不错	|简单业务稳定性很好
水平扩缩容|	很方便的在集群中添加删除node|	rac架构添加实例，依然需要share everything	|支持
多租户(在一个实例中创建多个database)|	原生支持|	12c版本开始支持	|不支持，需要应用自己实现
dblink|	支持|	支持|	支持/功能有限
查询其他类型数据库|	丰富的fdw插件|	oracle gateway	|不支持
double cache(db cache && os cache)	|支持|	不支持	|不支持
资源控制(类似linux的limit)	|支持|	支持|	支持
访问控制|	pg_hba.conf文件	|sqlnet.ora	|权限表
数据undo|	MVCC|	undo tablespace	|undo log
数据redo|	WAL log	|online redo log|	redo log
数据完整性约束(包括主键、外键、唯一、check等约束)|支持	|支持|	支持
存储过程/函数/触发器|	支持	|支持|	支持
数据库内部job|	pg_cron	|dbms_job/dbms_scheduler|	Event Scheduler
用户自定义类型|	支持|	支持|	不支持
秒以下的时间类型|	支持	|支持	|支持
自增字段|	支持|	不支持|	支持
物化视图|	支持|	支持|	不支持
序列|	支持|	支持|	不支持
非结构化数据|	支持json格式|	不支持	|5.7.7版本后支持
空间地图数据|	支持|	不支持|	不支持
XML	|支持|	支持|	支持
全文搜索|	支持|	支持|	支持
复杂查询|	支持|	支持|	语法支持，但性能有限
子查询(包括简单子查询和标量子查询)|	支持|	支持|	支持，但性能很差
并行查询|	3.1版本支持|	支持|	不支持
局部索引|	有	|不支持	|不支持
复合索引|	支持|	支持|	支持
位图索引|	不支持|	支持|	支持
函数索引|	支持|	支持|	不支持
分析函数|	支持|	支持|	不支持
分区表	|通过继承表实现	|丰富的分区特性|	支持
窗口函数|	支持|	支持|	官方分支不支持
外部函数(使用C/Python等语言在DB中编写函数)	|支持|	支持|	不支持
表连接类型	|nest loop/hash join/sort merge join|	nest loop/hash join/sort merge join|	nest loop
性能优化工具与度量信息|	丰富的日志信息和表、索引的统计信息	|awr和ash提供了丰富的诊断信息|	内部性能视图和对象统计信息
优化器提示信息|	安装插件pg_hint_plan后支持|	原生丰富的hint提示	|支持，数量有限
