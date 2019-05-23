2019年5月23日11:33:57<br/>
maven工程启动报404<br/>
新建的maven项目在启动的时候一直报404，但是welcome-file-list也配置了，index.jsp也有。<br/>
最后网上查的解决方案如下：<br/>
1.右击项目–>属性(properties)->Deployment Asssembly–>清除其中的/WebContent和
测试文件夹(/src/test/resources和/src/test/java，如果有的话，有可能会没有)<br/>
2.在第一步的基础上，新建文件夹，即点击Add–>Folder–>src–>main-webapp,选中点击finish,最后保存，重新运行项目.

最后问题解决。<br/><br/>
classnotfoundexception contextloaderlistener
有可能是因为没有导入jar包，不过这个不太可能，另一种情况：
右键点击项目--选择Properties
选择Deployment Assembly,在右边点击Add按钮，在弹出的窗口中选择Java Build Path Entries，点击Next，选择Maven Dependencies，点击finish

