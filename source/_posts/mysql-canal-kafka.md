# canal 加 kafka
一.mysql
1.设置my.cnf/my.ini
log-bin=mysql-bin
binlog-format=ROW
server_id=1
2.show master status 查看状态

二.canal
1.设置mysql地址和用户名密码
// slaveId 不能与 my.cnf 中的 server-id 项重复
canal.instance.mysql.slaveId = 1234
canal.instance.master.address = 127.0.0.1:3306
canal.instance.dbUsername = canal
canal.instance.dbPassword = canal
2.启动
bin/startup.sh

三.单机版zookeeper
默认即可, 修改conf/zoo_sample.cfg为zoo.cfg

四.单机版kafka
1.启动server
./bin/kafka-server-start.sh ./config/server.properties
2.创建主题
./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test