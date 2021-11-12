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
