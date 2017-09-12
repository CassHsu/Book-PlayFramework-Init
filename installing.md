# 環境準備與安裝

### Java 8

請先確認電腦所使用之Java版本為Java 8

```bash
$ java -version

java version "1.8.0_112"
Java(TM) SE Runtime Environment (build 1.8.0_112-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.112-b16, mixed mode)
```

### SBT

下載網址 http://www.scala-sbt.org/download.html

Mac使用Homebrew安裝

```
$ brew install sbt@1
==> Downloading https://cocl.us/sbt-1.0.1.tgz
==> Downloading from https://62a44.https.cdn.softlayer.net/sbt/1.0.1/sbt-1.0.1.tgz
######################################################################## 100.0%
==> Caveats
You can use $SBT_OPTS to pass additional JVM options to SBT:
   SBT_OPTS="-XX:+CMSClassUnloadingEnabled -XX:MaxPermSize=256M"

This formula uses the standard Lightbend sbt launcher script.
Project specific options should be placed in .sbtopts in the root of your project.
Global settings should be placed in /usr/local/etc/sbtopts
==> Summary
🍺  /usr/local/Cellar/sbt/1.0.1: 482 files, 61.0MB, built in 23 seconds
```

### 建立專案

在欲安裝Play專案的目錄下執行sbt new指令建立新專案，若初次使用會下載套件，會花比較多時間。

執行會出現選單，若不修改調整直接enter使用預設值。

```
$ sbt new playframework/play-java-seed.g8
[info] Set current project to play (in build file:/Users/cass/Documents/Repositories/java/play/)

This template generates a Play Java project 

name [play-java-seed]: demo
organization [com.example]:       
scala_version [2.12.2]: 
play_version [2.6.3]: 

Template applied in ./demo
```

在該目錄下建立指定為demo的專案資料夾

```
$ ls
demo	target
```

### 執行專案

初次執行將會下載相依套件，需要耐心等候。

進入demo目錄執行sbt run

```
$ cd demo/

$ sbt run

[warn] Executing in batch mode.
[warn]   For better performance, hit [ENTER] to switch to interactive mode, or
[warn]   consider launching sbt without any commands, or explicitly passing 'shell'
[info] Loading project definition from /Users/cass/Documents/Repositories/java/play/demo/project
[info] Set current project to demo (in build file:/Users/cass/Documents/Repositories/java/play/demo/)

--- (Running the application, auto-reloading is enabled) ---

[info] p.c.s.AkkaHttpServer - Listening for HTTP on /0:0:0:0:0:0:0:0:9000

(Server started, use Enter to stop and go back to the console...)
```

在瀏覽器檢視 http://localhost:9000/ 

執行成功

![](/assets/WelcomeToPlay.png)

