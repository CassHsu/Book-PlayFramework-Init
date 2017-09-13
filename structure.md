# Play專案結構

---

![](/assets/ST_Overview.png)

## app/

1. 包含所有可執行的source code

2. 以目錄定義M.V.C. 模式

   1. controllers/

   2. models/

   3. views

3. 可新增自己的目錄：如utils/

## **public/**

在當Web Server時可被外部直接取得之資料，/public在url上會被對應到/assets。

ex：http://localhost:9000/assets/images/favicon.png可直接取得play的icon。  
![](/assets/ST_public.png)

# **conf/**

存放兩個主要的設定檔

* application.conf：包含參數的主設定檔。
* routes：定義路由。

# **lib/**

存放不由Framework管理的Library檔，如程式會用到的JAR檔。

## **build.sbt**

此應用程式之Build宣告

```
name := """demo"""
organization := "com.example"

version := "1.0-SNAPSHOT"

lazy val root = (project in file(".")).enablePlugins(PlayJava)

scalaVersion := "2.12.2"

libraryDependencies += guice

```

## **project/**

![](/assets/ST_project.png)

1. **build.properties  
   **定義此專案中目前用到的plugins

2. **plugins.sbt  
   **定義Build此App所需各個套件與版本資訊

## **target/**

存放compiled class跟由Framework所generated出的所有相關檔案。



