### 任务爬取项关联表 task_crawl_relate

| 字段名         | 类型      | 说明                                                         | 索引        |
| -------------- | --------- | ------------------------------------------------------------ | ----------- |
| id             | int       | 自增id                                                       | primary_key |
| taskId         | char(100) | 任务id                                                       | normal      |
| crawlId        | char(100) | 爬取项id                                                     |             |
| crawlTimeType  | char(30)  | 爬取时间类型：week:一周内 month:一月内 customization：自定义 none:无限制 |             |
| crawlStartTime | int       | 自定义开始时间                                               |             |
| crawlEndTime   | int       | 自定义结束时间                                               |             |
| crawlCount     | int       | 爬取数量                                                     |             |
| createTime     | int64     | 创建时间                                                     |             |
| updateTime     | int64     | 更新时间                                                     |             |

索引：taskId