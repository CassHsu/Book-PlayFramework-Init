# 整合開發環境IDE

## IntelliJ IDEA!

下載選擇Community版：[https://www.jetbrains.com/idea/download/](https://www.jetbrains.com/idea/download/)

1. 解壓縮安裝
2. 安裝SBT  
   Preferences &gt; Plugins &gt; 搜尋SBT &gt; Install  
   ![](/assets/IDE_Install_SBT.png)

3. 安裝Scala  
   Preferences &gt; Plugins &gt; 搜尋Scala &gt; Install  
   ![](/assets/IDE_Install_Scala.png)

4. . 啟動畫面選Import Project  
   ![](/assets/IDE_ImportProjFromSBT.png)

5. 選Demo專案的目錄  
   ![](/assets/IDE_ChooseDemo.png)

6. 使用SBT匯入  
   ![](/assets/IDE_ImportProjFromSBT.png)

7. 匯入設定，初次匯入需指定JDK位置  
   ![](/assets/IDE_ImportProj_Setting.png)

8. 匯入專案  
   ![](/assets/IDE_ShowDemoProj.png)

9. 設定執行指令  
   專案Build成功後，要執行Run時會出現設定Run/Debug Configurations視窗  
   用+新增SBT Task，Name自行指定，Tasks欄位填入~run  
   ![](/assets/IDE_RunConfigurations.png)

10. 執行專案  
    選擇Run或任意綠色箭頭，於port 9000執行成功  
    ![](/assets/IDE_run_OK.png)

11. 




