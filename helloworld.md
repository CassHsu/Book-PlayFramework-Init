# Hello World

---

### 新增Controller

在app/Controllers內新增HelloController.java

```java
package controllers;

import play.mvc.Controller;
import play.mvc.Result;

public class HelloController extends Controller {
    public Result hello() {
        return ok("Hello World");
    }
}
```

### 設定路由

在conf/routes內新增GET方法

```
# Hello World
GET     /hello                      controllers.HelloController.hello()
```

### 顯示Hello World

Rebuild & Run 後在瀏覽器開啟http://localhost:9000/hello

![](/assets/Hello_World.png)



