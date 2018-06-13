## 地图回调地址
##### http://101.231.198.170:9090/qyrz/mapCallBack
请求参数

字段|类型|描述
---|:--:|---:
id|字符串|企业唯一id
status|字符串|处理状态(2处理中，3已处理，4不处理)
remark|字符串|备注

返回

字段|类型|描述
---|:--:|---:
ret|字符串|返回码； 0表示成功，非0表示出错
msg|字符串|返回信息；ret非0时表示出错时错误原因


## 漏话查询
##### http://hebei.callkr.cn/WeiXinServer/page_bgMissCall.action
#### 请求方式Get

#### 请求参数

字段名称|字段类型|字段描述|示例数据
---|:--:|---:|---:
timestamp|字符串|时间戳|1493468759
ownernumber|字符串|电话号码|17602100074
type|字符串|业务类型|1
signature|字符串|签名信息(见鉴权方式)|B250148B284956EC5218D4B0503E7F8A
#### 接口返回html页面

## 鉴权方式

字段名称|字段类型|字段描述|示例数据
---|:--:|---:|---:
token|字符串|接口调用标识，有接口提供方下发|miscall

#### 签名规范：
- 根据参数名称将所有请求参数的值按照字典升序排序
- 字符串拼接成一个字符串进行sha1加密
- 获得加密后的字符串signature，标识该请求来源，接口每次请求时将签名作为参数传递

## 示例
###### 请求参数
``` 
timestamp=1493468759
ownernumber=17602100074
token=miscall
type=1
```
###### 按字典排序后顺序为
``` 
1
1493468759
17602100074
miscall
```
###### 拼接后的字符串为
``` 
1149346875917602100074miscall
```
###### sha1后的字符串为
``` 
543d6bc98f064778f0439d2d14b1e7439eb0188b
```
###### 则漏话查询的url为
``` 
http://hebei.callkr.cn/WeiXinServer/page_bgMissCall.action?timestamp=1493468759&ownernumber=17602100074&type=1&signature=543d6bc98f064778f0439d2d14b1e7439eb0188b
```
