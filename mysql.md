## 从表中查询数据
* select * from 表名称   *(表示所有列)
* select 列名称 from 表名称

## 插入数据
* insert into 表名称 (列1,列2) values (值1,值2)

## 更新数据
* update 表名称 set 列名称 = 新值 where 列名称 = 某值
* 更新某一行中的若干列 set 列名称 = 新值, 列名称 = 新值

## 删除数据
* delete from 表名称 where 列名称 = 值

## 运算符
* = 等于 <>/!= 不等于 > 大于 <小于 >= 大于等于 <=
* between 某个范围 like 搜索某种模式
* and 同时满足  or 或者

## 排序
* select * from 表名称 order by 列名称  asc默认升序  desc降序

## count(*)  函数返回查询结果的总数据条数
* select count(*) from 表名称

## as 作为别名
* select count(*) as total from 表名称