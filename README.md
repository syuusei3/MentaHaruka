# simpleVueSpringBoot
Developing simple app using with vue.js and SpringBoot 


## MySQLでuserテーブルを作成

以下の手順に従って、userテーブルを作成してください。

1. テーブル構造を作成:

```sql
CREATE TABLE `user` (
  `id` BIGINT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(100) NOT NULL,
  `address` VARCHAR(255) NULL,
  `phone` VARCHAR(50) NULL,
  `update_date` DATETIME NOT NULL,
  `create_date` DATETIME NOT NULL,
  `delete_date` DATETIME NULL,
  PRIMARY KEY (`id`)
);
```

2. 初期データを挿入:

```sql
INSERT INTO `user` (`id`, `name`, `address`, `phone`, `update_date`, `create_date`)
VALUES ('1', 'Yamada Taro', 'TOkyo', '090-0000-0000', '2021-06-30', '2021-06-30');

INSERT INTO `user` (`id`, `name`, `address`, `phone`, `update_date`, `create_date`)
VALUES ('2', 'test test', 'Kyoto', '080-0000-0000', '2021-06-30', '2021-06-30');

```

3. 文字ばけした場合：
```sql
   ALTER DATABASE database_name
   CHARACTER SET utf8mb4
   COLLATE utf8mb4_general_ci;

```

```sql
   CREATE TABLE user (
     column_name VARCHAR(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci
   ) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
```
