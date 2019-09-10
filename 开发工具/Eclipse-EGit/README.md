## eclipse使用Egit插件拉取项/推送目报错
Message:https://github.com/huangtiancai/web.git: cannot open git-upload-pack
eclipse报错信息为cannot open git-upload-pack
## 解决
1.网络问题：ping github.com  一般不是这个问题
2.在eclipse-window-preferences-team-git-configuration中add entry，设置key为http.sslVerify，值为false，然后apply
3.查看eclipse的错误日志，找到如下异常信息：
```
org.eclipse.jgit.api.errors.TransportException: https://github.com/huangtiancai/web.git: cannot open git-upload-pack
	at org.eclipse.jgit.api.LsRemoteCommand.execute(LsRemoteCommand.java:223)
	at org.eclipse.jgit.api.LsRemoteCommand.call(LsRemoteCommand.java:159)
	at org.eclipse.egit.core.op.ListRemoteOperation.run(ListRemoteOperation.java:99)
	at org.eclipse.egit.ui.internal.clone.SourceBranchPage$8.run(SourceBranchPage.java:339)
	at org.eclipse.jface.operation.ModalContext$ModalContextThread.run(ModalContext.java:119)
Caused by: org.eclipse.jgit.errors.TransportException: https://github.com/huangtiancai/web.git: cannot open git-upload-pack
	at org.eclipse.jgit.transport.TransportHttp.connect(TransportHttp.java:518)
	at org.eclipse.jgit.transport.TransportHttp.openFetch(TransportHttp.java:296)
	at org.eclipse.jgit.api.LsRemoteCommand.execute(LsRemoteCommand.java:202)
	... 4 more
Caused by: javax.net.ssl.SSLException: Received fatal alert: protocol_version
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:154)
	at sun.security.ssl.SSLSocketImpl.recvAlert(SSLSocketImpl.java:1979)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:1086)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1332)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1359)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1343)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:563)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
```
最重要的异常信息其实是：`Caused by: javax.net.ssl.SSLException: Received fatal alert: protocol_version`
就是ssl协议的版本不对，上面提到的博客还贴出了github的通知：
2018年2月8日后禁止通过TLSv1.1协议连接https://github.com 和 https://api.github.com.

总结原因就是：
eclipse是4.4.0版的并不是最新版的，因此我的ecplise的默认JDK为JDK1.7，当然最新版的eclipse默认是1.8的不会有这个问题，因为JDK1.8默认支持TLSv1.2，JDK1.7默认是TLSv1.1，所以需要将eclipse中的TLSv1改为TLSv1.2。怎么改呢？
其实很简单，网上答案千奇百怪但是如果eclipse的默认JDK是1.7的就简单，如果是1.7以下的请另外百度

打开eclipse安装目录下的eclipse.ini添加一句：`-Dhttps.protocols=TLSv1,TLSv1.1,TLSv1.2`  就可以了。

原文链接：https://blog.csdn.net/Royal__Moon/article/details/79427431