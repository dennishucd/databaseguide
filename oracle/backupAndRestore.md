# 备份与还原
## exp备份
**说明：** exp和imp可以在客户端进行，客户端在Oracle官网下载"Oracle Database Client"，如[OracleClient12c](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/database12c-win64-download-2297732.html)<br>
示例：<br>
exp username/pwd@172.2.1.6/serviceName file=d:\net.dmp full=y<br>
**注：** 针对命令的提示，全部直接回车处理。<br>
## imp还原
示例：<br>
imp "'usernamepwd@172.2.1.6/serviceName as sysdba'" file="C:\Users\dennis\Downloads\sentiment.dmp" full=y<br>
