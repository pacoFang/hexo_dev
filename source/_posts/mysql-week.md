mysql 日期按周group by

1、select subdate('2019-05-16',date_format('2019-05-16','%w')-1)
这种写法不对。虽然可以得到周一，但是聚合时一周是从周日开始的

2.select str_to_date(concat(yearweek('2019-01-01',1),'1'),'%Y%u%w')
新的写法，校验没问题
