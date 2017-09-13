# JSON

---

在app/controllers內新增一個ApiController，新增echoJson的Action

```java
package controllers;

import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.node.ObjectNode;
import play.libs.Json;
import play.mvc.Controller;
import play.mvc.BodyParser;
import play.mvc.Result;

public class ApiController extends Controller {
    @BodyParser.Of(BodyParser.Json.class)
    public Result echoJson() {
        JsonNode json = request().body().asJson();
        JsonNode echo = json.get("echo");

        ObjectNode result = Json.newObject();

        if(echo == null) {
            result.put("ResCode", "ERR001");
            result.put("ResMessage", "Missing parameter [echo]");

        } else {
            result.put("ResCode", "0000");
            result.put("ResMessage", "OK");
            result.put("echo", echo.asText());
        }

        return ok(result);
    }
}
```

* 其中@BodyParser.Of\(BodyParser.Json.class\)為指定使用Json處理，不加也可以運作。
* 使用request\(\)可取得查詢內容。

在routes內新增採用POST方法之路由

```
# api json
POST    /api/json/echo              controllers.ApiController.echoJson()
```

使用Postman檢視，正確的上下行

![](/assets/JSON_Result.png)

