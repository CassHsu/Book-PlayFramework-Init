# 資料庫

---

### 1. 新增**JDBC模組**

打開build.sbt，確認**libraryDependencies**內是否包含**javaJdbc**

若無則可加入 libraryDependencies += javaJdbc

預設可能如下

```
libraryDependencies += guice
```

可以Seq改寫，兩套間以逗號分隔

```
libraryDependencies ++= Seq(
  guice,
  javaJdbc
)
```

存檔便會提示自動安裝

### **2. 設定JDBC connection pools**

打開**conf/application.con**，新增使用MySQL的db區塊設定欲使用的資料庫位址與帳號密碼

```
db.default.driver=com.mysql.jdbc.Driver
db.default.url="jdbc:mysql://localhost/playdemo"
db.default.username=playDemoAdmin
db.default.password="123456789"
```

建立上述資料庫與帳號資料可參考下列SQL命令：

使用root進入mysql中 ，輸入密碼

```
mysql -u root -p

MariaDB [(none)]> create user 'playDemoAdmin' identified by '123456789';
MariaDB [(none)]> CREATE DATABASE playdemo;
MariaDB [(none)]> GRANT ALL PRIVILEGES ON playdemo.* TO 'playDemoAdmin';
MariaDB [(none)]> FLUSH PRIVILEGES;
```



