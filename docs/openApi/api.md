---

title: API 文档
permalink: /api

---


# OpenAPI接口文档

https://aliiot.on-bright.com	为测试域名
https://alicloud.on-bright.com	为生产域名


## 添加obox

Request Method:POST
urlPath: /consumer/open/add_obox
content-type: application/json
HttpBody:

| 参数      | 参数类型   |   说明     |
| --------   | -----:  | :----:  |
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
