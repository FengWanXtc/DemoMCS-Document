# 3.2 Mediadevice——mediadevicelib

## 3.2.1 get_md_audio_in

- 函数声明:

```
  def get_md_audio_in(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备上 **音频输入** 子信息系统，对应 MA 文档 **<font color=#00CD00>GET</font>** **`/mediadevice/audio/in`** 接口

- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |                  备注                   |
  |:----------------:|:------:|:-------------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   | 参考响应体描述[Response](/api/response.html) |


- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1001_device_get_audio_in.py

  ![docker_image](picture/md_audio_in.png)

## 3.2.2 get_md_audio_out
- 函数声明:
```
  def get_md_audio_out(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备上 **音频输出** 子信息系统，对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/audio/out`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |


- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1002_device_get_audio_out.py

  ![docker_image](picture/md_audio_out.png)
  
## 3.2.3 get_md_video_in
- 函数声明:
```
  def get_md_video_in(token='', ip=HOST_IP)
```


- 描述： 用于获取边缘设备上 **视频输入** 子信息系统，对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/video/in`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1003_device_get_video_in.py

  ![docker_image](picture/md_video_in.png)
  
## 3.2.4 get_md_video_out
- 函数声明:
```
  def get_md_video_out(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备上 **视频输出** 子信息系统，对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/video/out`** 接口

- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1004_device_get_video_out.py

  ![docker_image](picture/md_video_out.png)

## 3.2.5 get_md_audio_in_capability
- 函数声明:
```
  def get_md_audio_in_capability(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备 **音频采集** 的能力列表。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/audio/in/capability`** 接口

- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1005_device_get_audio_in_capability.py

  ![docker_image](picture/md_audio_in_cap.png)

## 3.2.6 get_md_audio_out_capability

- 函数声明:
```
  def get_md_audio_out_capability(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备 **音频播放** 的能力列表。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/audio/out/capability`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1006_device_get_audio_out_capability.py

  ![docker_image](picture/md_audio_out_cap.png)

## 3.2.7 get_md_video_in_capability

- 函数声明:
```
  def get_md_video_in_capability(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备 **视频采集** 的能力列表。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/video/in/capability`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1007_device_get_video_in_capability.py

  ![docker_image](picture/md_video_in_cap.png)

## 3.2.8 get_md_video_out_capability
- 函数声明:
```
  def get_md_video_out_capability(token='', ip=HOST_IP)
```
- 描述： 用于获取边缘设备 **视频输出** 的能力列表。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/video/out/capability`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |


- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1008_device_get_video_out_capability.py

  ![docker_image](picture/md_video_out_cap.png)


## 3.2.9 get_md_video_out_background
- 函数声明:
```
  def get_md_video_out_background(token='', ip=HOST_IP)
```
- 描述： 获取边缘设备 **视频输出** 子系统的永久背景设置。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/video/out/background`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |


- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1009_device_get_video_out_background.py

  ![docker_image](picture/md_video_out_bg.png)

## 3.2.10 get_md_list
- 函数声明:
```
  def get_md_list(token='', ip=HOST_IP)
```

- 描述： 用于获取边缘设备上所有 **音、视频输入** 子系统信息。对应 MA 文档 **<font color=#00CD00>GET
</font>** **`/mediadevice/list`** 接口。该接口调用相当于一次调用 **<font color=#00CD00>GET
</font>** **`mediadevice/audio/in`**,**<font color=#00CD00>GET</font>** **`mediadevice/audio/out`**,**<font color=#00CD00>
GET</font>** **`mediadevice/video/in`**,**<font color=#00CD00>GET</font>** **`mediadevice/video/out`** 四个接口。

- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1010_device_get_md_list.py

  ![docker_image](picture/md_list.png)


## 3.2.11 get_audio_in_configuration
- 函数声明:
```
  def get_audio_in_configuration(token='', ip=HOST_IP)
```
- 描述： 获取边缘设备 **音频输入** 子系统的永久配置信息。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/audio/in/configuration`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1011_device_get_audio_in_cfg.py

  ![docker_image](picture/md_audio_in_cfg.png)

## 3.2.12 get_audio_out_configuration
- 函数声明:

```
  def get_audio_out_configuration(token='', ip=HOST_IP)
```

- 描述： 获取边缘设备 **音频输出** 子系统的永久配置信息。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/audio/out/configuration`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1012_device_get_audio_out_cfg.py

  ![docker_image](picture/md_audio_out_cfg.png)

## 3.2.13 get_md_director_strategy
- 函数声明:
```
  def get_md_director_strategy(token='', ip=HOST_IP)
```
- 描述： 获取边缘设备当前存储的导播策略信息。对应 MA 文档 **<font color=#00CD00>
GET</font>** **`/mediadevice/director-strategy`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |         备注         |
  |:------------:| :------: | :----------------: | :--------------------: |
  | token    |    string    |      鉴权码      | 缺省为空，目前未使能 |
  | ip       |    string    | 发送请求的小站IP |                      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |

- DemoMCS 演示效果

  脚本：DemoMCS\01_Basic_Tests\MA_API_Basic_Tests\1013_device_get_director_strategy.py

  ![docker_image](picture/md_ai_strategy_1.png)
  ![docker_image](picture/md_ai_strategy_2.png)