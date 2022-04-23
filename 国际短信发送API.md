**国际短信发送服务**

**HOST**: http://api.sjroom.cn/doc.html

**联系人**: manson 18973716781

**Version**:V1.0

# 国际短信API
## 1.获取短信通道


**接口描述**: 先找管理员开通，能发送的通道，此时能查询到对应的goodsSupplySmsConfigId。
此goodsSupplySmsConfigId，在发送的时候用到。


**接口地址**:`http://api.sjroom.cn/api/open/int/sms/list`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"account": "",
	"password": ""
}
```


**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  |  
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |  
|password| 密码  | body | true |string  | 


**响应参数**:


| 参数名称         | 参数说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|goodsSupplySmsConfigId| 通道ID  |integer(int64)  | integer(int64)   |
|countryCode|  国码 |string  |    |
|countryOperator|  运营商 |string  |    |
|customerPrice|  客户价格 |number  |    |
|nameEn| 国家中文 |string  |    |
|nameZh| 国家英文 |string  |    |
|status| 1：启用，0：禁用 |integer(int32)  | integer(int32)   |

**响应示例**:

```json
[
	{
		"countryCode": "",
		"countryOperator": "",
		"customerPrice": 0,
		"goodsSupplySmsConfigId": 0,
		"nameEn": "",
		"nameZh": "",
		"status": 0
	}
]
```



**响应状态**:


| 状态码         | 说明                            |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |IntSmsConfigRespVo|


## 2.短信提交


**接口描述**: 找客服开通通道以后，先通过通道列表获取通道ID，即可以调用此接口发送短信。


**接口地址**:`http://api.sjroom.cn/api/open/int/sms/submit`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
  "account": "",
  "password": "",
  "goodsSupplySmsConfigId": 0,
  "phone": "",
  "sendContent": ""
}
```


**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  | 
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |
|password| 密码  | body | true |string  |
|goodsSupplySmsConfigId| 通道id  | body | true |integer(int64)  |
|phone| 检测号码，最多支持一万个。  | body | true |string  |    
|sendContent| 短信内容  | body | true |string  |   


**响应参数**:

| 参数名称         | 参数说明     |     in |      数据类型  |  
| ------------ | -------------------------------- |--------|----|
|stateCode| 状态码  | body | string  |    
|stateMsg| 消息  | body | string  |
|data| 批次号  | body | string  |


**响应示例**:

```json
{
  "stateCode": "200",
  "stateMsg": "成功",
  "data": "xx"
}
```



**响应状态**:


| 状态码         | 说明                            |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  ||


## 3.短信回执查询


**接口描述**: 根据批次号查询，该短信是否发送完成。


**接口地址**:`http://api.sjroom.cn/api/open/int/sms/query`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  |  
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |  
|password| 密码  | body | true |string  |
|batchNo| 批次号  | body | true |string  |

**请求示例**：
```json
{
  "account": "",
  "password": "",
  "batchNo": ""
}
```


**响应参数**:


| 参数名称         | 参数说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|failPhones| 失败手机号码  |array  |    |
|failedNum| 失败条数(个)  |integer(int64)  | integer(int64)   |
|successNum| 成功条数(个)  |integer(int64)  | integer(int64)   |
|successPhones| 成功手机号码  |array  |    |
|totalNum| 总条数(个)=成功条数+失败条数  |integer(int64)  | integer(int64)   |

**响应示例**:

```json
{
	"failPhones": [],
	"failedNum": 0,
	"successNum": 0,
	"successPhones": [],
	"totalNum": 0
}
```


**响应状态**:


| 状态码         | 说明                            |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |IntSmsOpenQueryRespVo|

## 4.查询（余额）


**接口描述**: 查询余额


**接口地址**:`http://api.sjroom.cn/api/open/int/sms/balance`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  | 
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |    
|password| 密码  | body | true |string  |    


**请求示例**：
```json
{
	"account": "",
	"password": ""
}
```


**响应参数**:

| 参数名称         | 参数说明     |     in |      数据类型  |  
| ------------ | -------------------------------- |--------|----|
|stateCode| 状态码  | body | string  |    
|stateMsg| 消息  | body | string  |
|data| 返回余额  | body | string  |

**响应示例**:

```json
{
  "stateCode": "200",
  "stateMsg": "成功",
  "data": "0"
}

```
| 状态码         | 说明                            |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  ||
