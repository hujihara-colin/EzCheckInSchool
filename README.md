# EzCheckInSchool
完美校园自动打卡一天三次校内版。

# 使用方法
首先，点击右上角Star并Fork，

接下来抓包完美校园打卡内容，本文使用Fiddler代理手机抓包

fiddler没有手机客户端，都是安装在PC上，要实现对手机上的程序抓包，则需要对PC上的fiddler和手机端做一些配置。步骤如下：

https://www.cnblogs.com/wenbodeboke/p/9770771.html

设置好手机代理后，打开完美校园开始健康打卡（最好在指定的打卡时间打卡方便抓包），目标数据包为POST到`https://reportedh5.17wanxiao.com/sass/api/epmpics`的JSON
格式如下：

```
{
	"businessType": "epmpics",
	"method": "submitUpInfoSchool",
	"jsonData": {
		"deptStr": {
			"deptid": xxxx,
			"text": "x学院-xx-xxxxxx"
		},
		"areaStr": "{\"streetNumber\":\"\",\"street\":\"x街\",\"district\":\"x区\",\"city\":\"x市\",\"province\":\"x省\",\"town\":\"\",\"pois\":\"xxxx\",\"lng\":xxx.,\"lat\":xxx,\"address\":\"x区x街x城\",\"text\":\"x省-x市\",\"code\":\"\"}",
		"reportdate": xxxxxxxxxx,
		"customerid": 43,
		"deptid": xxxx,
		"source": "app",
		"templateid": "clockSign3",
		"stuNo": "学号",
		"username": "姓名",
		"userid": 用户ID,
		"updatainfo": [
			{
				"propertyname": "temperature",
				"value": "36.4"
			},
			{
				"propertyname": "symptom",
				"value": "无症状"
			}
		],
		"customerAppTypeRuleId": 146,
		"clockState": 0
	},
	"token": "TOKEN字段"
}
```
接下来你需要把上面获取到的信息以此设为Secert

在Settings添加以下Secert字段

AREASTR //抓包JSON中的"areaStr"，删去转义符‘\’，填写{ }及中间的部分

DEPTID //抓包JSON中的"deptid"

DEPTTEXT //抓包JSON中的"jsonData"的"text"

STUNO //抓包JSON中的"stuNo"

USERID //抓包JSON中的"userid"

USERNAME //抓包JSON中的"username"

SCKEY //Server酱调用URL

添加后开启Actions方法 

Settings->Action->I understand... 

回到项目主页，修改README.md随便加几个空格触发Actions

# 代码参考及详细教程
https://github.com/ReaJason/17wanxiaoCheckin-Actions

https://github.com/YooKing/HAUT_autoCheck/blob/master/main.py