# 打包與部署

---

## **dist**

執行dist指令，將自動產生壓縮檔便於移動，於目的地解壓縮後執行bin內與專案同名的Script後即可啟動。



在終端機中進入該專案目錄，執行sbt \(or 在IDE開發環境的Terminal視窗\)

```
$ sbt
[info] Loading global plugins from /Users/cass/.sbt/0.13/plugins
[info] Loading project definition from /Users/cass/Documents/Repositories/java/play/demo/project
[info] Set current project to demo (in build file:/Users/cass/Documents/Repositories/java/play/demo/)
[demo] $ 
```

在sbt環境中執行dist

```
[demo] $ dist
[info] Packaging /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT-sources.jar ...
[info] Done packaging.
[info] Wrote /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT.pom
[info] Main Scala API documentation to /Users/cass/Documents/Repositories/java/play/demo/target/scala-2.12/api...
[info] Packaging /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT-web-assets.jar ...
[info] Done packaging.
[info] Packaging /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT.jar ...
[info] Done packaging.
model contains 24 documentable templates
[info] Main Scala API documentation successful.
[info] Packaging /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT-javadoc.jar ...
[info] Done packaging.
[info] Packaging /Users/Play/Documents/Repositories/java/play/demo/target/scala-2.12/demo_2.12-1.0-SNAPSHOT-sans-externalized.jar ...
[info] Done packaging.
[info] 
[info] Your package is ready in /Users/Play/Documents/Repositories/java/play/demo/target/universal/demo-1.0-SNAPSHOT.zip
[info] 
[success] Total time: 13 s, completed 2017/9/15 下午 01:38:39
```

打包好之檔案位於target/universal/下![](/assets/Deply_dist.png)將該壓縮檔移至欲部署之目錄下解壓縮，此例為/deploy，目標執行檔名為demo

進入解壓縮後目錄中的bin：/deploy/demo-1.0-SNAPSHOT/bin

因為使用zip解壓縮沒有帶執行權限，故需修改權限加入可執行權限

```
$ chmod +x demo
```

執行成功

```
$./demo -Dplay.crypto.secret=hellokey
[info] application - Creating Pool for datasource 'default'
[info] p.a.d.DefaultDBApi - Database [default] connected at jdbc:mysql://localhost/playdemo
[warn] application - system properties: play.crypto.secret is deprecated, use play.http.secret.key instead
[warn] o.h.v.m.ParameterMessageInterpolator - HV000184: ParameterMessageInterpolator has been chosen, EL interpolation will not be supported
[info] play.api.Play - Application started (Prod)
[info] p.c.s.AkkaHttpServer - Listening for HTTP on /0:0:0:0:0:0:0:0:9000
```

若需執行evo則需加入-DapplyEvolutions.default=true

```
$./demo -Dplay.crypto.secret=hellokey -DapplyEvolutions.default=true
```



