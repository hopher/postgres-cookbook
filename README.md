# postgres-cookbook
PostgreSQL Cookbook


## 序列函数

| 函数                              | 返回类型 | 描述                                                         |
| --------------------------------- | -------- | ------------------------------------------------------------ |
| nextval(regclass)                 | bigint   | 递增序列对象到它的下一个数值并且返回该值。这个动作是自动完成的。即使多个会话并发运行nextval，每个进程也会安全地收到一个唯一的序列值。 |
| currval(regclass)                 | bigint   | 在当前会话中返回最近一次nextval抓到的该序列的数值。(如果在本会话中从未在该序列上调用过 nextval，那么会报告一个错误。)请注意因为此函数返回一个会话范围的数值，而且也能给出一个可预计的结果，因此可以用于判断其它会话是否执行过nextval。 |
| lastval()                         | bigint   | 返回当前会话里最近一次nextval返回的数值。这个函数等效于currval，只是它不用序列名为参数，它抓取当前会话里面最近一次nextval使用的序列。如果当前会话还没有调用过nextval，那么调用lastval将会报错。 |
| setval(regclass, bigint)          | bigint   | 重置序列对象的计数器数值。设置序列的last_value字段为指定数值并且将其is_called字段设置为true，表示下一次nextval将在返回数值之前递增该序列。 |
| setval(regclass, bigint, boolean) | bigint   | 重置序列对象的计数器数值。功能等同于上面的setval函数，只是is_called可以设置为true或false。如果将其设置为false，那么下一次nextval将返回该数值，随后的nextval才开始递增该序列。 |



## 参考资料

- [PostgreSQL 基本语法](https://blog.csdn.net/taoshujian/article/details/60882172)