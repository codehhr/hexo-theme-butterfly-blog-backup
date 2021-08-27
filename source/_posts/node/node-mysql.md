---
title: node 连接 MySQL
date: 2021-07-16 11:46:10
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/node/mysql.jpg
tags:
categories:
comments:
---

{% btn 'https://github.com/codehhr/Message-board/',留言版案例,far fa-hand-point-right,green larger %}
# 安装 mysql 驱动

可以用淘宝镜像的 `cnpm` 安装

```bash
npm install mysql --save
```

# 引入 mysql 模块

```js
let mysql = require("mysql");
```

# 链接 MySQL

相应的修改`主机名` , `用户名` , `密码` 和 `数据库名`

```js
let mysql = require("mysql");
let connection = mysql.createConnection({
  host: "localhost",
  user: "root",
  password: "12345678",
  database: "test",
});
connection.connect();
connection.query(
  "SELECT * from comment_list",
  function (error, results, fields) {
    if (error) throw error;
    console.log(results);
  }
);
```

## 把这几个步骤封装成函数

```js
/*
    sql: 要执行的 sql 语句
    fun: 拿到数据库返回的 results 后执行的函数
*/
function interactingWithDatabase(sql, fun) {
  let connection = mysql.createConnection({
    host: "localhost",
    user: "root",
    password: "12345678",
    database: "comment_list",
  });
  connection.connect();
  connection.query(sql, function (err, results) {
    if (err) {
      throw err;
    } else {
      fun(results);
    }
  });
  connection.end();
}
```

# 数据库操作 ( CURD )

## sql 语句

```sql
增 : insert into 表名 ( 字段 , 字段 ) values ( 值 , 值 )
删 : delete from 表名 where 条件
改 : update 表名 set 字段 = 值 where 条件
查 : select 字段 from 表名 (where 条件)
```

## 示例

```sql
增 : INSERT INTO comment_list (name , comment) VALUES ('name' ,'comment')
删 : DELETE FROM comment_list WHERE id = 'userid'
改 : UPDATE comment_list SET comment = "newcomment" WHERE id = "userid"
查 : SELECT * FROM comment_list WHERE comment LIKE '%value%' or name LIKE '%value%'
```

# The_End
