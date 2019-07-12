---

title: API 文档
permalink: /api

---



# OpenAPI接口文档

https://aliiot.on-bright.com	为测试域名
https://alicloud.on-bright.com	为生产域名

## Mq说明

| Mq topic说明| | |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| access_token        |   String   |      |
| uniqueKey        |   String   |  第三方唯一用户标识     |

##### MqTopic
```html
	Mq topic : "ob-smart."+access_token+"."+uniqueKey
```

## 公共参数说明
```html
	除了登录接口，其他接口均含有access_token和uniqueKey两个参数，这两个参数拼接在url后面，类似：/consumer/open/registAliDev?access_token=fsdffadaffaf&uniqueKey=qwervd
```

## 登录

| 请求，method=POST|url=/oauth/token |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| 响应数据        |   响应数据类型   |   说明   |
| access_token        |   String   |      |
| token_type        |   String   |       |
| expires_in        |   int   |      |
| scope        |   String   |     域  |

##### 返回信息结构体
```html
{
    "access_token": "1b3494a4-a18a-4b24-8e57-a12d52c1afed",
    "token_type": "bearer",
    "expires_in": 516642,
    "scope": "company"
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/oauth/token?grant_type=client_credentials' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
```

## 注册ali设备

| 请求，method=POST|url=/consumer/open/registAliDev |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| type        |   String   |    （必选）   |
| zone        |   String   |    （必选）   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |
| data数据名称        |   data数据类型   |   说明   |
| kitCenter        |   String   |    地域   |
| deviceName        |   String   |    设备名称   |
| productKey        |   String   |    productKey   |
| deviceSecret        |   String   |    设备Secret     |

##### 返回信息结构体
```html
{
	"message": "select success",
	"status": 200,
	"data": {
		"kitCenter": "cn-shanghai",
		"deviceName": "ocPn9W7ajRqTM167slbS",
		"productKey": "b1eakXpQ1WU",
		"deviceSecret": "DElmvK5NoQswe1pYtMXfzyciYuktcraU"
	}
}
```
##### 请求示例body结构体
```html
{
	"type": "OBOX",
	"zone": "Asia/Shanghai"
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/registAliDev?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=rewrewrewqr' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -d '{
	"type": "OBOX",
	"zone": "Asia/Shanghai"
}'
```

## 删除设备

| 请求，method=DELETE |url=/consumer/open/device |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| serialId        |   String   |   设备序列号（必选）   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data（无） |

##### 返回信息结构体
```html
{
	"message": "delete success",
	"status": 204
}
```
##### 请求示例body结构体
```html
{
	"serialId": "c033000000"
}
```
##### 请求链路
```html
curl -X DELETE \
  'https://aliiot.on-bright.com/consumer/open/device?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=fdsfads' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -d '{
	"serialId": "c033000000"
}'
```
## 添加obox

| 请求，method=POST|url=/consumer/open/obox |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| deviceConfig        |   list   |   设备清单（非必选）   |
| groupConfig        |   list   |   组清单（非必选）   |
| sceneConfig        |   list   |   场景清单（非必选）   |
| oboxSerialId        |   String   |   obox序列号（必选）   |
| oboxName        |   String   |   obox名称（必选）   |
| oboxVersion        |   String   |   obox版本（必选）   |
| oboxStatus        |   String   |   obox状态（非必选）   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |

##### 返回信息结构体
```html
{
	"message": "add success",
	"status": 201,
	"data": {
		"obox_serial_id": "c033000000"
	}
}
```
##### 请求示例body结构体
```html
{
	"deviceConfig": [],
	"groupConfig": [],
	"oboxName": "OBOX33c0",
	"oboxSerialId": "c033000000",
	"oboxStatus": "1",
	"oboxVersion": "0a0219080a253002",
	"sceneConfig": []
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/obox?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=ewqf' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -d '{
	"deviceConfig": [],
	"groupConfig": [],
	"oboxName": "OBOX33c0",
	"oboxSerialId": "c033000000",
	"oboxStatus": "1",
	"oboxversion": "0a0219080a253002",
	"sceneConfig": []
}'
```
## 查询obox

| 请求，method=GET|url=/consumer/open/obox |param: |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |

##### 返回信息结构体
```html
{
	"message": "select success",
	"status": 200,
	"data": {
		"oboxs": [{
			"oboxName": "MBOX3391",
			"oboxSerialId": "9133000000",
			"oboxVersion": "0a02154400052002",
			"oboxStatus": 0
		}, {
			"oboxName": "OBOX9468",
			"oboxSerialId": "6894000000",
			"oboxVersion": "0a0218360a852002",
			"oboxStatus": 0
		}]
	}
}
```
## 删除obox

| 请求，method=DELETE|url=/consumer/open/obox |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| oboxSerialId        |   String   |   obox序列号（必选）   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |

##### 返回信息结构体
```html
{
	"message": "delete success",
	"status": 204
}
```
##### 请求示例body结构体
```html
{
	"oboxSerialId": "c033000000"
}
```
##### 请求链路
```html
curl -X DELETE \
  'https://aliiot.on-bright.com/consumer/open/obox?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=fdsaf' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -d '{
	"oboxSerialId": "c033000000"
}'
```

## 扫描设备

| 请求，method=POST|url=/consumer/open/device |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| oboxSerialId        |   String   |   obox序列号（必选）   |
| deviceType        |   String   |   设备父类型（非必选）   |
| deviceChildType        |   String   |   设备子类型（非必选）   |
| serialId        |   String   |   设备序列号（非必选）   |
| timeout        |   String   |   超时时间（非必选）   |

##### 返回信息结构体
```html
{
	"message": "add success",
	"status": 201,
}
```
##### 请求示例body结构体
```html
{
	"oboxSerialId": "c033000000"
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/device?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=dfasdf' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -d '{
	"oboxSerialId": "c033000000"
}'
```
## 添加门锁临时用户

| 请求，method=POST|url=/consumer/open/intelligentRemoteUser |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| serialId        |   String   |   门锁序列号（必选）   |
| nickName        |   String   |   昵称（必选）   |
| startTime        |   String   |   开始时间（必选）   |
| endTime        |   String   |   结束时间（必选）   |
| times        |   int   |   次数（必选）   |
| mobile        |   String   |   电话号码（非必选）   |
| isMax        |   String   |   isMax最小值为0,为有限次数;isMax最大值为1,为无限次数   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |

##### 返回信息结构体
```html
{
	"message": "add success",
	"status": 201,
	"data": {
		"remoteUser":{
			"serialId":"dfsfdsfsdfs",
			"nickName":"fsde",
			"pin":11,
			"start":"2019-01-11 11:12:23",
			"end":"2019-11-11 11:12:23",
			"isEnd":0,
			"times":1,
			"useTimes":0,
			"mobile":"15879618946",
			"pwd":"621112345",
			"isMax":0,
			"timeLeft":"10"
		}
	}
}
```
##### 请求示例body结构体
```html
{
	"nickName": "呃呃",
	"startTime": "1550573820000",
	"endTime": "1550841360000",
	"times": 1,
	"mobile": "15879618946",
	"isMax":0
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/intelligentRemoteUser?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=fdsfasfa' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -H 'cookie: JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A' \
  -b JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A \
  -d '{
	"nickName": "呃呃",
	"startTime": "1550573820000",
	"endTime": "1550841360000",
	"times": 1,
	"mobile": "15879618946",
	"isMax":0
}'
```
## 更新门锁临时用户

| 请求，method=PUT|url=/consumer/open/intelligentRemoteUser |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| serialId        |   String   |   门锁序列号（必选）   |
| nickName        |   String   |   昵称（必选）   |
| startTime        |   String   |   开始时间（必选）   |
| endTime        |   String   |   结束时间（必选）   |
| times        |   int   |   次数（必选）   |
| mobile        |   String   |   电话号码（非必选）   |
| pin        |   int   |   pin码（必选）   |
| isMax        |   String   |   isMax最小值为0,为有限次数;isMax最大值为1,为无限次数   |
| 响应数据        |   响应数据类型   |   说明   |
| message        |   String   |   消息   |
| status        |   int   |   消息类型   |
| data        |   json   |    data |


##### 返回信息结构体
```html
{
	"message": "update success",
	"status": 205,
	"data": {
		"pwd":"621012345",
		"remoteUser":{
			"serialId":"dfsfdsfsdfs",
			"nickName":"fsde",
			"pin":11,
			"start":"2019-01-11 11:12:23",
			"end":"2019-11-11 11:12:23",
			"isEnd":0,
			"times":1,
			"useTimes":0,
			"mobile":"15879618946",
			"pwd":"621112345",
			"isMax":0,
			"timeLeft":"10"
		}
	}
}
```
##### 请求示例body结构体
```html
{
	"nickName": "呃呃",
	"startTime": "1550573820000",
	"endTime": "1550841360000",
	"times": 1,
	"mobile": "15879618946",
	"isMax":0，
	"pin":10
}
```
##### 请求链路
```html
curl -X PUT \
  'https://aliiot.on-bright.com/consumer/open/intelligentRemoteUser?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed&uniqueKey=fasfdfas' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -d '{
	"nickName": "呃呃",
	"startTime": "1550573820000",
	"endTime": "1550841360000",
	"times": 1,
	"mobile": "15879618946",
	"isMax":0,
	"pin":10
}'
```

##还未完成接口 

##query_intelligent_fingerHome、query_intelligent_openRecord、query_intelligent_warningRecord、query_intelligent_useringRecord、edit_intelligent_user、send_intelligent_validateCode、add_intelligent_authPwd、query_intelligent_authPwd、query_intelligent_remote_unLocking、reset_intelligent_pwd、query_intelligent_push_list、modify_intelligent_push、send_remote_pwd、reset_intelligent_pwd_by_code

