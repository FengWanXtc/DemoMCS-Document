# 3.5 Response结构体说明

大部分接口函数返回值为特殊数据类型 **`Response`**,使用返回值的不同处理方式，可以获取相应的结果。

<br>

|          内容          |  类型   | 说明                                                                                                               | 
|:--------------------:|:-----:|:-----------------------------------------------------------------------------------------------------------------|
|   response.json()    | dict	 | Requests中内置的JSON解码器,返回的是一个字典类<br/>型数据，就是Spec中的Body内容，可以用 **键值对** 方<br/>式获取body中的字段,比如 response.json()[“Message”] | 
| response.status_code |  int  | 响应状态码，200为正常响应，此外有404、500等等                                                                                      |
|   response.headers   | dict	 | 以字典类型对象存储服务器响应头，但是这个字典比较<br/>特殊，字典键不区分大小写，若键不存在则返回None                                                           |
|    response.text     |  str  | 字符串方式的响应体，会自动根据响应头部的字符编码<br/>进行解码 ,内容和response.json()一样                                                          |         
|   response.content   | bytes | 字节方式的响应体，会自动解码gzip和deflate压缩                                                                                     |
|     response.url     |  str  | 获取下发的url                                                                                                         |
 |   response.cookies   | 特殊类型  | 获取cookie                                                                                                         | 
 |     response.raw     | 特殊类型  | 返回原始响应体                                                                                                          |