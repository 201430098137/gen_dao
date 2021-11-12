### 自动生成标准dao和orm代码

将md文件复制进aa.md文件即可

md文件格式如下

### 任务表 task

| 字段名        | 类型        | 说明                                                         | 索引        |
| ------------- | ----------- | ------------------------------------------------------------ | ----------- |
| id            | int         | 自增id                                                       | primary_key |
| taskId        | char(100)   | 任务id                                                       | normal      |
| taskName      | varchar(30) | 任务名                                                       |             |
| taskTimeType  | char(30)    | 任务时间类型  long-term:长期  temporary:临时                 |             |
| taskStartTime | int64       | 任务开始时间                                                 |             |
| taskEndTime   | int64       | 任务结束时间                                                 |             |
| taskType      | char(30)    | 任务类型 account:指定账号  keyword:关键词爬取                |             |
| taskStatus    | char(30)    | 任务状态 Finish:已结束 Doing:进行中 Ready:还没开始 Pause 暂停中 |             |
| comment       | text(200)   | 备注                                                         |             |
| platform      | char(30)    | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 |             |
| createTime    | int64       | 创建时间                                                     |             |
| updateTime    | int64       | 更新时间                                                     |             |

索引：taskId



### 任务账号关联表 task_account_relate

| 字段名      | 类型      | 说明                                                         | 索引        |
| ----------- | --------- | ------------------------------------------------------------ | ----------- |
| id          | int       | 自增id                                                       | primary_key |
| subTaskId   | char(100) | 子任务id                                                     | normal      |
| taskId      | char(100) | 任务id                                                       |             |
| platform    | char(30)  | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 |             |
| accountSign | char(50)  | 账号标识昵称或平台id                                         |             |
| userId      | char(100) | 用户id                                                       |             |
| status      | char(30)  | 状态：Doing:进行中 Finish:完成                               |             |
| createTime  | int64     | 创建时间                                                     |             |
| updateTime  | int64     | 更新时间                                                     |             |

索引：taskId

### 任务关键词关联表 task_keyword_relate

| 字段名             | 类型      | 说明                           | 索引        |
| ------------------ | --------- | ------------------------------ | ----------- |
| id                 | int       | 自增id                         | primary_key |
| subTaskId          | char(100) | 子任务id                       | normal      |
| taskId             | char(100) | 任务id                         | normal      |
| keyword            | char(100) | 关键词                         |             |
| status             | char(30)  | 状态：Doing:进行中 Finish:完成 |             |
| videoSuccessNumber | int       | 视频信息获取成功次数           |             |
| createTime         | int64     | 创建时间                       |             |
| updateTime         | int64     | 更新时间                       |             |

索引：taskId





### 任务爬取项关联表 task_crawl_relate

| 字段名         | 类型      | 说明           | 索引        |
| -------------- | --------- | -------------- | ----------- |
| id             | int       | 自增id         | primary_key |
| taskId         | char(100) | 任务id         | normal      |
| crawlId        | char(100) | 爬取项id       |             |
| crawlStartTime | int64     | 自定义开始时间 |             |
| crawlCount     | int       | 爬取数量       |             |
| createTime     | int64     | 创建时间       |             |
| updateTime     | int64     | 更新时间       |             |

索引：taskId

### 爬取项表 crawl

| 字段名      | 类型         | 说明                                                         | 索引        |
| ----------- | ------------ | ------------------------------------------------------------ | ----------- |
| id          | int          | 自增id                                                       | primary_key |
| crawlId     | char(100)    | 爬取项id                                                     | normal      |
| name        | char(50)     | 爬取项名                                                     |             |
| description | varchar(100) | 描述                                                         |             |
| crawlType   | char(30)     | 爬取类型：account:账号 focus关注 follow:粉丝 video:视频  videoComment:视频评论 CommentUser:评论人信息 |             |
| createTime  | int64        | 创建时间                                                     |             |
| updateTime  | int64        | 更新时间                                                     |             |

 索引：crawelId

### 用户信息表 platform_user

| 字段名               | 类型         | 说明                                                         | 索引                          |
| -------------------- | ------------ | ------------------------------------------------------------ | ----------------------------- |
| id                   | int          | 自增id                                                       | primary_key                   |
| shortUserId          | char(50)     | 用户id,tiktok查找用户信息时用到                              | idx_shortUserId               |
| userId               | char(100)    | 用户id                                                       | complex:idx_userId_platform:1 |
| platform             | char(30)     | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 | complex:idx_userId_platform:2 |
| platformId           | char(50)     | 平台号 如：抖音号，快手号,tiktok号                           | normal                        |
| gender               | char(30)     | 性别：Man:男 Woman:女                                        |                               |
| username             | char(50)     | 昵称                                                         |                               |
| birthday             | char(50)     | 生日                                                         |                               |
| address              | varchar(150) | 所在地                                                       |                               |
| school               | char(50)     | 学校                                                         |                               |
| description          | text         | 描述                                                         |                               |
| fan                  | int          | 粉丝数                                                       |                               |
| follow               | int          | 关注数                                                       |                               |
| videoNum             | int          | 视频数                                                       |                               |
| LikeCount            | int          | 用户获赞数                                                   |                               |
| focusSuccessNumber   | int          | 关注信息获取成功次数                                         |                               |
| followSuccessNumber  | int          | 粉丝信息获取成功次数                                         |                               |
| videoSuccessNumber   | int          | 视频信息获取成功次数                                         |                               |
| commentSuccessNumber | int          | 评论信息获取成功次数                                         |                               |
| createTime           | int64        | 创建时间                                                     |                               |
| updateTime           | int64        | 更新时间                                                     |                               |

 索引：userId-platform

platformId-platform

### 账号关联表 account_relate

| 字段名       | 类型      | 说明                                                         | 索引        |
| ------------ | --------- | ------------------------------------------------------------ | ----------- |
| id           | int       | 自增id                                                       | primary_key |
| userId       | char(100) | 用户id                                                       | normal      |
| relateUserId | char(100) | 关联用户id                                                   |             |
| relateType   | char(30)  | 关联关系：focus:关注 fan:粉丝                                |             |
| platform     | char(30)  | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 |             |
| createTime   | int64     | 创建时间                                                     |             |
| updateTime   | int64     | 更新时间                                                     |             |





### 视频表 video

| 字段名               | 类型          | 说明                                                         | 索引        |
| -------------------- | ------------- | ------------------------------------------------------------ | ----------- |
| id                   | int           | 自增id                                                       | primary_key |
| videoId              | char(100)     | 视频id                                                       | normal      |
| userId               | char(100)     | 用户id                                                       | normal      |
| videoTitle           | varchar(250)  | 视频标题                                                     | fulltext    |
| platform             | char(30)      | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 |             |
| description          | varchar(1500) | 简介                                                         |             |
| commentCount         | int           | 评论数                                                       |             |
| likeCount            | int           | 点赞数                                                       |             |
| fileId               | char(100)     | 文件id                                                       |             |
| duration             | int           | 文件时长                                                     |             |
| downloadStatus       | char(30)      | 下载状态：Success:成功 Fail 失败 Doing 正在进行              |             |
| commentSuccessNumber | int           | 评论信息获取成功次数                                         |             |
| publishTime          | int64         | 发布时间                                                     |             |
| createTime           | int64         | 创建时间                                                     |             |
| updateTime           | int64         | 更新时间                                                     |             |

 索引：videoId

userId

full-text (videoTitle)



### 账号喜欢视频关联表 account_video_relate

| 字段名     | 类型      | 说明                                                         | 索引        |
| ---------- | --------- | ------------------------------------------------------------ | ----------- |
| id         | int       | 自增id                                                       | primary_key |
| userId     | char(100) | 用户id                                                       | normal      |
| videoId    | char(100) | 视频id                                                       |             |
| platform   | char(30)  | 平台 douyin:抖音 kuaishou:快手 twitter:推特,tiktok:海外版抖音 |             |
| createTime | int64     | 创建时间                                                     |             |
| updateTime | int64     | 更新时间                                                     |             |



### 评论表 comment

| 字段名       | 类型       | 说明                                                        | 索引        |
| ------------ | ---------- | ----------------------------------------------------------- | ----------- |
| id           | int        | 自增id                                                      | primary_key |
| commentId    | char(100)  | 评论id                                                      |             |
| userId       | char(100)  | 用户id                                                      | normal      |
| videoId      | char(100)  | 视频id                                                      | normal      |
| platform     | char(30)   | 平台 douyin:抖音 kuaishou:快手 tweet:推特,tiktok:海外版抖音 |             |
| content      | text       | 评论内容                                                    |             |
| commentType  | char(30)   | 评论类型：文字:text image:图片 video:视频                   |             |
| extend       | text(1000) | 附带的视频和图片链接用，json[{"type":"video/image","url"}]  |             |
| commentCount | int        | 评论数                                                      |             |
| likeCount    | int        | 点赞数                                                      |             |
| publishTime  | int64      | 评论时间                                                    |             |
| createTime   | int64      | 创建时间                                                    |             |
| updateTime   | int64      | 更新时间                                                    |             |

 索引：commentId

videoId

userId



### 文件表 file

| 字段名     | 类型      | 说明     | 索引        |
| ---------- | --------- | -------- | ----------- |
| id         | int       | 自增id   | primary_key |
| fileId     | char(100) | 文件id   | normal      |
| size       | int       | 文件大小 |             |
| fileType   | char(15)  | 文件格式 |             |
| createTime | int64     | 创建时间 |             |
| updateTime | int64     | 更新时间 |             |

 索引：fileId


### 后台管理账号表 user_admin

| 字段名        | 类型      | 说明     | 索引        |
| ------------- | --------- | -------- | ----------- |
| id            | int       | 自增id   | primary_key |
| adminId       | char(100) | 管理员id | normal      |
| adminName     | char(100) | 用户名   |             |
| adminPassword | char(100) | 用户密码 |             |
| createTime    | int64     | 创建时间 |             |
| updateTime    | int64     | 更新时间 |             |



### mongo表设计

### 爬虫失败原因表 reason

| 字段名     | 类型      | 说明                                              | 索引 |
| ---------- | --------- | ------------------------------------------------- | ---- |
| id         | int       | 自增id                                            |      |
| type       | char(100) | 任务类型：task：任务 download：下载 comment：评论 |      |
| data       | text      | 数据                                              |      |
| reasons    | text      | 失败原因                                          |      |
| retryTimes | int       | 重试次数                                          |      |
| createTime | int64     | 创建时间                                          |      |
| updateTime | int64     | 更新时间                                          |      |

 索引：fileId





### 用户原始数据表 user_origin_data

| 字段名     | 类型      | 说明     | 索引   |
| ---------- | --------- | -------- | ------ |
| _id        | int       | 主键     |        |
| subTaskId  | char(100) | 子任务id | normal |
| data       | text(500) | 数据     |        |
| pcursor    | char(30)  | 游标     |        |
| createTime | int64     | 创建时间 |        |
| updateTime | int64     | 更新时间 |        |



### 视频列表原始数据表 video_origin_data

| 字段名     | 类型      | 说明                                          | 索引   |
| ---------- | --------- | --------------------------------------------- | ------ |
| _id        | int       | 主键                                          |        |
| subTaskId  | char(100) | 子任务id                                      | normal |
| data       | text(500) | 数据                                          |        |
| status     | string    | 状态： Finish:已处理 Doing:正在处理 Fail 失败 |        |
| pcursor    | string    | 游标或页数                                    |        |
| createTime | int64     | 创建时间                                      |        |
| updateTime | int64     | 更新时间                                      |        |



### 评论列表原始数据表 comment_origin_data

| 字段名     | 类型      | 说明                                           | 索引                            |
| ---------- | --------- | ---------------------------------------------- | ------------------------------- |
| _id        | int       | 主键                                           |                                 |
| subTaskId  | char(100) | 子任务id                                       | complex:idx_subTaskId_videoId:1 |
| videoId    | char(100) | 音频id                                         | complex:idx_subTaskId_videoId:2 |
| data       | text(500) | 数据                                           |                                 |
| status     | string    | 状态： Finish:已处理 Doing:正在处理 Fail: 失败 |                                 |
| pcursor    | string    | 游标或页数                                     |                                 |
| createTime | int64     | 创建时间                                       |                                 |
| updateTime | int64     | 更新时间                                       |                                 |



