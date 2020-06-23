# The Ultimate MySQL Bootcamp: Go from SQL Beginner to Expert

## 6/22 久々に再開
なぜか DB が消えていたので create db cat_app; を作り直して table 再作成
  - [Online Courses - Anytime, Anywhere \| Udemy](https://www.udemy.com/course/the-ultimate-mysql-bootcamp-go-from-sql-beginner-to-expert/learn/lecture/6914102#overview)
  
が作り直す
```
> drop table cats;
> create table cats
  (
  cat_id int not null auto_increment,
  name  varchar(100),
  breed varchar(100),
  age   int,
  primary key (cat_id)
  );
> desc cats;
> insert into cats (name, breed, age)
            values ('Ringo', 'Tabby', 4),
                   ('Cindy', 'Maine coon', 10),
                   ('Dumbledore', 'Maine Coon', 11),
                   ('Egg', 'Presian', 4),
                   ('Misty', 'Tabby', 13),
                   ('George Michael', 'Ragdoll', 9),
                   ('Jackson', 'Sphynx', 7);
 
```


カラムを選択する
```
> select cat_id, name, age from cats;

```

カラムに条件をつける
```
> select * from cats where name='egg';

別のカラムの同じ値のみ
> select name, age FROM cats WHERE breed='Tabby'; 

```

カラム名を変更する
- name -> cat name
- breed kitty breed
```
> select name as 'cat name', breed as 'kitty breed' from cats;
```

cats テーブルの name カラムの値が 'Misty' の カラム age の 値を 14 にする
- update cats -> cats テーブルの
- where name='Misty' -> name カラムの値が 'Misty'
- set age -> カラム age の 値を 14 にする
```
> update cats set age =14 where name ='Misty';
```

更新 update
- name カラムが Ringo の カラム breed の値を -> British Shorthair に update

```
mysql root@localhost:cat_app> select * from cats where name='Ringo';
+--------+-------+-------+-----+
| cat_id | name  | breed | age |
+--------+-------+-------+-----+
| 1      | Ringo | Tabby | 4   |
+--------+-------+-------+-----+

1 row in set
Time: 0.017s

mysql root@localhost:cat_app> update cats set breed='British Shorthair' where name='Ringo';
Query OK, 1 row affected
Time: 0.007s

mysql root@localhost:cat_app> select * from cats where name='Ringo';
+--------+-------+-------------------+-----+
| cat_id | name  | breed             | age |
+--------+-------+-------------------+-----+
| 1      | Ringo | British Shorthair | 4   |
+--------+-------+-------------------+-----+


```

複数 カラム update

```
update shirts set color='off white', shirt_size='XS' where color='white';
```

削除
- cat_id と age が一致しているデータのみ削除
```
delete from cats where name='Egg';
select * from cats;
select * from cats where name='egg';
delete from cats where name='egg';
select * from cats;
delete from cats;

delete from cats where cat_id=age;
```

データの作成
- insert into テーブル名(カラム名, カラム名, ..., ...,
  )values('値', '値', ..., ...,);
```
insert into shirts(color, article, shirt_size, last_worn
)values('purple', 'polo shirt', 'medium', 50);
```
