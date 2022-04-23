**空号检测服务**

**HOST**: http://api.sjroom.cn/doc.html

**联系人**: manson 18973716781

**Version**:V1.0

# 1.空号检测API

## 号码检测-号码


**接口描述**: 通过传入手机号码，检测后返回响应状态。


**接口地址**:`http://api.sjroom.cn/api/open/check`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求示例**：
```json
{
	"account": "",
	"password": "",
	"phone": ""
}
```


**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  | 
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |    
|password| 密码  | body | true |string  |    
|phone| 检测号码（多个号码请用逗号隔开），最多支持一万个。  | body | false |string     |

**请求示例**:

```json
{
	"account": "xxx",
	"password": "xxx",
	"phone": "18973716781"
}
```
**响应参数**:

| 参数名称         | 参数说明     |     in |      数据类型  |  
| ------------ | -------------------------------- |--------|----|
|stateCode| 状态码  | body | string  |    
|stateMsg| 消息  | body | string  |
|data| 返回体  | body | string  |
|batchNo| 批次号 | data | string  |
|blank| 空号手机号码，列表 | data | array  |
|unknow| 沉默手机号码，列表 | data | array  |
|active| 活跃手机号码，列表 | data | array  |
|risk| 风险手机号码，列表 | data | array  |


**响应示例**:
```json
{
  "stateCode": "200",
  "stateMsg": "成功",
  "data": {
    "batchNo": "xxxxx",
    "blank": [],
    "unknow": [],
    "active": [
      "18973716781"
    ],
    "risk": []
  }
}
```
**响应状态**:


| 状态码         | 说明                            | 
| ------------ | -------------------------------- |
| 200 | OK  |
| 500 | 错误，返回错误信息  |

## 号码检测-文件检测


**接口描述**: 通过文件包，进行检测，返回对应状态的包。


**接口地址**:`http://api.sjroom.cn/api/open/file/check`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  | 
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |     
|password| 密码  | body | true |string  |    
|fileUrl| 公网能访问的URL  | body | true |string  |

**请求示例**：
```json
{
  "account": "xxx",
  "password": "xxx",   
  "fileUrl": "http://xxxxx/xx.txt"
}
```

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
  "data": "APIxxx"
}
```

**响应状态**:


| 状态码         | 说明                            | 
| ------------ | -------------------------------- |
| 200 | OK  |
| 201 | 检测中  |
| 500 | 错误，返回错误信息  |

## 2.号码检测-查询详情


**接口描述**:


**接口地址**:`http://api.sjroom.cn/api/open/check/detail`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`



**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  | 
| ------------ | -------------------------------- |-----------|--------|----|
|account| 账号  | body | true |string  |
|password| 密码  | body | true |string  |    
|batchNo| 批次号  | body | true |string  |    
|isDownLoadExcel| 是否需要excel包  | body | false |boolean  |

**请求示例**：
```json
{
  "account": "",
  "password": "",
  "batchNo": "",
  "isDownLoadExcel": false
}
```

**响应参数**:


| 参数名称         | 参数说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|data|   |DetectionRespVo  | DetectionRespVo   |
|stateCode|   |string  |    |
|stateMsg|   |string  |    |



**DetectionRespVo**

| 参数名称         | 参数说明                             |    类型 |  schema |
| ------------ | ------------------|--------|----------- |
|activeNum | 活跃号条数(个)   |integer(int64)  |    |
|activeNumUrl | 活跃号条数包   |string  |    |
|batchNo | 批次号-讯秒云   |string  |    |
|blankNum | 空号条数(个)   |integer(int64)  |    |
|blankNumUrl | 空号条数包   |string  |    |
|detectionNum | 检测条数(个)   |integer(int64)  |    |
|detectionNumExcelUrl | 检测包-excel   |string  |    |
|detectionNumUrl | 检测包   |string  |    |
|fileName | 文件名称   |string  |    |
|originNumUrl | 检测原始包   |string  |    |
|riskNum | 风险号条数(个)   |integer(int64)  |    |
|riskNumUrl | 风险号条数包   |string  |    |
|unKnowNum | 沉默号条数(个)   |integer(int64)  |    |
|unKnowNumUrl | 沉默号条数包   |string  |    |

**响应示例**:

```json
{
	"data": {
		"activeNum": 0,
		"activeNumUrl": "",
		"batchNo": "",
		"blankNum": 0,
		"blankNumUrl": "",
		"detectionNum": 0,
		"detectionNumExcelUrl": "",
		"detectionNumUrl": "",
		"fileName": "",
		"originNumUrl": "",
		"riskNum": 0,
		"riskNumUrl": "",
		"unKnowNum": 0,
		"unKnowNumUrl": ""
	},
	"stateCode": "",
	"stateMsg": ""
}
```

**响应状态**:


| 状态码         | 说明                            |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |RespVo«DetectionRespVo»|


## 3.查询（条数）


**接口描述**:


**接口地址**:`http://api.sjroom.cn/api/open/query`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`


**请求参数**：

| 参数名称         | 参数说明     |     in |  是否必须      |  数据类型  |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|account| 账号  | body | false |string  |    |
|password| 密码  | body | false |string  |    |

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
