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

  ```
  Get Mediadevice audio in success! No error found!
  
  +---------------------------+-----------+----------------------------+---------+
  | DeviceName                | DeviceId  | AliasName                  | Default |
  +---------------------------+-----------+----------------------------+---------+
  | BuiltIn USB Audio Capture | 0103-0200 | BuiltInUSBAudioCapture_333 | True    |
  +---------------------------+-----------+----------------------------+---------+ 
  
  < BuiltIn USB Audio Capture > Has SubDevices. List As Follow: 
  +-----------+------------------------------------+-------------------------------------+
  | Id        | Name                               | Alias                               |
  +-----------+------------------------------------+-------------------------------------+
  | 0120-0200 | Mobile Mic Audio Capture - BuiltIn | MobileMicAudioCapture-BuiltIn_19342 |
  | 0111-0200 | Mic2 Audio Capture - BuiltIn       | Mic2AudioCapture-BuiltIn_41454      |
  +-----------+------------------------------------+-------------------------------------+
  ```

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

  ```
  Get Mediadevice audio out success! No error found!

  +----------------------------+-----------+-------------------------------+---------+
  | DeviceName                 | DeviceId  | AliasName                     | Default |
  +----------------------------+-----------+-------------------------------+---------+
  | HDMI Audio Playback        | 0200-0007 | HDMIAudioPlayback_1988        | False   |
  | BuiltIn USB Audio Playback | 0203-0200 | BuiltInUSBAudioPlayback_53583 | True    |
  +----------------------------+-----------+-------------------------------+---------+ 
  
  < BuiltIn USB Audio Playback > Has SubDevices. List As Follow: 
  +-----------+-----------------------------------------+------------------------------------------+
  | Id        | Name                                    | Alias                                    |
  +-----------+-----------------------------------------+------------------------------------------+
  | 0210-0200 | Speaker Audio Playback - BuiltIn        | SpeakerAudioPlayback-BuiltIn_57039       |
  | 0220-0200 | Mobile Speaker Audio Playback - BuiltIn | MobileSpeakerAudioPlayback-BuiltIn_61039 |
  +-----------+-----------------------------------------+------------------------------------------+
  ```
  
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

  ```
  Get Mediadevice video in success! No error found!
  
  +------------+-----------+--------------+---------+----------------------+
  | DeviceName | DeviceId  | AliasName    | Default | Algorithms           |
  +------------+-----------+--------------+---------+----------------------+
  | HDMI_CAM_1 | 0400-0000 | Teacher_HDMI | True    | ['teacher tracking'] |
  | HDMI_PC_IN | 0400-0002 | HDMI_IN      | False   | ['ppt tracking']     |
  | IPC_CAM_1  | 0403-0001 | Student_IPC  | False   | ['student tracking'] |
  +------------+-----------+--------------+---------+----------------------+
  ```
  
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

  ```
  Get Mediadevice video out success! No error found!
  
  +--------------+-----------+--------------------+---------+
  | DeviceName   | DeviceId  | AliasName          | Default |
  +--------------+-----------+--------------------+---------+
  | HDMI-Monitor | 0800-0000 | HDMI-Monitor_36646 | True    |
  +--------------+-----------+--------------------+---------+
  ```

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

  ```
  Get Mediadevice audio in capability success! No error found!
  
  +---------------+---------------+------------------------------------+---------+-----------------+------------------------+
  |    DeviceId   | ChannelsRange |          SampleRateRange           | Formats |     Layouts     |         Codecs         |
  +---------------+---------------+------------------------------------+---------+-----------------+------------------------+
  |   0103-0200   |     [1, 2]    | [8000, 16000, 32000, 44100, 48000] |  S16LE  | ['Interleaved'] | ['WAV', 'AAC', 'OPUS'] |
  | CurrentConfig |       2       |               44100                |  S16LE  |   Interleaved   |                        |
  +---------------+---------------+------------------------------------+---------+-----------------+------------------------+
  ```

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

  ```
  Get Mediadevice audio out capability success! No error found!
  
  +-----------+---------------+----------+--------+
  | DeviceId  | ChannelsRange | Formats  | Codecs |
  +-----------+---------------+----------+--------+
  | 0200-0007 | [1, 2]        | S16LE    | []     |
  |           |               | S16BE    |        |
  |           |               | F32LE    |        |
  |           |               | F32BE    |        |
  |           |               | S32LE    |        |
  |           |               | S32BE    |        |
  |           |               | S24LE    |        |
  |           |               | S24BE    |        |
  |           |               | S24_32LE |        |
  |           |               | S24_32BE |        |
  |           |               | U8       |        |
  | 0203-0200 | [1, 2]        | S16LE    | []     |
  +-----------+---------------+----------+--------+
  ```

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

  ```
  Get Mediadevice video in capability success! No error found!
  
  +-------------------------+
  |          Codecs         |
  +-------------------------+
  | ['H264', 'H265', 'VP9'] |
  +-------------------------+
  +-----------+-----------+----------+---------------+---------+--------+-------------------------+
  |  DeviceId | FormatSet | [ Format | ResolutionSet | [ Width | Height |      FrameRate ] ]      |
  +-----------+-----------+----------+---------------+---------+--------+-------------------------+
  | 0400-0000 |           |   UYVY   |               |   3840  |  2160  |           [30]          |
  |           |           |          |               |   1920  |  1080  |       [60, 50, 30]      |
  | 0400-0001 |           |   UYVY   |               |   3840  |  2160  |           [30]          |
  |           |           |          |               |   1920  |  1080  |       [60, 50, 30]      |
  | 0400-0002 |           |   UYVY   |               |   3840  |  2160  |           [30]          |
  |           |           |          |               |   1920  |  1080  |       [60, 50, 30]      |
  | 0401-2310 |           |   YUY2   |               |   640   |  480   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   320   |  180   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   480   |  270   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   640   |  360   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   800   |  448   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   800   |  600   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1024  |  576   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1280  |  720   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1920  |  1080  | [30, 25, 20, 15, 10, 5] |
  |           |           |   NV12   |               |   640   |  480   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   320   |  180   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   480   |  270   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   640   |  360   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   800   |  448   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   800   |  600   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1024  |  576   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1280  |  720   | [30, 25, 20, 15, 10, 5] |
  |           |           |          |               |   1920  |  1080  | [30, 25, 20, 15, 10, 5] |
  | 0403-0001 |           |   H264   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  |           |           |   H265   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  | 0403-0002 |           |   H264   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  |           |           |   H265   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  | 0403-0003 |           |   H264   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  |           |           |   H265   |               |   1920  |  1080  |       [25, 30, 60]      |
  |           |           |          |               |   3840  |  2160  |       [25, 30, 60]      |
  +-----------+-----------+----------+---------------+---------+--------+-------------------------+
  ```

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

  ```
  Get Mediadevice video out capability success!No error found!
  
  +-----------+-------+--------+
  | DeviceId  | Width | Height |
  +-----------+-------+--------+
  | 0800-0000 | 2560  | 1440   |
  +-----------+-------+--------+
  ```

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

  ```
  Get video out background success! No error found!
  
  +-----------+------------+
  | DeviceId  | Background |
  +-----------+------------+
  | 0800-0000 | null       |
  +-----------+------------+
  ```

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
  
  ```
  Get Device List success!No error found!
  
  Audio In Devices As Follow.
  +---------------------------+-----------+------------------------------+---------+
  | DeviceName                | DeviceId  | AliasName                    | Default |
  +---------------------------+-----------+------------------------------+---------+
  | BuiltIn USB Audio Capture | 0103-0200 | BuiltInUSBAudioCapture_33376 | True    |
  +---------------------------+-----------+------------------------------+---------+ 
  
  < BuiltIn USB Audio Capture > Has SubDevices. List As Follow: 
  +-----------+------------------------------------+-------------------------------------+
  | Id        | Name                               | Alias                               |
  +-----------+------------------------------------+-------------------------------------+
  | 0111-0200 | Mic2 Audio Capture - BuiltIn       | Mic2AudioCapture-BuiltIn_20480      |
  | 0120-0200 | Mobile Mic Audio Capture - BuiltIn | MobileMicAudioCapture-BuiltIn_26976 |
  +-----------+------------------------------------+-------------------------------------+ 
  
  ******************************************* Split Line **********************************************
  
  Audio Out Devices As Follow.
  +----------------------------+-----------+-------------------------------+---------+
  | DeviceName                 | DeviceId  | AliasName                     | Default |
  +----------------------------+-----------+-------------------------------+---------+
  | BuiltIn USB Audio Playback | 0203-0200 | BuiltInUSBAudioPlayback_33088 | True    |
  | HDMI Audio Playback        | 0200-0007 | HDMIAudioPlayback_13248       | False   |
  +----------------------------+-----------+-------------------------------+---------+ 
  
  < BuiltIn USB Audio Playback > Has SubDevices. List As Follow: 
  +-----------+-----------------------------------------+------------------------------------------+
  | Id        | Name                                    | Alias                                    |
  +-----------+-----------------------------------------+------------------------------------------+
  | 0210-0200 | Speaker Audio Playback - BuiltIn        | SpeakerAudioPlayback-BuiltIn_49088       |
  | 0220-0200 | Mobile Speaker Audio Playback - BuiltIn | MobileSpeakerAudioPlayback-BuiltIn_53632 |
  +-----------+-----------------------------------------+------------------------------------------+ 
  
  ******************************************* Split Line **********************************************
  
  Video In Devices As Follow.
  +------------+-----------+-------------+---------+----------------------+
  | DeviceName | DeviceId  | AliasName   | Default | Algorithms           |
  +------------+-----------+-------------+---------+----------------------+
  | IPC_CAM_1  | 0403-0001 | Student_IPC | False   | ['student tracking'] |
  | IPC_CAM_2  | 0403-0002 | Teacher_IPC | False   | ['teacher tracking'] |
  +------------+-----------+-------------+---------+----------------------+ 
  
  ******************************************* Split Line **********************************************
  
  Video Out Devices As Follow.
  +--------------+-----------+--------------------+---------+
  | DeviceName   | DeviceId  | AliasName          | Default |
  +--------------+-----------+--------------------+---------+
  | HDMI-Monitor | 0800-0000 | HDMI-Monitor_25664 | True    |
  +--------------+-----------+--------------------+---------+
  ```

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

  ```
  Get audio in configuration success! No error found!
  
  +-----------+--------+-------+--------------------+
  | DeviceId  | Volume | Mute  | LocalAmplification |
  +-----------+--------+-------+--------------------+
  | 0103-0200 |   85   | False |       False        |
  +-----------+--------+-------+--------------------+ 
  
  DeviceId < 0103-0200 > Has SubDevices. List As Follow: 
  +-----------+--------+-------+
  | Id        | Volume | Mute  |
  +-----------+--------+-------+
  | 0120-0200 |   70   | False |
  | 0111-0200 |   70   | False |
  +-----------+--------+-------+
  ```

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

  ```
  Get audio out configuration success! No error found!
  
  +-----------+--------+-------+
  | DeviceId  | Volume | Mute  |
  +-----------+--------+-------+
  | 0200-0007 |   70   | False |
  | 0203-0200 |   85   | False |
  +-----------+--------+-------+ 
  
  DeviceId < 0203-0200 > Has SubDevices. List As Follow: 
  +-----------+--------+-------+
  | Id        | Volume | Mute  |
  +-----------+--------+-------+
  | 0210-0200 |   70   | False |
  | 0220-0200 |   70   | False |
  +-----------+--------+-------+
  ```

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

  ```
  Get director strategy success! 
  
  [Scenario] <Teacher_With_Blackboard>  Template is <TEMPLATE_ONE_FRAME>. Strategy As follows: 
  
  +----------------+----------+---------------------+-------+------+---------+
  |     State      | Priority |     VideoSource     | Delay | Hold | Timeout |
  +----------------+----------+---------------------+-------+------+---------+
  |    Stand_N     |    1     |       Student       |   0   |  6   |   180   |
  |    Stand_1     |    2     |   Student_Tracking  |   0   |  6   |   180   |
  | PptMouseAction |    3     |  Computer_Tracking  |   0   |  15  |   3600  |
  |      Many      |    4     |   Teacher_Tracking  |   0   |  6   |   3600  |
  |     Write      |    6     | Blackboard_Tracking |   0   |  6   |   3600  |
  |      Move      |    7     |   Teacher_Tracking  |   0   |  6   |   3600  |
  |     Stand      |    8     |   Teacher_Tracking  |   0   |  6   |   3600  |
  |      Out       |    9     |       Teacher       |   0   |  6   |   3600  |
  |      Sit       |    10    |       Student       |   0   |  6   |   3600  |
  |   NoTeacher    |    11    |       Teacher       |   0   |  6   |   3600  |
  |     Others     |    12    |       Teacher       |   0   |  6   |   3600  |
  +----------------+----------+---------------------+-------+------+---------+ 
  
  **********************************************************************************************
  
  [Scenario] <Teacher_Without_Blackboard>  Template is <TEMPLATE_ONE_FRAME>. Strategy As follows: 
  
  +----------------+----------+-------------------+-------+------+---------+
  |     State      | Priority |    VideoSource    | Delay | Hold | Timeout |
  +----------------+----------+-------------------+-------+------+---------+
  |    Stand_N     |    1     |      Student      |   0   |  6   |   180   |
  |    Stand_1     |    2     |  Student_Tracking |   0   |  6   |   180   |
  | PptMouseAction |    3     | Computer_Tracking |   0   |  15  |   3600  |
  |      Many      |    4     |  Teacher_Tracking |   0   |  6   |   3600  |
  |     Write      |    6     |  Teacher_Tracking |   0   |  6   |   3600  |
  |      Move      |    7     |  Teacher_Tracking |   0   |  6   |   3600  |
  |     Stand      |    8     |  Teacher_Tracking |   0   |  6   |   3600  |
  |      Out       |    9     |      Teacher      |   0   |  6   |   3600  |
  |      Sit       |    10    |      Student      |   0   |  6   |   3600  |
  |   NoTeacher    |    11    |      Teacher      |   0   |  6   |   3600  |
  |     Others     |    12    |      Teacher      |   0   |  6   |   3600  |
  +----------------+----------+-------------------+-------+------+---------+ 
  
  **********************************************************************************************
  
  [Scenario] <Student_With_Blackboard>  Template is <TEMPLATE_ONE_FRAME>. Strategy As follows: 
  
  +----------------+----------+---------------------+-------+------+---------+
  |     State      | Priority |     VideoSource     | Delay | Hold | Timeout |
  +----------------+----------+---------------------+-------+------+---------+
  |    Stand_N     |    1     |       Student       |   0   |  6   |   180   |
  |    Stand_1     |    2     |   Student_Tracking  |   0   |  6   |   180   |
  | PptMouseAction |    3     |  Computer_Tracking  |   0   |  15  |   3600  |
  |     Write      |    5     | Blackboard_Tracking |   0   |  6   |   3600  |
  |      Move      |    6     |   Teacher_Tracking  |   0   |  6   |   3600  |
  |     Stand      |    7     |   Teacher_Tracking  |   0   |  6   |   3600  |
  |      Many      |    8     |       Teacher       |   0   |  6   |   3600  |
  |      Sit       |    9     |       Student       |   0   |  6   |   3600  |
  |      Out       |    10    |       Teacher       |   0   |  6   |   3600  |
  |   NoTeacher    |    11    |       Teacher       |   0   |  6   |   3600  |
  |     Others     |    12    |       Teacher       |   0   |  6   |   3600  |
  +----------------+----------+---------------------+-------+------+---------+ 
  
  **********************************************************************************************
  
  [Scenario] <Student_Without_Blackboard>  Template is <TEMPLATE_ONE_FRAME>. Strategy As follows: 
  
  +----------------+----------+-------------------+-------+------+---------+
  |     State      | Priority |    VideoSource    | Delay | Hold | Timeout |
  +----------------+----------+-------------------+-------+------+---------+
  |    Stand_N     |    1     |      Student      |   0   |  6   |   180   |
  |    Stand_1     |    2     |  Student_Tracking |   0   |  6   |   180   |
  | PptMouseAction |    3     | Computer_Tracking |   0   |  15  |   3600  |
  |     Write      |    5     |  Teacher_Tracking |   0   |  6   |   3600  |
  |      Move      |    6     |  Teacher_Tracking |   0   |  6   |   3600  |
  |     Stand      |    7     |  Teacher_Tracking |   0   |  6   |   3600  |
  |      Many      |    8     |      Teacher      |   0   |  6   |   3600  |
  |      Sit       |    9     |      Student      |   0   |  6   |   3600  |
  |      Out       |    10    |      Teacher      |   0   |  6   |   3600  |
  |   NoTeacher    |    11    |      Teacher      |   0   |  6   |   3600  |
  |     Others     |    12    |      Teacher      |   0   |  6   |   3600  |
  +----------------+----------+-------------------+-------+------+---------+ 
  
  **********************************************************************************************
  ```

