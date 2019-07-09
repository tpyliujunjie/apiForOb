---

title: API 文档
permalink: /api

---



# OpenAPI接口文档

https://aliiot.on-bright.com	为测试域名
https://alicloud.on-bright.com	为生产域名

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

## 添加obox

| 请求，method=POST|url=/consumer/open/obox |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| access_token        |   String   |   token（公司专属）   |
| device_config        |   list   |   设备清单（非必选）   |
| group_config        |   list   |   组清单（非必选）   |
| scene_config        |   list   |   场景清单（非必选）   |
| uniqueKey        |   String   |   第三方唯一用户标识（必选）   |
| obox_serial_id        |   String   |   obox序列号（必选）   |
| obox_name        |   String   |   obox名称（必选）   |
| obox_version        |   String   |   obox版本（必选）   |
| obox_pwd        |   String   |   obox密码（必选）   |
| obox_status        |   String   |   obox状态（必选）   |
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
	"uniqueKey":"fasdfsdfasd",
	"device_config": [],
	"group_config": [],
	"obox_name": "OBOX33c0",
	"obox_pwd": "88888888",
	"obox_serial_id": "c033000000",
	"obox_status": "1",
	"obox_version": "0a0219080a253002",
	"scene_config": []
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/add_obox?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'Postman-Token: 20dbc811-e4f7-4fb9-a526-4df7a9c2ada9,d3231c41-690b-4f80-ba1a-23528be20283' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -H 'cookie: JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A' \
  -b JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A \
  -d '{
	"device_config": [],
	"group_config": [],
	"obox_activate": "0",
	"obox_name": "OBOX33c0",
	"obox_pwd": "88888888",
	"obox_serial_id": "c033000000",
	"obox_status": "1",
	"obox_version": "0a0219080a253002",
	"scene_config": [],
	"uniqueKey":"fadsfdsfdsafdas"
}'
```

## 扫描设备

| 请求，method=POST|url=/consumer/open/search_new_device |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| access_token        |   String   |   token（公司专属）   |
| uniqueKey        |   String   |   第三方唯一用户标识（必选）   |
| oboxSerialId        |   String   |   obox序列号（必选）   |
| deviceType        |   String   |   设备父类型（非必选）   |
| deviceChildType        |   String   |   设备子类型（非必选）   |
| serialId        |   String   |   设备序列号（非必选）   |
| timeout        |   String   |   超时时间（必选）   |

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
	"uniqueKey":"fasdfsdfasd",
	"oboxSerialId": "c033000000"
}
```
##### 请求链路
```html
curl -X POST \
  'https://aliiot.on-bright.com/consumer/open/search_new_device?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'Postman-Token: 20dbc811-e4f7-4fb9-a526-4df7a9c2ada9,0a5c5ba0-adb5-4737-9603-69b877507593' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -H 'cookie: JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A' \
  -b JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A \
  -d '{
	"uniqueKey":"fasdfsdfasd",
	"oboxSerialId": "c033000000"
}'
```
## 添加门锁临时用户

| 请求，method=POST|url=/consumer/open/intelligentRemoteUser |param:body |
| --------   | -----:  | :----:  |
| 参数      | 参数类型   |   说明     |
| access_token        |   String   |   token（公司专属）   |
| uniqueKey        |   String   |   第三方唯一用户标识（必选）   |
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
	"uniqueKey":"fasdfsdfasd",
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
  'https://aliiot.on-bright.com/consumer/open/intelligentRemoteUser?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -H 'Postman-Token: 20dbc811-e4f7-4fb9-a526-4df7a9c2ada9,15e15c74-1d63-455f-991a-b4baf028bf53' \
  -H 'User-Agent: PostmanRuntime/7.15.0' \
  -H 'accept-encoding: gzip, deflate' \
  -H 'cache-control: no-cache' \
  -H 'content-length: 136' \
  -H 'cookie: JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A' \
  -b JSESSIONID=5BC8BA7B9382E508E79179CDD84F7C1A \
  -d '{
	"uniqueKey":"fasdfsdfasd",
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
| access_token        |   String   |   token（公司专属）   |
| uniqueKey        |   String   |   第三方唯一用户标识（必选）   |
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
	"uniqueKey":"fasdfsdfasd",
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
  'https://aliiot.on-bright.com/consumer/open/intelligentRemoteUser?access_token=1b3494a4-a18a-4b24-8e57-a12d52c1afed' \
  -H 'Accept: */*' \
  -H 'Authorization: Basic VGVuY2VudDpUZW5jZW50' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Content-Type: application/json' \
  -H 'Host: aliiot.on-bright.com' \
  -d '{
	"uniqueKey":"fasdfsdfasd",
	"nickName": "呃呃",
	"startTime": "1550573820000",
	"endTime": "1550841360000",
	"times": 1,
	"mobile": "15879618946",
	"isMax":0,
	"pin":10
}'
```
