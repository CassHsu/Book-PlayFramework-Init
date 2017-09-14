# Ebean ORM

---

### 1. 安裝Ebean的Plugin

在project/plugins.sbt中新增

```
addSbtPlugin("com.typesafe.sbt" % "sbt-play-ebean" % "4.0.2")
```

加入後應會如下圖提示要Refresh，選擇Refresh或auto-import後會自動安裝![](/assets/Ebean_addPlugin.png)

### 2. **啟用PlayEbean**

在**build.sbt**中存下列設定

```
lazy val root = (project in file(".")).enablePlugins(PlayJava)
```

加入PlayEbean，以逗號分隔

```
lazy val root = (project in file(".")).enablePlugins(PlayJava, PlayEbean)
```

### 3. 定義Model與db關聯

在conf/application.conf加入

```
ebean.default = ["models.*"]
```

指定db.default對應到models的Package

### 4. 新增指定**的Package**

到app內新增models

![](/assets/Ebean_pkg_models.png)

### 5. **在models內新增欲對應資料表之物件**

關鍵為Model是否有匯入正確，其Package為 **io.ebean.Mode，**若build.sbt中enablePlugins沒有加上**PlayEbean**將會無法import。

Product.java

```java
package models;

import io.ebean.Finder;
import io.ebean.Model;
import play.data.validation.Constraints;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "PRODUCT")
public class Product extends Model {
    @Id
    public long id;

    @Column
    @Constraints.Required
    public String name;

    @Column
    @Constraints.Required
    public int price;

    public static Finder<Long, Product> find = new Finder<Long,Product>(Product.class);
}
```

### 6. 新增Action

回到ApiController內新增showProducts

```java
public Result showProducts() {
    List<Product> pList = Product.find.all();

    ObjectNode result = Json.newObject();

    result.put("ResCode", "0000");
    result.put("ResMessage", "OK");
    result.set("products",Json.toJson(pList));

    return ok(result);
}
```

並到routes內做相關的路由對應

```
GET     /api/json/showProducts      controllers.ApiController.showProducts()
```

### 7. 初次執行 evolution

在瀏覽器上執行 [http://localhost:9000/api/json/showProducts](http://localhost:9000/api/json/showProducts)![](/assets/Ebean_evolution.png)

從網頁選**Apply this script now!**

執行完Evolution後切換回原請求之回應

```
{
    ResCode: "0000",
    ResMessage: "OK",
    products: [ ]
}
```

### 8. 檢視資料庫

前往資料庫確認，table已新增

```
MariaDB [playdemo]> show tables;
+--------------------+
| Tables_in_playdemo |
+--------------------+
| play_evolutions    |
| product            |
+--------------------+
2 rows in set (0.00 sec)
```

product

```
MariaDB [playdemo]> describe product;
+-------+--------------+------+-----+---------+----------------+
| Field | Type         | Null | Key | Default | Extra          |
+-------+--------------+------+-----+---------+----------------+
| id    | bigint(20)   | NO   | PRI | NULL    | auto_increment |
| name  | varchar(255) | YES  |     | NULL    |                |
| price | int(11)      | NO   |     | NULL    |                |
+-------+--------------+------+-----+---------+----------------+
3 rows in set (0.01 sec)
```



