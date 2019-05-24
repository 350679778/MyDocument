## maven工程启动报404
2019年5月23日11:33:57<br/>
新建的maven项目在启动的时候一直报404，但是welcome-file-list也配置了，index.jsp也有。<br/>
最后网上查的解决方案如下：<br/>
1.右击项目–>属性(properties)->Deployment Asssembly–>清除其中的/WebContent和
测试文件夹(/src/test/resources和/src/test/java，如果有的话，有可能会没有)<br/>
2.在第一步的基础上，新建文件夹，即点击Add–>Folder–>src–>main-webapp,选中点击finish,最后保存，重新运行项目.<br/>
最后问题解决。

## 启动tomcat报classnotfoundexception contextloaderlistener 异常
2019年5月24日10:29:07<br/>
有可能是因为没有导入jar包，不过这个不太可能，另一种情况：
右键点击项目--选择Properties
选择Deployment Assembly,在右边点击Add按钮，在弹出的窗口中选择Java Build Path Entries，点击Next，选择Maven Dependencies，点击finish。<br/><br/>

## idea maven jar包下载失败问题
2019年5月24日10:31:45<br/>
有可能是lastupdated文件导致jar包下载失败，执行以下脚本
```go
@echo off
rem create by NettQun
  
rem 这里写你的仓库路径
set REPOSITORY_PATH=C:\Users\Admin\.m2\repository
rem 正在搜索...
for /f "delims=" %%i in ('dir /b /s "%REPOSITORY_PATH%\*lastUpdated*"') do (
    echo %%i
    del /s /q "%%i"
)
rem 搜索完毕
pause
```
新建 .bat文件即可(windows)

```go
# create by NettQun
# 这里写你的仓库路径
REPOSITORY_PATH=~/Documents/tools/repository
echo 正在搜索...
find $REPOSITORY_PATH -name "*lastUpdated*" | xargs rm -fr
```
新建 .sh文件(linux)
