

# 影评数据库参数说明文档

### film_review_database:

```sql
create database film_review_database character set utf8;
```



### 用户表（user）

| 字段名            | 说明       | 备注                           |
| ----------------- | ---------- | ------------------------------ |
| user_id           | 用户ID     | int primary key auto_increment |
| user_name         | 用户名     | varchar(20) not null           |
| user_password     | 用户密码   | varchar(20) not null           |
| user_phone_number | 用户手机号 | varchar(11)                    |
| user_email        | 用户邮箱   | varchar(32)                    |
| user_head_picture | 用户头像   | blob                           |
|                   |            |                                |
|                   |            |                                |
|                   |            |                                |

#### 建表语句

```sql
create table user(user_id int primary key auto_increment,user_name varchar(20) not null,user_password varchar(20) not null,user_phone_number varchar(11),user_email varchar(32),user_head_picture blob);
```



### 电影表(film)

| 字段名                | 说明     | 备注                           |
| --------------------- | -------- | ------------------------------ |
| film_id               | 电影ID号 | int primary key auto_increment |
| film_name             | 电影名称 | varchar(20) not null           |
| film_poster           | 电影海报 | mediumblob                     |
| film_language         | 电影语言 | varchar(10)                    |
| film_show_time        | 上映时间 | date                           |
| film_tag              | 电影标签 | varchar(20)                    |
| film_actor            | 演员     | varchar(32)                    |
| film_class            | 电影类型 | varchar(20)                    |
| film_country          | 制片国家 | varchar(20)                    |
| film_sum_time         | 时长     | time                           |
| film_gut_introduction | 剧情简介 | text                           |
|                       |          |                                |
|                       |          |                                |
|                       |          |                                |

#### 建表语句

```sql
create table film(film_id int primary key auto_increment,film_name varchar(20) not null,film_poster mediumblob,film_language varchar(10),film_show_time date,film_tag varchar(20),film_actor varchar(32),film_class varchar(20),film_country varchar(20),film_sum_time time,film_gut_introduction text);
```



### 评价(comment)

| 字段名          | 说明             | 备注                           |
| --------------- | ---------------- | ------------------------------ |
| comment_id      | 用户-电影-多对多 | int primary key auto_increment |
| comment_grade   | 评分             | char(1)                        |
| comment_article | 影评文章         | text                           |
| c_user_id       | 外键关联user     |                                |
| c_film_id       | 外键关联film     |                                |

#### 建表语句

```sql
create table comment(comment_id int primary key auto_increment,comment_grade char(1),comment_article text,c_user_id int,c_film_id int,constraint foreign key(c_user_id) references user(user_id),constraint foreign key(c_film_id) references film(film_id));
```



### 新闻(news)

| 字段名       | 说明       | 备注                           |
| ------------ | ---------- | ------------------------------ |
| news_id      | 新闻ID     | int primary key auto_increment |
| news_title   | 新闻标题   | varchar(32) not null           |
| news_content | 新闻内容   | text                           |
| news_picture | 新闻图片   | blob                           |
| news_dot_bit | 新闻点击率 | smallint                       |

#### 建表语句

```sql
create table news(news_id int primary key auto_increment,news_title varchar(32) not null,news_content text,news_picture blob,news_dot_bit smallint);
```



### 宣传片(trailer)

| 字段名          | 说明               | 备注                           |
| --------------- | ------------------ | ------------------------------ |
| trailer_id      | 电影-宣传片-一对多 | int primary key auto_increment |
| trailer_title   | 宣传片标题         | varchar(32) not null           |
| trailer_picture | 宣传片图片         | mediumblob                     |
| trailer_video   | 宣传片视频         | longblob                       |
| t_film_id       | 外键关联电影       | int                            |

#### 建表语句
```sql
create table trailer(trailer_id int primary key auto_increment,trailer_title varchar(32) not null, trailer_picture mediumblob,trailer_video longblob,t_film_id int,constraint foreign key(t_film_id) references film(film_id));
```



### 广告(ad)

| 字段名        | 说明     | 备注                           |
| ------------- | -------- | ------------------------------ |
| ad_id         | 广告ID   | int primary key auto_increment |
| ad_businesser | 广告商   | varchar(32) not null           |
| ad_picture    | 广告图片 | mediumblob                     |
|               |          |                                |

#### 建表语句

```sql
create table ad(ad_id int primary key auto_increment,ad_businesser varchar(32) not null,ad_picture mediumblob);
```

