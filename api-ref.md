# API参考

本文为您汇总了内容中心中提供可调用的API信息。



## 概述

本文使用基于API URL发起的HTTP或HPPTS请求的用户， 内容中心并无提供SDK方式。

不同API模块的请求会有不同校验签名，需要在模块说明中查看调用机制和签名生成方式，为了方便显示，我们将部分URL地址参数将使用中括号进行占位示意。接口调用成功会显示返回参数，调用失败则显示相应报错，具体API错误码需要查看功能模块内信息分析排查。



### 导航

您可以通过下表查找可调用的API模块功能。

<table>
	<tr>
	    <th>板块</th>
	    <th>功能模块</th>
	    <th>描述</th>  
	</tr >
    <tr>
	    <td rowspan="1">PGC</td>
	    <td >调取文章数据</td>
	    <td >获取内容中心指定文章数据</td>
	</tr>
    <tr>
	    <td rowspan="2">UGC</td>
	    <td >存储内容数据</td>
	    <td >指定平台对发送的数据进行存储</td>
	</tr>
    <tr>
        <td >查询内容数据</td>
	    <td >授权平台通过标示获取指定存储数据</td>
	</tr>
    <tr >
	    <td rowspan="9">内容检测</td>
	    <td>上传文件</td>
	    <td>临时文件上传获取授权信息</td>
	</tr>
	<tr >
	    <td>文本</td>
	    <td>检测文本中的内容</td>
	</tr>
	<tr>
	    <td>图片</td>
	    <td>检测图片违规或识别图片中的不良信息</td>
	</tr>
	<tr>
	    <td>文件</td>
	    <td>解析待检测文件中的图片和文字部分，并分别检测其中的违规内容</td>
	</tr>
	<tr>
	    <td>音频</td>
	    <td>检测音频文件中的违规信息</td>
	</tr>
	<tr>
        <td>视频</td>
	    <td>检测视频中的违规内容或不良信息</td>
	</tr>
	<tr>
	    <td>直播 - 音频流</td>
	    <td>检查音频流中的违规信息</td>
	</tr>
	<tr>
	    <td>直播 - 视频流</td>
	    <td>检查视频流中的违规信息</td>
	</tr>
    <tr>
	    <td>结果查询</td>
	    <td>返回检测信息</td>
	</tr>
	<tr>
	    <td rowspan="4">标签库</td>
	    <td>标签数据</td>
	    <td>获取标签属性及其层级数据</td>
	</tr>
    <tr>
	    <td>标签群组</td>
	    <td>获取指定标签映射的标签组</td>
	</tr>
	<tr>
	    <td>绑定标签</td>
	    <td>登记使用标签数据</td>
	</tr>
    <tr>
	    <td>统计回访</td>
	    <td>使用标签数据时统计</td>
	</tr>
    <tr>
	    <td rowspan="2">收藏夹</td>
	    <td >目录管理</td>
	    <td >以用户为单位创建划分不同目录管理各类型的内容数据，删除内容数据</td>
	</tr>
    <tr>
        <td >收藏管理</td>
	    <td >指定目录进行类型记录</td>
    </tr>
	<tr>
	    <td rowspan="1">营销支持</td>
	    <td >二维码/九宫格图片合并</td>
	    <td >图片素材生成带二维码及九宫格图片地址</td>
	</tr>
	<tr>
	    <td rowspan="1">渠道数据</td>
	    <td >界面新闻</td>
	    <td >接入同步界面新闻文章数据，撤销文章</td>
	</tr>
</table>






## 板块

### PGC

------------------------------

内容中心提供对文章内容进行调取功能。



##### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |



##### 通信协议

**https**



##### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



##### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化.



#### 调取文章数据-接口

------

接口路径：**/{version}/ability/pgc/article**



接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/pgc/artcile?id={id}&categoryId={categoryId}
```

请求参数示例:

| 名称       | 类型   | 必须 | 说明         |
| ---------- | ------ | ---- | ------------ |
| id         | string | 是   | 文章标示     |
| categoryId | string | 是   | 文章栏目标示 |


返回数据示例：

```
{
  "code": 200,
  "data": {
    "isUnpublishTask": false,
    "types": [
      {
        "uid": "blt02387252a34e549b",
        "displayTitle": "Test-02-08052",
        "contentUrl": "http://pages.amway.com.cn/t/blt02387252a34e549b/20200715/01/a.html",
        "previewUrl": "http://pages.amway.com.cn/p/t/blt02387252a34e549b/20200715/01/a.html"
      }
    ],
    "updatedBy": "blt7f3bcc57d3306a37",
    "previewUrl": "http://pages.amway.com.cn/p/20200715/01/a.html",
    "workflowStatus": 0,
    "pushStatus": 0,
    "title": "测试文章-2020071",
    "locale": "zh-cn",
    "version": 5,
    "tags": [
      "测试",
      "文章"
    ],
    "contentStatus": 0,
    "uid": "blt8e9eea59e72919cd",
    "createdAt": 1594985430067,
    "contentUrl": "http://pages.amway.com.cn/20200715/01/a.html",
    "createdBy": "blt7f3bcc57d3306a37",
    "isPublishTask": false,
    "fields": {
      "contentImages": [],
      "attachments": [
        {
          "filename": "4_公众号_01推送任务列表.png",
          "size": "215000",
          "assetId": "blt59b269b3ee04967c",
          "contentType": "image/png",
          "url": "https://images.contentstack.io/v3/assets/blt4965ba1948428719/blt59b269b3ee04967c/5f0c0bf4aa875d7f39ead513/4_公众号_01推送任务列表.png"
        }
      ],
      "typeName": "测试分类",
      "description": "测试文章说明",
      "source": "category",
      "categoryName": "ArticleTemplate",
      "thumbnailType": "L",
      "operator": "CNVMKT21",
      "allowShare": true,
      "content": "<h1>别让“中国式谦虚”丢了孩子气场全开的勇气</h1><p><a href=\"https://ch.amwaynet.com.cn/content/china/accl/solr/searchResults.html?category=%E4%BA%B2%E5%AD%90%E8%82%B2%E5%84%BF&categoryType=sourceTag\">亲子育儿</a> &nbsp;</p><p>大年初一视频拜年的时候，和表姐聊了几句，说到她家的孩子今年上小学，第一次期末考试就得了全班第一。</p></p>",
      "products": [
        {
          "itemNumber": "89033",
          "quantity": 100
        },
        {
          "itemNumber": "78965",
          "quantity": 50
        }
      ],
      "path": "/20200715/01/a.html",
      "strippedContent": "别让“中国式谦虚”丢了孩子气场全开的勇气",
      "host": "ch.amwaynet.com.cn",
      "tagsPath": [],
      "creator": "",
      "contentTag": "文章",
      "author": "张三",
      "aboReadonly": true,
      "contentAudio": [
        {
          "audioLen": 1000,
          "assetId": "blt59b269b3ee04967c",
          "title": "测试音乐",
          "contentType": "audio/mp3",
          "url": "https://images.contentstack.io/v3/assets/blt4965ba1948428719/blt59b269b3ee04967c/5f0c0bf4aa875d7f39ead513/4_公众号_01推送任务列表.png"
        }
      ],
      "allowIdentities": [
        "ABO",
        "FOA"
      ],
      "displayPublishTime": true,
      "contentVideos": [],
      "typeId": "test_type_id_1",
      "keyTags": [
        "测试",
        "文章"
      ],
      "thumbnails": [
        {
          "assetId": "blt59b269b3ee04967c",
          "type": "L",
          "url": "https://images.contentstack.io/v3/assets/blt4965ba1948428719/blt59b269b3ee04967c/5f0c0bf4aa875d7f39ead513/4_公众号_01推送任务列表.png"
        }
      ],
      "noSearch": true,
      "categoryId": "article_template",
      "promotion": true
    },
    "publishDetails": [
      {
        "environment": "blt3dfb83bad4e64684",
        "time": 1595812839033,
        "locale": "zh-cn",
        "user": "blt7f3bcc57d3306a37"
      }
    ],
    "publishStatus": true,
    "updatedAt": 1596008255420
  }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |





### UGC

------------------------------

不同平台中的内容可通过UGC板块功能进行存储，调取。



##### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |



##### 通信协议

**https**



##### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



##### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化.



#### 存储数据

##### 内容存储-接口

------

接口路径：**/{version}/ability/ugc/cas**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| PUT         | 存储   |      |

请求示例路径

```
PUT /v1/ability/ugc/cas
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"type":"string",
	"url":"string",
	"content":"string",
	"extra":"jsonString",
	"id":"string"
}
```

body 数据参数示例:

| 名称    | 类型   | 必须 | 说明                                                      |
| ------- | ------ | ---- | --------------------------------------------------------- |
| type    | string | 是   | cas业务类型: 图文-post，文本-word，图片-image，视频-video |
| url     | string | 否   | 单一类型文件URL参数, 图片-image / 视频-video 时必填.      |
| content | string | 否   | 存储字符内容,  图文-post / 文本-word 时必填.              |
| extra   | string | 是   | 额外业务内容                                              |
| id      | string | 是   | 业务数据唯一标示, 例子:"typeid_uid_cpid_cid"                                          |

返回数据示例：

```
{
    "code": 200,
    "data": {
    	"type":"string",
		"id":"string"
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称 | 类型   | 说明             |
| ---- | ------ | ---------------- |
| type | string | cas类型          |
| id   | string | 业务数据唯一标示 |



##### 查询内容-接口

------

接口路径：**/{version}/ability/ugc/cas**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/ugc/cas?id={id}
```
请求参数示例:

| 名称 | 类型   | 必须 | 说明                       |
| ---- | ------ | ---- | -------------------------- |
| id   | string | 是   | 业务数据唯一标示 |


返回数据示例：

```
{
    "code": 200,
    "data": {
        "type":"string",
        "url":"string",
        "content":"string",
        "extra":"jsonString",
        "id":"string"
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称    | 类型   | 必须 | 说明                                                      |
| ------- | ------ | ---- | --------------------------------------------------------- |
| type    | string | 是   | cas业务类型: 图文-post，文本-word，图片-image，视频-video |
| url     | string | 否   | 单一类型文件URL参数, 图片-image / 视频-video 时必填.      |
| content | string | 否   | 存储字符内容,  图文-post / 文本-word 时必填.              |
| extra   | string | 是   | 额外业务内容                                              |
| id      | string | 是   | 业务数据唯一标示, 例子:"typeid_uid_cpid_cid"              |







### 内容检测

------------------------------

可对检测内容进行风险，敏感，违规内容进行筛查，同时适配多种策略对内容检测细节进行处理。提供文本，图片，语音，视频，直播进行数据内容的检测能力并提供结果反馈。



##### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |



##### 通信协议

**https**



##### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



##### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化.



#### 上传文件

##### 获取临时授权token-接口

------

接口路径：**/{version}/ability/green/token**

| Head Parameter | type   | value  | Memo                 |
| -------------- | ------ | ------ | -------------------- |
| Platform       | string | aliyun | 服务平台标示: aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 获取   |      |

请求示例路径

```
GET /v1/ability/green/token
```

返回数据示例：

```
{
  "code": 200,
  "data": {
    "token":{
        "accessKeyId": "string",
        "securityToken": "string",
        "accessKeySecret": "string",
        "expiration": "2020-08-17T06:15:17Z"
    },
    "info":{
    	"bucket": "string",
    	"dir": "string"
    }
  }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型   | 说明     |
| ----- | ------ | -------- |
| token | object | 密钥信息 |
| info  | object | 上传信息 |

token 说明：

| 名称            | 类型   | 说明     |
| --------------- | ------ | -------- |
| accessKeyId     | string | 密钥ID   |
| securityToken   | number | 密钥密匙 |
| accessKeySecret | number | 密钥     |
| expiration      | string | 过期时间 |

info 说明：

| 名称   | 类型   | 说明         |
| ------ | ------ | ------------ |
| bucket | string | 对象存储桶   |
| dir    | string | 存储目录路径 |



#### 检测内容

##### 文本内容检测-接口

------

接口路径：**/{version}/ability/green/text**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/text
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"content":"美好生活"
		},
		{
			"content":"减少呼吸开始"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

tasks 数组中单个对象参数说明:

| 名称    | 类型   | 必须 | 说明     |
| ------- | ------ | ---- | -------- |
| content | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"content":"美好生活",
        		"status":"OK",
        		"results": [
                    {
                        "suggestion":"pass",
                        "filteredContent":"美好生活",
                        "label":"normal",
                        "hitWords":[]
                    }
        		]
        	},
        	{
        		"taskCode": "string",
        		"content":"减少呼吸开始",
        		"status":"OK",
        		"results": [
                    {
                        "suggestion":"block",
                        "filteredContent":"减少**开始",
                        "label":"customized",
                        "hitWords":["呼吸"]
                    }
        		]
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型          | 说明                                        |
| -------- | ------------- | ------------------------------------------- |
| taskCode | string        | 执行                                        |
| content  | string        | 检查文本原值                                |
| status   | string        | 任务状态, OK / PEDDING / CANCEL             |
| results  | array(object) | 检测结果, 句中会有不同方向结果,通常只有单个 |

results 数组单个数据体说明：

| 名称            | 类型          | 说明                       |
| --------------- | ------------- | -------------------------- |
| suggestion      | string        | 处理结果 pass/block/review |
| filteredContent | string        | 屏蔽文本处理值             |
| label           | string        | 命中类型                   |
| hitWords        | array(string) | 击中词集合                 |



##### 图片文件检测-接口

----------------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 图片链接支持以下协议：HTTP和HTTPS。
- 图片支持以下格式：PNG、JPG、JPEG、BMP、GIF、WEBP。
- 图片大小限制为10MB以内。
- 图片下载时间限制为3秒内，如果下载时间超过3秒，返回下载超时。
- 图片像素建议不低于256*256，像素过低可能会影响识别效果



接口路径：**/{version}/ability/green/image**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/image
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		},
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "OK"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |





##### 文件检测-接口

---------------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 文本内容支持以下格式：PDF、WORD、TXT、PPT、EXCEL、OUTLOOK、VISIO、ZIP、TAR、RTF。
- 图片内容支持以下格式：PDF。
- 支持的文件大小为5M以内。



接口路径：**/{version}/ability/green/file**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/file
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		},
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "PADDING"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |



##### 音频文件检测-接口

---------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 支持的语音文件大小小于200M。
- 支持的音频文件格式：MP3、WAV、AAC、WMA、OGG、M4A、AMR、AUDIO。
- 支持的视频文件格式：AVI、FLV、MP4、MPG、ASF、WMV、MOV、RMVB、RM。



接口路径：**/{version}/ability/green/voice**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/voice
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		},
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "PADDING"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |



##### 视频文件检测-接口

---------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 视频文件链接支持以下协议：HTTP和HTTPS。
- 视频文件支持以下格式：AVI、FLV、MP4、MPG、ASF、WMV、MOV、WMA、RMVB、RM、FLASH、TS。
- 视频大小限制：单个视频大小不超过200MB。



接口路径：**/{version}/ability/green/video**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/video
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		},
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "PADDING"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |



##### 直播-音频流检测-接口

---------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 支持检测的语音流格式：M3U8、FLV。
- 语音流支持的协议：HTTP、RTMP、RTSP。
- 语音流时长小于24小时。



接口路径：**/{version}/ability/green/live/voice**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/live/voice?callback={callback}&seed={seed}
```

请求参数示例:

| 名称     | 类型   | 必须 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | string | 否   | 回调地址(URLEncode编码地址)，有结果时POST请求该地址，当该字段为空时，您必须定时检索检测结果。 |
| seed     | string | 否   | 回调通知请求中的签名, 传callback下必传                       |

POST回调请求参数示例:

| 名称     | 类型   | 必须 | 说明                                               |
| -------- | ------ | ---- | -------------------------------------------------- |
| checksum | string | 否   | appId+seed+content拼成字符串，通过SHA256算法生成。 |
| content  | string | 否   | 以POST进行RAW的JSON发送                            |



请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "PADDING"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |



##### 直播-视频流检测-接口

---------------------------------

###### 异步处理

需要异步处理，请查询结果接口进行检测结果查询。

- 视频流支持以下协议：RTMP、HLS、HTTP-FLV、RTSP。
- 视频流时长限制：单个视频流检测任务最长支持24小时，超过24小时任务自动结束。



接口路径：**/{version}/ability/green/live/video**

| Head Parameter | type   | value  | Memo                     |
| -------------- | ------ | ------ | ------------------------ |
| Platform       | string | aliyun | 服务平台标示, 默认aliyun |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 检测   |      |

请求示例路径

```
POST /v1/ability/green/live/video
```

请求参数示例:

| 名称     | 类型   | 必须 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | string | 否   | 回调地址(URLEncode编码地址)，有结果时POST请求该地址，当该字段为空时，您必须定时检索检测结果。 |
| seed     | string | 否   | 回调通知请求中的签名, 传callback下必传                       |

POST回调请求参数示例:

| 名称     | 类型   | 必须 | 说明                                               |
| -------- | ------ | ---- | -------------------------------------------------- |
| checksum | string | 否   | appId+seed+content拼成字符串，通过SHA256算法生成。 |
| content  | string | 否   | 以POST进行RAW的JSON发送                            |



请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"tasks":[
		{
			"url":"string"
		}
	]
}
```

body数据参数说明:

| 名称  | 类型          | 必须 | 说明                                           |
| ----- | ------------- | ---- | ---------------------------------------------- |
| tasks | array(object) | 是   | 检测任务数组, 每个为一个任务执行并返回taskCode |

contents数组中单个对象参数说明:

| 名称 | 类型   | 必须 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | string | 是   | 检查文本 |

返回数据示例：

```
{
	"code": 0,
	"data":{
        "tasks":[
        	{
        		"taskCode": "string",
        		"url": "string",
        		"status": "PADDING"
        	}
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | string | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明 |
| ----- | ------------- | ---- |
| tasks | array[object] | 执行 |

tasks 说明：

| 名称     | 类型   | 说明                            |
| -------- | ------ | ------------------------------- |
| taskCode | string | 执行                            |
| url      | string | 命中图片地址                    |
| status   | string | 任务状态, OK / PEDDING / CANCEL |













##### 结果查询-接口

------

接口路径：**/{version}/ability/green/results**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/green/results?taskCode={taskCode}
```

请求参数示例:

| 名称     | 类型   | 必须 | 说明         |
| -------- | ------ | ---- | ------------ |
| taskCode | string | 是   | 执行记录编码 |

基本返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": []
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称         | 类型          | 说明                                                         |
| ------------ | ------------- | ------------------------------------------------------------ |
| taskCode     | string        | 任务执行编码                                                 |
| type         | string        | 任务执行类型 : text / image / file / voice / video           |
| createDate   | string        | 创建时间，需要符合 ISO-8601 格式                             |
| callbackDate | string        | 结果响应时间，需要符合 ISO-8601 格式，同步执行与createDate相同 |
| results      | array(object) | 检测结果数据体                                               |

--------------------------------------

text 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"text",
        "content":"美好生活",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results":[
            {
                "suggestion":"pass",
                "filteredContent":"美好生活",
                "label":"normal",
                "hitWords":[]
            }
        ]
	}
}
```

text / results 数组单个数据体说明：

| 名称            | 类型          | 说明                       |
| --------------- | ------------- | -------------------------- |
| suggestion      | string        | 处理结果 pass/block/review |
| filteredContent | string        | 屏蔽文本处理值             |
| label           | string        | 命中类型                   |
| hitWords        | array(string) | 击中词集合                 |

--------------------------------------

image 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"image",
        "url":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": [
            {
                "label":"sexy",
                "rate": 72.5,
                "scene":"porn",
                "suggestion":"review",
            },{
                "label": "normal",
                "rate": 100.0,
                "scene": "terrorism",
                "suggestion": "pass"
            }, {
                "label": "normal",
                "rate": 99.9,
                "scene": "ad",
                "suggestion": "pass"
            }, {
                "label": "normal",
                "rate": 99.91,
                "scene": "qrcode",
                "suggestion": "pass"
            }, {
                "label": "normal",
                "rate": 100.0,
                "scene": "live",
                "suggestion": "pass"
            }, {
                "label": "normal",
                "rate": 99.9,
                "scene": "logo",
                "suggestion": "pass"
            }
        ]
	}
}
```

image / results 说明：

| 名称       | 类型   | 说明                       |
| ---------- | ------ | -------------------------- |
| suggestion | string | 处理结果 pass/block/review |
| rate       | number | 命中概率                   |
| label      | string | 命中类型                   |
| scene      | string | 命中场景                   |

--------------------------------------

voice 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"voice",
        "url":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": [{
        	"suggestion": "block",
        	"details":[
                {
                    "startTime": 11670,
                    "endTime": 14685,
                    "label": "customized",
                    "text": "超低折扣，大甩卖",
                    "keyword": "甩卖"
                },
                {
                    "startTime": 14685,
                    "endTime": 16065,
                    "label": "ad",
                    "text": "微信12345"
                }
        	]
        }]
	}
}
```

voice / results 说明：

| 名称       | 类型   | 说明                       |
| ---------- | ------ | -------------------------- |
| suggestion | string | 处理结果 pass/block/review |
| details    | number | 文本命中详情               |

voice / results / details说明：

| 名称      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| startTime | number | 句子开始的时间，单位是秒。   |
| endTime   | number | 句子结束的时间，单位是秒。   |
| text      | string | 命中的语音转换成文本的结果。 |
| label     | string | 检测结果的分类               |
| keyword   | string | 命中的自定义词库文字         |

--------------------------------------

video 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"video",
        "url":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": [{
			"image": [{
                "label": "porn",
                "scene": "porn",
                "suggestion": "block"
            }],
            "audio": [{
                "scene": "antispam",
                "label": "customized",
                "suggestion": "block",
                "rate": 99.91,
                "details": [
                	{
                        "startTime": 0,
                        "endTime": 24,
                        "text": "blabla...",
                        "label": "customized"
                    },
                    {
                        "startTime": 24,
                        "endTime": 60,
                        "text": "blabla...",
                        "label": "normal"
                    }
                ]
            }]
        }]
	}
}
```

video / results 说明：

| 名称  | 类型          | 说明                 |
| ----- | ------------- | -------------------- |
| image | array(object) | 影相图片检测结果集合 |
| audio | array(object) | 视频语音检测结果集合 |

video / image 说明：

| 名称       | 类型   | 说明                       |
| ---------- | ------ | -------------------------- |
| label      | string | 检测结果的分类             |
| scene      | string | 命中场景                   |
| suggestion | string | 处理结果 pass/block/review |

video / audio /details 说明：

| 名称      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| startTime | number | 句子开始的时间，单位是秒。   |
| endTime   | number | 句子结束的时间，单位是秒。   |
| text      | string | 命中的语音转换成文本的结果。 |
| label     | string | 检测结果的分类               |
| keyword   | string | 命中的自定义词库文字         |

----------------------------

live-voice 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"live-voice",
        "url":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": [{
        	"suggestion": "block",
        	"details":[
                {
                    "startTime": 11670,
                    "endTime": 14685,
                    "label": "customized",
                    "text": "超低折扣，大甩卖",
                    "keyword": "甩卖",
                    "url":"string"
                }
        	]
        }]
	}
}
```

live-voice / results 说明：

| 名称       | 类型   | 说明                       |
| ---------- | ------ | -------------------------- |
| suggestion | string | 处理结果 pass/block/review |
| details    | number | 文本命中详情               |

live-voice / results / details说明：

| 名称      | 类型   | 说明                                                       |
| --------- | ------ | ---------------------------------------------------------- |
| startTime | number | 句子开始的时间，单位是秒。                                 |
| endTime   | number | 句子结束的时间，单位是秒。                                 |
| text      | string | 命中的语音转换成文本的结果。                               |
| label     | string | 检测结果的分类                                             |
| keyword   | string | 命中的自定义词库文字                                       |
| url       | string | 该段文本对应的语音流的临时访问地址。该地址有效时间为30分钟 |

--------------------------------------

live-video 返回数据示例：

```
{
	"code": 0,
	"data":{
        "taskCode":"string",
        "type":"live-video",
        "url":"string",
        "createDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "callbackDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "results": [{
			"image": [{
                "label": "porn",
                "scene": "porn",
                "suggestion": "block"
            }],
            "audio": [{
                "scene": "antispam",
                "label": "customized",
                "suggestion": "block",
                "rate": 99.91,
                "details": [
                	{
                        "startTime": 0,
                        "endTime": 24,
                        "text": "blabla...",
                        "label": "customized"
                    },
                    {
                        "startTime": 24,
                        "endTime": 60,
                        "text": "blabla...",
                        "label": "normal"
                    }
                ]
            }]
        }]
	}
}
```

live-video / results 说明：

| 名称  | 类型          | 说明                 |
| ----- | ------------- | -------------------- |
| image | array(object) | 影相图片检测结果集合 |
| audio | array(object) | 视频语音检测结果集合 |

live-video / image 说明：

| 名称       | 类型   | 说明                       |
| ---------- | ------ | -------------------------- |
| label      | string | 检测结果的分类             |
| scene      | string | 命中场景                   |
| suggestion | string | 处理结果 pass/block/review |

live-video / audio / details 说明：

| 名称      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| startTime | number | 句子开始的时间，单位是秒。   |
| endTime   | number | 句子结束的时间，单位是秒。   |
| text      | string | 命中的语音转换成文本的结果。 |
| label     | string | 检测结果的分类               |
| keyword   | string | 命中的自定义词库文字         |

----------------------------











### 标签库

------------------------------

提供对标签库获取标签数据, 标签群组数据, 绑定标签等场景能力。



##### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |



##### 通信协议

**https**



##### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



##### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化。

`` Head Parameter`` 中的AppId，需要标签库进行分派给其他平台使用。



#### 标签数据

##### 查询平台标签-接口

------

接口路径：**/{version}/ability/tag**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/tag
```

返回数据示例：

```
{
	"code": 0,
	"data":{
        "appId":"string",
        "count": 40,
        "roots": 1,
        "tags":[
            {
                "id": number,
                "code":"t_QUdE0_eEORVfe3pC",
                "appId":"string",
                "name":"string",
                "desc":"string",
                "typeName":"string",
                "pid": 0,
                "validityStartDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "validityEndDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "status": number,
                "approval": number,
                "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "history": [
                	"names": [{
                    	"name":"string",
                    	"createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                    	"replaceDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                    	"replaceName":"string",
                    	"operator":"string"
                    }],
                    "references": [{
                    	"tagCode":"t_QUdE0_eEORVfe3pC",
                    	"tag":{tagObject},
                    	"fromAppId": "string",
                    	"referenceDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                    	"operator":"string"
                    }]
                ],
                "child": [{
                        "id": number,
                        "code":"t_QUdE0_OV6tMwWLVe",
                        "appId":"string",
                        "name":"string",
                        "desc":"string",
                        "typeName":"string",
                        "pid": number,
                        "validityStartDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                        "validityEndDate":"yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                        "status": number,
                        "approval": number,
                        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                		"modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                        "history": [],
                        "child": []
                }]
            }
        ]
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称  | 类型          | 说明                   |
| ----- | ------------- | ---------------------- |
| appId | string        | 平台唯一标识           |
| count | number        | 平台总标签数           |
| roots | number        | 平台根节点数           |
| tags  | array[object] | 平台下自有标签层级数据 |

tags 数组单项说明:

| 名称              | 类型          | 说明                                                         |
| ----------------- | ------------- | ------------------------------------------------------------ |
| id                | string        | 标签流水标示                                                 |
| code              | string        | 标签业务代码, 唯一, t_QUdE0_eEORVfe3pC , t=标签, 第一段为appId, 第二段为10位字符随机码 |
| appId             | string        | 所属平台标示                                                 |
| name              | string        | 标签名称                                                     |
| desc              | string        | 标签描述                                                     |
| typeName          | string        | 标签类型                                                     |
| pid               | number        | 父标签ID                                                     |
| validityStartDate | string        | 有效开始时间，需要符合 ISO-8601 格式                         |
| validityEndDate   | string        | 有效到期时间，需要符合 ISO-8601 格式                         |
| status            | number        | 标签状态 , 临时-0/正常上线-1/停用-2                          |
| approval          | number        | 审批状态, -1= 待审批,  0=审批中,  2= 退回, 3 = 拒绝,  1=通过, 4=拒绝审批中 |
| createDate        | string        | 创建时间，需要符合 ISO-8601 格式                             |
| modifyDate        | string        | 修改时间，需要符合 ISO-8601 格式                             |
| history           | array(object) | 标签名称历史                                                 |
| child             | array(object) | 子层级标签数据, 与tags数组一致                               |

history 说明：

| 名称       | 类型          | 说明         |
| ---------- | ------------- | ------------ |
| names      | array(object) | 历史标签集合 |
| references | array(object) | 历史引用集合 |

name 说明：

| 名称        | 类型   | 说明         |
| ----------- | ------ | ------------ |
| name        | string | 标签名称     |
| createDate  | number | 名称创建时间 |
| fromAppId   | number | 替换时间     |
| replaceName | string | 替换名称     |
| operator    | string | 操作者       |

references 说明：

| 名称          | 类型   | 说明         |
| ------------- | ------ | ------------ |
| tagCode       | string | 标签代码     |
| tag           | object | 标签数据体   |
| fromAppId     | string | 引用来源平台 |
| referenceDate | string | 引用时间     |
| operator      | string | 操作者       |



##### 查询平台指定标签-接口

------

接口路径：**/{version}/ability/tag/{code}**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/tag/{code}
```

返回数据示例：

```
{
	"code": 0,
	"data":{
        "id": 1,
        "code": "t_QUdE0_eEORVfe3pC",
        "appId":"string",
        "name": "string",
        "desc": "string",
        "typeName": "string",
        "pid": 0,
        "validityStartDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "validityEndDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "status": 1,
        "approval": 1,
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "history": [
            "names": [{
                "name":"string",
                "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "replaceDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "replaceName":"string",
                "operator":"string"
            }],
            "references": {
                "tagCode":"t_QUdE0_eEORVfe3pC",
                "tag":{tagObject},
                "fromAppId": "string",
                "referenceDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
                "operator":"string"
            }
        ],
        "child": [{
            "id": 1,
            "code": "t_QUdE0_OV6tMwWLVe",
            "appId":"string",
            "name": "string",
            "desc": "string",
            "typeName": "string",
            "pid": 1,
            "validityStartDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
            "validityEndDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
            "status": 1,
            "approval": 1,
            "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
            "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
            "history": [],
            "child": []
        }]
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 单项说明:

| 名称              | 类型          | 说明                                                         |
| ----------------- | ------------- | ------------------------------------------------------------ |
| id                | string        | 标签流水标示                                                 |
| code              | string        | 标签业务代码, 唯一, t_QUdE0_eEORVfe3pC , t=标签, 第一段为appId, 第二段为10位字符随机码 |
|                   | string        | 所属平台标示                                                 |
| name              | string        | 标签名称                                                     |
| desc              | string        | 标签描述                                                     |
| typeName          | string        | 标签类型                                                     |
| pid               | number        | 父标签ID                                                     |
| validityStartDate | string        | 有效开始时间，需要符合 ISO-8601 格式                         |
| validityEndDate   | string        | 有效到期时间，需要符合 ISO-8601 格式                         |
| status            | number        | 标签状态 , 临时-0/正常上线-1/停用-2                          |
| approval          | number        | 审批状态, -1= 待审批,  0=审批中,  2= 退回, 3 = 拒绝,  1=通过, 4=拒绝审批中 |
| createDate        | string        | 创建时间，需要符合 ISO-8601 格式                             |
| modifyDate        | string        | 修改时间，需要符合 ISO-8601 格式                             |
| history           | array(object) | 标签名称历史                                                 |
| child             | array(object) | 子层级标签数据, 与tags数组一致                               |

history 说明：

| 名称       | 类型          | 说明         |
| ---------- | ------------- | ------------ |
| names      | array(object) | 历史标签集合 |
| references | array(object) | 历史引用集合 |

name 说明：

| 名称        | 类型   | 说明         |
| ----------- | ------ | ------------ |
| name        | string | 标签名称     |
| createDate  | number | 名称创建时间 |
| fromAppId   | number | 替换时间     |
| replaceName | string | 替换名称     |
| operator    | string | 操作者       |

references 说明：

| 名称          | 类型   | 说明         |
| ------------- | ------ | ------------ |
| tagCode       | string | 标签代码     |
| tag           | object | 标签数据体   |
| fromAppId     | string | 引用来源平台 |
| referenceDate | string | 引用时间     |
| operator      | string | 操作者       |



#### 标签群组

##### 查询平台群组列表-接口

------

接口路径：**/{version}/ability/tag/group**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/tag/group
```

返回数据示例：

```
{
	"code": 0,
	"data":[
        {
        	"id": number,
        	"name": "string",
        	"desc": "string",
        	"targetTagId": "string",
        	"targetTagCode": "string",
        	"targetDetail":{tagObjectWithoutChild}
        	"status": number,
            "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
            "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
        }
	]
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称          | 类型   | 说明                                     |
| ------------- | ------ | ---------------------------------------- |
| id            | string | 群组唯一标识                             |
| name          | number | 群组名称                                 |
| desc          | number | 描述                                     |
| targetTagId   | string | 平台下自有的目标标签标示                 |
| targetTagCode | string | 平台下自有的目标标签代码                 |
| targetDetail  | object | 平台下自有的目标标签属性(不带子标签集合) |
| status        | number | 群组状态 , 正常=1 / 停用=2               |
| createDate    | string | 创建时间，需要符合 ISO-8601 格式         |
| modifyDate    | string | 修改时间，需要符合 ISO-8601 格式         |



##### 查询平台单群组数据-接口

------

接口路径：**/{version}/ability/tag/group/target/{targetTagCode}**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求示例路径

```
GET /v1/ability/tag/group
```

返回数据示例：

```
{
	"code": 0,
	"data":{
        "id": number,
        "name": "string",
        "desc": "string",
        "targetTagId": "string",
        "targetTagCode": "string",
        "status": number,
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "targetDetail":{tagObjectWithoutChild}
        "items":[
        	{tagObjectWithoutChild},
        	{tagObjectWithoutChild}
        ]
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称          | 类型          | 说明                                     |
| ------------- | ------------- | ---------------------------------------- |
| id            | string        | 群组唯一标识                             |
| name          | number        | 群组名称                                 |
| desc          | number        | 描述                                     |
| targetTagId   | string        | 平台下自有的目标标签标示                 |
| targetTagCode | string        | 平台下自有的目标标签代码                 |
| targetDetail  | object        | 平台下自有的目标标签属性(不带子标签集合) |
| status        | number        | 群组状态 , 正常=1 / 停用=2               |
| createDate    | string        | 创建时间，需要符合 ISO-8601 格式         |
| modifyDate    | string        | 修改时间，需要符合 ISO-8601 格式         |
| items         | array(object) | 群组标签项, 每个标签属性(不带子标签集合) |



#### 绑定标签

第三方平台对使用标签时, 需要用它们的目标数据对使用标签进行绑定确认.



##### 数据绑定标签-接口

------

接口路径：**/{version}/ability/tag/bing/{tagCode}/object**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| PUT         | 操作   |      |

请求参数示例:

| 名称 | 类型   | 必须 | 说明                       |
| ---- | ------ | ---- | -------------------------- |
| id   | string | 是   | 第三方平台目标对象唯一标识 |

请求示例路径

```
PUT /v1/ability/tag/bing/{tagCode}/object?id=UMxy5mV4RECuPRBQ
```

返回数据示例：

```
{
	"code": 0
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



##### 查询绑定-接口

------

接口路径：**/{version}/ability/tag/bing/object**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 查询   |      |

请求参数示例:

| 名称 | 类型   | 必须 | 说明                                |
| ---- | ------ | ---- | ----------------------------------- |
| id   | string | 是   | AppId下唯一的第三方平台目标对象标识 |

请求示例路径

```
GET /v1/ability/tag/bing/object?id=UMxy5mV4RECuPRBQ
```

返回数据示例：

```
{
	"code": 0,
	"data": [
        {
            "tag": {tagObject},
			"objects": [
            	"id": "UMxy5mV4RECuPRBQ",
	            "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
			]
        }
	]
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称    | 类型   | 说明                             |
| ------- | ------ | -------------------------------- |
| tag     | object | 标签属性                         |
| objects | string | 创建时间，需要符合 ISO-8601 格式 |

objects 说明：

| 名称       | 类型   | 说明                             |
| ---------- | ------ | -------------------------------- |
| id         | string | 第三方平台唯一标识               |
| createDate | string | 创建时间，需要符合 ISO-8601 格式 |





##### 取消绑定-接口

------

接口路径：**/{version}/ability/tag/bing/{tagCode}/object**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action   | Memo |
| ----------- | -------- | ---- |
| DELETE      | 取消绑定 |      |

请求参数示例:

| 名称 | 类型   | 必须 | 说明                       |
| ---- | ------ | ---- | -------------------------- |
| id   | string | 是   | 第三方平台目标对象唯一标识 |

请求示例路径

```
DELETE /v1/ability/tag/bing/{tagCode}/object?id=UMxy5mV4RECuPRBQ
```

返回数据示例：

```
{
	"code": 0,
	"data": {
		"id": "UMxy5mV4RECuPRBQ"
	}
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |
| data | object | 数据体 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |

data 说明：

| 名称 | 类型   | 说明               |
| ---- | ------ | ------------------ |
| id   | string | 第三方平台唯一标识 |



#### 访问标签

第三方平台对标签进行展示时, 需要回调进行统计.



##### 统计回访-接口

------

接口路径：**/{version}/ability/tag/stats/{tagCode}/object/{objectId}**

| Head Parameter | value  | Memo     |
| -------------- | ------ | -------- |
| AppId          | string | 平台标示 |

接口方法

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| POST        | 统计   |      |

请求参数示例:

| 名称 | 类型   | 必须 | 说明                       |
| ---- | ------ | ---- | -------------------------- |
| id   | string | 是   | 第三方平台目标对象唯一标识 |

请求示例路径

```
POST /v1/ability/tag/stats/{tagCode}/object?id={objectId}
```

返回数据示例：

```
{
	"code": 500,
	"message": "tag is not exist"
}
```


返回参数说明：

| 名称    | 类型   | 必显     | 说明 |
| :------ | :----- | :------- | :--- |
| code    | number | 返回码   |      |
| message | string | 错误信息 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



##### 



### 收藏夹

---------------------------------------

用户即Amway Id为单位。用户单位下的管理目录记录图文，文本，图片，视频数据。



#### 开发准备

##### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |



##### 通信协议

**https**



##### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



##### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化.



#### 目录管理

##### 查询列表/新增目录-接口

------

接口路径：**/{version}/ability/favorite/{amwayId}/folder**

接口方法

| Http Method | Action | Memo                 |
| ----------- | ------ | -------------------- |
| GET         | 查询   | 查询用户收藏目录列表 |
| PUT         | 新增   | 新增目录文件夹       |

请求示例路径

```
GET /v1/ability/favorite/{amwayId}/folder
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"folders":[{
        "id": "string",
        "folderName": "string",
        "folderIndex": 0,
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
    }]
}
```

body raw数据中 folders 参数说明:

| 名称        | 类型   | 必须 | Http Method | 说明                             |
| ----------- | ------ | ---- | ----------- | -------------------------------- |
| id          | string | 是   | GET         | 数据唯一标识, PUT时无需带ID      |
| folderName  | string | 是   | GET / PUT   | 文件夹名称,名称唯一,无次级目录   |
| folderIndex | number | 是   | GET / PUT   | 顺序唯一值                       |
| createDate  | string | 是   | GET         | 创建时间，需要符合 ISO-8601 格式 |
| modifyDate  | string | 是   | GET         | 修改时间，需要符合 ISO-8601 格式 |


Http状态码说明：

| Http Code | Description              |
| --------- | ------------------------ |
| 200       | 完成调用 - GET成功返回   |
| 202       | 资源已创建 - PUT成功返回 |
| 204       | 请求未操作               |
| 401       | 鉴权错误                 |
| 500       | 请求无法完成，出现错误   |

返回数据示例：

```
{
	"code": 0,
	"data": [{
        "id": "string",
        "folderName": "string",
        "folderIndex": 0,
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
    }]
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



##### 修改目录-接口

------------------------------

接口路径：**/{version}/ability/favorite/{amwayId}/folder/{folderId}**

接口方法

| Http Method | Action | Memo             |
| ----------- | ------ | ---------------- |
| PETCH       | 修改   | 修改指定目录数据 |

请求示例路径

```
PETCH /v1/ability/favorite/{amwayId}/folder/{folderId}
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"folderName": "string",
    "folderIndex": 0
}
```

body raw数据中 folders 参数说明:

| 名称        | 类型   | 必须 | 说明                           |
| ----------- | ------ | ---- | ------------------------------ |
| folderName  | string | 是   | 文件夹名称,名称唯一,无次级目录 |
| folderIndex | number | 是   | 顺序唯一值                     |


Http状态码说明：

| Http Code | Description              |
| --------- | ------------------------ |
| 200       | 完成修改 - PETCH成功返回 |
| 204       | 请求未操作               |
| 401       | 鉴权错误                 |
| 500       | 请求无法完成，出现错误   |

返回数据示例：

```
{
	"code": 0,
	"data": {
        "id": "string",
        "folderName": "string",
        "folderIndex": 0,
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



#### 收藏管理

##### 收藏内容-接口

------------------------------

接口路径：**/{version}/ability/favorite/{amwayId}/folder/{folderId}**

接口方法

| Http Method | Action | Memo                 |
| ----------- | ------ | -------------------- |
| PUT         | 收藏   | 指定目录进行收藏内容 |

请求示例路径

```
PUT /v1/ability/favorite/{amwayId}/folder/{folderId}
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"name": "string",
	"url": "string",
	"description": "string",
	"type": "string"
}
```

body raw数据中 folders 参数说明:

| 名称        | 类型   | 必须 | 说明                                                         |
| ----------- | ------ | ---- | ------------------------------------------------------------ |
| name        | string | 是   | 内容名称                                                     |
| url         | string | 否   | 内容链接, type除word外必填                                   |
| description | string | 否   | 描述, type为word必填                                         |
| type        | string | 否   | 收藏内容类型<br />图文-post / 文本-word / 图片-image / 视频-video |


Http状态码说明：

| Http Code | Description                |
| --------- | -------------------------- |
| 200       | 完成修改调用 - PUT成功返回 |
| 204       | 请求未操作                 |
| 401       | 鉴权错误                   |
| 500       | 请求无法完成，出现错误     |

返回数据示例：

```
{
	"code": 0,
	"data": {
        "id": "string",
        "name": "string",
        "url": "string",
        "description": "string",
        "type": "string",
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



##### 修改内容-接口

----------------------------------------

接口路径：**/{version}/ability/favorite/{amwayId}/folder/{folderId}/{contentId}**

接口方法

| Http Method | Action | Memo         |
| ----------- | ------ | ------------ |
| PETCH       | 修改   | 修改收藏属性 |

请求示例路径

```
PETCH /v1/ability/favorite/{amwayId}/folder/{folderId}/{contentId}
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
{
	"name":"string",
	"description":"string"
}
```

body raw数据中 folders 参数说明:

| 名称        | 类型   | 必须 | 说明                 |
| ----------- | ------ | ---- | -------------------- |
| name        | string | 是   | 内容名称             |
| description | string | 否   | 描述, type为word必填 |


Http状态码说明：

| Http Code | Description                |
| --------- | -------------------------- |
| 200       | 完成修改调用 - PUT成功返回 |
| 204       | 请求未操作                 |
| 401       | 鉴权错误                   |
| 500       | 请求无法完成，出现错误     |

返回数据示例：

```
{
	"code": 0,
	"data": {
        "id": "string",
        "name": "string",
        "url": "string",
        "description": "string",
        "type": "string",
        "createDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
        "modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
    }
}
```


返回参数说明：

| 名称 | 类型   | 必显   | 说明 |
| :--- | :----- | :----- | :--- |
| code | number | 返回码 |      |

code 返回码说明：

| 返回码 | 说明     | 备注 |
| :----- | :------- | ---- |
| 0      | 操作成功 |      |
| 500    | 内部错误 |      |



### 营销支持

-----------------------------------

#### 二维码/九宫格图片合并

接口图片数据来源于AEM后台，AEM后台新增文章缩略图（大图、小图、三图）并通过CMS同步到openSearch的图片数据，文章和图片新增附件、视频清晰度、文章缩略图、九宫格缩略图几个字段上传到openSearch。

通过接口即可选定图片进行带二维码图片的生成输出图片使用地址。

--------------------------------------------

##### 界面数据操作使用

接口地址：
```
https://prwqa.amwaynet.com.cn/restful/creteQRImgMerge?ada={加密账号}&id={图片ID}
```

1、ada号需要加密处理测试加密账号如附件，可使用加密的账号替换括号文字部分；

2、id为二维码图片或九宫格图片的id（紫色字部分），可在AEM上拿到id进行填写，取id的规则见下：

###### 二维码图片

A.访问二维码图片http://10.140.211.60:4502/siteadmin#/content/china/accl/qrcodeimages

B.在二维码图片列表中打开二维码详情页，点编辑，复制图片URL即可

![](http://cc-cdn.amway.com.cn/docs/image004.jpg)

###### 九宫格图片

A.访问九宫格图片列表http://10.140.211.60:4502/siteadmin#/content/china/accl/aaworkshop/squareMng

B.id取九宫图片路径去掉域名+Name，如/content/china/accl/aaworkshop/squareMng/nutrilite/004

![](http://cc-cdn.amway.com.cn/docs/image005.jpg)

###### 拼接使用

把拼接好的链接在浏览器中访问，扫码即可跳转到AEM上配置的对应链接中。

例如：

二维码图片链接：https://prwqa.amwaynet.com.cn/restful/creteQRImgMerge?ada=7j0u0Q4GBVYOgZwCSeQTHQ==&id=https://bizqa.amwaynet.com.cn/content/dam/china/accl/content_hub/yunzhidao/%E7%BA%BD%E5%B4%94%E8%8E%B1%C2%AE%E9%92%99%E9%95%81%E7%BB%B4D%E5%92%80%E5%9A%BC%E7%89%87%EF%BC%88%E5%84%BF%E7%AB%A5%E5%9E%8B%EF%BC%892.jpg

九宫格图片链接：https://prwqa.amwaynet.com.cn/restful/creteQRImgMerge?ada=7j0u0Q4GBVYOgZwCSeQTHQ==&id=/content/china/accl/aaworkshop/squareMng/nutrilite/005

--------------------------------------------

##### 开发准备

###### 访问域名

| 环境 | 域名                       |
| ---- | -------------------------- |
| PD   | aaworkshop.amwaynet.com.cn |
| QA   | prwqa.amwaynet.com.cn      |

###### 通信协议

###### **https**



**接口路径**

```
/restful/creteQRImgMerge
```

接口方法：

| Http Method | Action | Memo |
| ----------- | ------ | ---- |
| GET         | 访问   |      |

**请求路径示例**

```
GET /restful/creteQRImgMerge?ada={ada}&id={id}
```

**请求参数说明**

| 元素 | 类型   | 备注                                      | 是否必填 |
| :--- | :----- | :---------------------------------------- | :------- |
| ada  | String | 加密后的ada账号(加密解密方式参照附件文档) | 是       |
| id   | String | 对应openSearch图片的id                    |          |

**返回结果**
接口成功会返回一张二维码图片；

**错误返回参数说明**

| 元素      | 类型   | 备注                       |
| :-------- | :----- | :------------------------- |
| errorCode | String | 错误编号（AW_001，AW_002） |
| errorMsg  | String | 错误信息                   |
| status    | String | 状态                       |

**错误返回示例**

```
{
	"errorCode": "AW_002",
	"errorMsg": "ada不存在",
	"status": "fail"
}
```



### 渠道数据

--------------------------------------------

#### 界面新闻

通过界面新闻服务端接入，同步界面新闻已收集的各渠道新闻文章到内容中心指定栏目中。同时给予界面新闻在紧急撤档时，可对指定已同步文章进行下架操作。

##### 开发准备

###### 访问域名

| 环境 | 域名                   |
| ---- | ---------------------- |
| Prod | cc-api.amway.com.cn    |
| QA   | cc-rc-api.amway.com.cn |

###### 通信协议

**https**



###### 鉴权方式

- 请求Header中添加一个”Authorization“参数；
- Authorization字段的值的格式为“APPCODE ＋ 半角空格 ＋APPCODE值”。
- APPCODE 另行分发
- X-Ca-Nonce 需传入一个随机字符



###### 调用版本

**{version} **当前值为 ``v1``，根据内容中心版本变化.

------



##### 新闻-新增/更新-接口

###### 接口说明

该接口用于渠道-界面新闻对新闻项数据进行写入内容中心指定Stack中.

单次调用条数不能大于10条记录

------

###### 接口信息

接口路径：**/{version}/news/jiemian**

接口方法

| Http Method | Action | Memo     |
| ----------- | ------ | -------- |
| PUT         | 新增   | 数组批量 |
| PATCH       | 更新   | 数组批量 |

请求示例路径

```
PUT /v1/news/jiemian
```

请求body数据示例:

**字段值为空则无需传递此参数**

```
[{
	"id": "string",
	"title": "string",
	"digest": "string",
	"displayType": 1,
	"link": "string",
	"locale": "string",
	"categroyId": "string",
	"categroyName": "string",
	"coverImages": ["string","string"],
	"description": "string",
	"tags": ["string","string"],
	"hit": 100,
	"author": "string",
	"source": "string",
	"originalTitle": "string",
	"originalLink": "string",
	"modifyDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX",
	"publishDate": "yyyy-MM-dd'T'HH:mm:ss.SSSXXX"
}]
```

请求数组中单个对象参数说明:

| 名称          | 类型     | 必须 | 说明                                                         |
| ------------- | -------- | ---- | ------------------------------------------------------------ |
| id            | string   | 是   | 新闻唯一标识                                                 |
| title         | string   | 是   | 新闻标题                                                     |
| digest        | string   | 否   | 新闻摘要                                                     |
| displayType   | number   | 是   | 界面新闻应用的新闻列表中，存在右侧细图新闻项，及大图居中新闻项，需要提供区分此类型新闻的字段标识。<br/>1=右小图，2=大图带摘要，3=大图不带摘要，4=三小图模式 |
| link          | string   | 是   | 移动端链接                                                   |
| locale        | string   | 否   | 语言代码与国家地区缩写标识，默认“zh-cn”，e.g. “en-us”        |
| categroyId    | string   | 是   | 所属栏目唯一标识                                             |
| categroyName  | string   | 是   | 所属栏目名称                                                 |
| coverImages   | string[] | 是   | 封面图地址数组，每个下标值存放一个地址信息                   |
| description   | string   | 是   | 无法引用使用Class样式. <br>如内容必要样式，协助把外联内联样式转换为HTML标准标签进行描述。<br>无法转换请协助清除样式相关属性及值，可保留HTML标准标签。<br/>https://www.w3schools.com/tags/default.asp |
| tags          | string[] | 是   | 新闻文章的标签描述或名称数组，每个下标值存放一个标签信息     |
| hit           | number   | 否   | 浏览数                                                       |
| author        | string   | 是   | 作者/编辑/界面号名称                                         |
| source        | string   | 否   | 来源                                                         |
| originalTitle | string   | 否   | 原文标题                                                     |
| originalLink  | string   | 否   | 原文链接                                                     |
| modifyDate    | string   | 是   | 更新时间，需要符合 ISO-8601 格式                             |
| publishDate   | string   | 是   | 发布时间，需要符合 ISO-8601 格式                             |

Http状态码说明：

| Http Code | Description              |
| --------- | ------------------------ |
| 202       | 完成调用 - PATCH成功返回 |
| 202       | 资源已创建 - PUT成功返回 |
| 204       | 请求未操作               |
| 401       | 鉴权错误                 |
| 500       | 请求无法完成，出现错误   |

返回数据示例：

```
{
	"taskCode": "",
	"code": 0
}
```


返回参数说明：

| 名称     | 类型   | 必显   | 说明           |
| :------- | :----- | :----- | :------------- |
| taskCode | String | 是     | 后台任务查询码 |
| code     | number | 返回码 |                |

code 返回码说明：

| 返回码 | 说明                     | 备注 |
| :----- | :----------------------- | ---- |
| 0      | 操作成功                 |      |
| 500    | 内部错误                 |      |
| 2      | 单次执行不能大于10条记录 |      |



##### 新闻-撤销-接口

###### 接口说明

该接口用于渠道-界面新闻对新闻项数据进行撤销下架操作，请谨慎使用。

操作接口将界面同步的数据，在内容中心里进行下架操作，直接影响终端显示，应使用在紧急新闻撤销时。

调用接口时调用方需要进行审计日志记录。以匹配我方审计日志进行操作复盘及审计工作。

------

###### 接口信息

接口路径：**/{version}/news/jiemian**

接口方法

| Http Method | Action   | Memo |
| ----------- | -------- | ---- |
| DELETE      | 下架撤销 |      |

请求示例路径

```
DELETE /v1/news/jiemian?id=2&operator=tester&operationDate=2008-09-03T20:56:35.450686
```

请求参数示例:

| 名称          | 类型   | 必须 | 说明                             |
| ------------- | ------ | ---- | -------------------------------- |
| id            | string | 是   | 新闻唯一标识                     |
| operator      | string | 是   | 操作人员名称                     |
| operationDate | string | 是   | 撤销时间，需要符合 ISO-8601 格式 |

Http状态码说明：

| Http Code | Description            |
| --------- | ---------------------- |
| 200       | 完成调用               |
| 204       | 请求未操作             |
| 401       | 鉴权错误               |
| 500       | 请求无法完成，出现错误 |

返回数据示例：

```
{
	"code": 0
}
```


返回参数说明：

| 名称   | 类型   | 必显 | 说明   |
| :----- | :----- | :--- | :----- |
| `code` | number | 是   | 返回码 |

code 返回码说明：

| 返回码 | 说明         | 备注 |
| :----- | :----------- | ---- |
| 0      | 操作成功     |      |
| 1      | 参数不完整   |      |
| 12     | 日期格式错误 |      |
| 500    | 内部错误     |      |



##### 新闻-执行记录-接口

###### 接口说明

根据"新闻-新增/更新-接口"返回的执行记录编码(taskCode)查询调用结果执行情况

------

###### 接口信息

接口路径：**/{version}/news/jiemian/[taskCode]**

接口方法：

| Http Method | Action       | Memo |
| ----------- | ------------ | ---- |
| GET         | 任务执行记录 |      |

请求示例路径

```
GET /v1/news/jiemian/9b28dc04b92911ea954902fcdc4e7412
```

请求参数示例:

| 名称     | 类型   | 必须 | 说明         |
| -------- | ------ | ---- | ------------ |
| taskCode | string | 是   | 执行记录编码 |

Http状态码说明：

| Http Code | Description            |
| --------- | ---------------------- |
| 200       | 完成调用               |
| 204       | 请求未操作             |
| 401       | 鉴权错误               |
| 500       | 请求无法完成，出现错误 |

返回数据示例：

```
[
	{
		"taskCode":"9b28dc04b92911ea954902fcdc4e7412",
		"taskItemCode":"e2d58bb0b92911ea9afe02fcdc4e7412",
		"operator":"tester",
		"operationDate":"2008-09-03T20:56:35.450686",
		"input":"{id:'13387ec0b92a11ea87d802fcdc4e7412'}",
		"output":"{rst:'successed'}",
		"status":"success",
		"operationType":"unpublish"
	},
	...
]
```


返回参数说明：

| 名称            | 类型   | 必显 | 说明                                     |
| :-------------- | :----- | :--- | :--------------------------------------- |
| `taskCode`      | String | 是   | 执行记录编码                             |
| `taskItemCode`  | String | 是   | 执行记录项编码                           |
| `operator`      | String | 是   | 操作人                                   |
| `operationDate` | String | 是   | 操作时间                                 |
| `input`         | String | 是   | 输入值(包含请求入参)                     |
| `output`        | String | 是   | 输出值(包含错误详细和第三方接口调用信息) |
| `status`        | String | 是   | 状态(successed/failed)                   |
| `operationType` | String | 是   | 状态(create/update/unpublish)            |

code 返回码说明：

| 返回码 | 说明       | 备注 |
| :----- | :--------- | ---- |
| 0      | 操作成功   |      |
| 1      | 参数不完整 |      |
| 500    | 内部错误   |      |

