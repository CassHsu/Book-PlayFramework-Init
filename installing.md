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





