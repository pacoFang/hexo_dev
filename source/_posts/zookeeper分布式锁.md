一 实现原理:
    1.zookeeper的有序节点,比如在/lock下创建有序节点
        node-000000,下一个节点是node-0000001
    2.zookeeper的临时节点,会话结束或者超时之后zookeeper
        自动删除节点
    3.事件监听,当节点变化时,如创建,删除,修改,子节点变更等操
        作时会通知客户端
    4.zookeeper操作的原子性,避免并发问题
 实现步骤:
    1.连接zookeeper,创建临时有序的子节点.
    2.判断是否是最小的子节点,如果不是,监听此父节点的变更消息,
        直到获取锁.
    3.执行业务代码.
    4.删除该节点.
    注意:当最小节点释放时,最好只通知下一个最小节点,可以避免羊群
 效应
 
二 实现:通过curator-recipes实现
        <dependency>
            <groupId>org.apache.curator</groupId>
            <artifactId>curator-recipes</artifactId>
            <version>3.0.0</version>
        </dependency>
注意.如果jar包版本和zookeeper版本不同,会报异常
Exception in thread "main" org.apache.zookeeper
.KeeperException$UnimplementedException: 
KeeperErrorCode = Unimplemented for 
/curator/lock/_c_e29cea17-ee1f-431d-
...

三 curator:curator是Netflix公司开源的一个zookeeper客户端,
    实现了操作zookeeper节点,锁,leader选举等功能