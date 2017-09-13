# **Actions,Controllers and Results**

---

## **Actions**

Play應用程式接收的request大多會由Action來處理。Action會接收參數在處理過之後回傳Result給Client，如Hello World範例中的hello\(\)，便是一個Action。

```java
public Result hello() {
    return ok("Hello World");
}
```

上例中，ok是一個Result類別，會回傳200 OK。

## **Controllers**

繼承play.mvc.controller者，其內可包含許多個Actions。範例如下：

```java
public class HelloController extends Controller {
    public Result hello() {
        return ok("Hello World");
    }

    public Result hello1() {
        return ok("Hello World 1");
    }
}
```

### **傳參數至Controller**

處理action的方法也可以接收輸入參數：

```java
public Result hello1(String name) {
    return ok("Hello " + name);
}
```

在conf/routes內設定：

```
# Hello name
GET     /hello1/:name               controllers.HelloController.hello1(name)
```

Run後結果如下圖：

![](/assets/Act_HelloCass.png)

## **Results**

### 更改Content-Type

預設的Content-Type是text/plain，可用as修改：

```java
Result htmlResult = ok("<h1>Hello World!</h1>").as("text/html");
```

### **設定response header**

```java
public Result helloHtml() {
    response().setHeader(CONTENT_TYPE,"text/html");
    Result pageNotFound = notFound("<h1>Page not found</h1>").as("text/html");
    return pageNotFound;
}
```

conf/routes 路由設定：

```
# Hello Html
GET     /helloHtml                  controllers.HelloController.helloHtml()
```

重run後，連線到

[http://localhost:9000/helloHtml](http://localhost:9000/helloHtml)

驗證結果：

![](/assets/Act_Html.png)

### **其他Result**

```java
Result notFound = notFound();
Result pageNotFound = notFound("<h1>Page not found</h1>").as("text/html");
Result badRequest = badRequest(views.html.form.render(formWithErrors));
Result oops = internalServerError("Oops");
Result anyStatus = status(488, "Strange response type");
```

### **Redirects**

Redirect也是Result。

在Controller中新增action，導向/hello：

```java
public Result hello2() {
    return redirect("/hello");
}
```

在routes中新增路由

```
# Hello Redirect
GET     /hello2                     controllers.HelloController.hello2()
```

瀏覽器中執行[http://localhost:9000/hello2](http://localhost:9000/hello2) 便會重新導向到[http://localhost:9000/hello](http://localhost:9000/hello)





