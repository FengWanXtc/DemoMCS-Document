# 2.1. 各个Spec简介
- VideoSpec/AudioSpec: 外设收入的Spec，作为原始的音/视频源
- VideoAiSpec/AudioAiSpec(未应用): 经过AI处理的新的视频源,教师特写，学生特写
- VideoDirectorSpecS: 导播路视频流，结合了各路视频流合成的一路
- AudioComposeSpecs：将多路音频合成一路的音频流
- VideoComposeSpecs:将多路视频合成一路的视频流
- VideoTransformSpecs:将原始视频六进行翻转，放缩，修改帧率等操作形成的新视频流
- PlaySpecs ：用于音频播放输出的Specs
- AudioCodecSpecs/VideoCodecSpecs: 音视频编码的Specs,经过编码后可以进行录制，推拉流等操作
- RenderSpecs：用于在显示器屏幕上回显视频画面的Specs
- ServerSpecs: 用于推送本地视频流使用的Specs，需要经过编码才可以
- CodecStreamSpecs：用于拉取远端视频流使用的Specs，远端视频拉取下来后会经过解码流程，
                   所以想录制远端需要用CodecSpecs进行编码


# 2.2 基础回显
```json
   {
     "Name": "Two_Camera_Render",
     "Type": "MCS",
     "Description": "Two Cameras Render ",
     "Version": "0.3",
     "VideoSpecs": [
         {
             "Name": "Teacher",
             "DeviceId": "0400-0000",
             "Width": 1920,
             "Height": 1080,
             "FrameRate": 30
         },
         {
             "Name": "Student",
             "DeviceId": "0403-0001",
             "Width": 1920,
             "Height": 1080,
             "FrameRate": 30
         }
     ],
     "RenderSpecs": [
         {
             "Name": "Render_test",
             "DeviceId": "0800-0000",
             "CompositionSpec": [
                 {
                     "Geometry": [0, 0, 960, 540],
                     "SourceName": "Teacher"
                 },
                 {
                     "Geometry": [960, 0, 960, 540],
                     "SourceName": "Student"
                 }
             ]
         }
     ]
   }
```

#### 画面效果


#### 注
- 帧率锁定为30帧，否则返回的响应体会有错误提示
- 不同类型摄像头DeviceId有区别，可以用 /mediadevice/video/in查看
- VideoSpecs的 Format 字段推荐不写，不同类型摄像头根据MIOS会补全

# 2.3. 本地回声
```json
   {
     "Name": "Local echo",
     "Type": "MCS",
     "Description": "Audio Local echo",
     "Version": "0.3",
    "AudioSpecs": [
        {
            "Name": "AudioInDefault",
            "DeviceId": "",
            "SampleRate": 44100,
            "Channels": 2
        },
        {
            "Name": "AudioInPC",
            "DeviceId": "",
            "SampleRate": 48000,
            "Channels": 2,
            "Format": "S16LE",
            "Layout": "Interleaved"
        }
    ],
    "PlaySpecs": [
        {
            "Name": "LocalPlaySpec",
            "Sources": [
                {
                    "SourceName": "AudioInDefault",
                    "Volume": 70
                }
            ]
        }
    ]
   }
```

#### 注
- 采样率我们推荐 16000，44100，48000
- 


# 2.4. 带算法的回显

```json
   {
  "Name": "Video Ai Render",
  "Type": "MCS",
  "Description": "Two Cameras Render ",
  "Version": "0.3",
  "VideoSpecs": [
    {
      "Name": "Teacher",
      "DeviceId": "0400-0000",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Student",
      "DeviceId": "0403-0001",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    }
  ],
  "VideoAiSpecs": [
    {
      "Name": "Teacher_Ai",
      "SourceName": "Teacher",
      "Algorithm": "Teacher Tracking",
      "ProcessRate": 10,
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Student_Ai",
      "SourceName": "Student",
      "Algorithm": "Student Tracking",
      "ProcessRate": 30,
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    }
  ],
  "RenderSpecs": [
    {
      "Name": "Render_test",
      "DeviceId": "0800-0000",
      "Background": "NA",
      "CompositionSpec": [
        {
          "Geometry": [
            0,
            0,
            960,
            540
          ],
          "SourceName": "Teacher"
        },
        {
          "Geometry": [
            960,
            0,
            960,
            540
          ],
          "SourceName": "Student"
        },
        {
          "Geometry": [
            0,
            540,
            960,
            540
          ],
          "SourceName": "Teacher_Ai"
        },
        {
          "Geometry": [
            960,
            540,
            960,
            540
          ],
          "SourceName": "Student_Ai"
        }
      ]
    }
  ]
}
```

# 2.5 音视频录制
```json
{
    "Name": "Basic_MCS",
    "Type": "MCS",
    "Description": "The four-channel AI scenario Basic MCS",
    "Version": "0.3",
    "AudioSpecs": [
        {
            "Name": "AudioInDefault",
            "DeviceId" : "",
            "SampleRate": 48000,
            "Channels": 2
        }
    ],
    "AudioCodecSpecs": [
        {
            "Name": "AudioInDefault_aac_Codec",
            "SourceName": "AudioInDefault",
            "Codec": "aac"
        }
    ],
    "VideoSpecs": [
        {
            "Name": "Teacher",
            "DeviceId": "0400-0000",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Student",
            "DeviceId": "0400-0001",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        }
    ],
    "VideoCodecSpecs": [
        {
            "Name": "Teacher_h264_Codec",
            "SourceName": "Teacher",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "4mbps",
            "iFrameInterval": 30,
            "idrInterval": 30
        }
    ],
    "RecordSpecs": [
        {
            "Name": "Director_Record",
            "AudioCodecName": "AudioInDefault_aac_Codec",
            "VideoCodecName": "Teacher_h264_Codec ",
            "Format": "mp4",
            "Path": "S4E7_Basic_yyyy-mm-dd-hh-mm-ss.mp4"
        }
    ]
}

```
#### 注
- 经过编码的流（VideoCodecSpecs，AudioCodecSpecs）只能用于录制或者推拉流，无法回显

# 2.6 Compose音视频流
## 音频

```json
{
  "Name": "AudioComposeSpecTest",
  "Type": "MCS",
  "Description": "MCS Template",
  "Version": "0.3",
  "AudioSpecs": [
    {
      "Name": "MIC",
      "DeviceId": "",
      "SampleRate": 44100,
      "Channels": 2
    },
    {
      "Name": "PC",
      "DeviceId": "",
      "SampleRate": 44100,
      "Channels": 2,
      "Format": "S16LE",
      "Layout": "Interleaved"
    }
  ],
  "AudioComposeSpecs": [
    {
      "Name": "CompositorAudio",
      "SampleRate": 44100,
      "MixerSpec": [
        {
          "SourceName": "MIC",
          "Volume": 100
        },
        {
          "SourceName": "PC",
          "Volume": 100
        }
      ]
    }
  ],
  "PlaySpecs": [
    {
      "Name": "Audio_Play",
      "DeviceId": "",
      "Sources": [
        {
          "SourceName": "CompositorAudio",
          "Volume": 100
        }
      ]
    }
  ]
}
```
#### 注
- HDMI_IN_RX口通过HDMI接上PC，才会有相应的外设

## 视频
```json
{
    "Name": "VideoComposeSpecTest",
    "Type": "MCS",
    "Description": "The four-channel AI scenario Basic MCS",
    "Version": "0.3",
    "VideoSpecs": [
        {
            "Name": "Teacher",
            "DeviceId": "0400-0000",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Student",
            "DeviceId": "0403-0001",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Computer",
            "DeviceId": "0400-0002",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        }, 
       {
            "Name": "Blackboard",
            "DeviceId": "0403-0002",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        }
    ],
    "VideoComposeSpecs": [
        {
            "Name": "Compositor",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30,
            "CompositionSpec": [
                {
                    "Geometry": [
                        0,
                        0,
                        960,
                        540
                    ],
                    "ZOrder": 1,
                    "SourceName": "Teacher"
                },
                {
                    "Geometry": [
                        960,
                        0,
                        960,
                        540
                    ],
                    "ZOrder": 1,
                    "SourceName": "Student"
                },
                {
                    "Geometry": [
                        0,
                        540,
                        960,
                        540
                    ],
                    "ZOrder": 1,
                    "SourceName": "Computer"
                },
                {
                    "Geometry": [
                        960,
                        540,
                        960,
                        540
                    ],
                    "ZOrder": 1,
                    "SourceName": "Blackboard"
                }
            ]
        }
    ],
    "RenderSpecs": [
        {
            "Name": "Render_test",
            "DeviceId": "0800-0000",
            "CompositionSpec": [
                {
                    "Geometry": [
                        0,
                        0,
                        960,
                        540
                    ],
                    "SourceName": "Compositor"
                },
                {
                    "Geometry": [
                        960,
                        0,
                        960,
                        540
                    ],
                    "SourceName": "Teacher"
                },
                {
                    "Geometry": [
                        0,
                        540,
                        960,
                        540
                    ],
                    "SourceName": "Student"
                },
                {
                    "Geometry": [
                        960,
                        540,
                        960,
                        540
                    ],
                    "SourceName": "Computer"
                }
            ]
        }
    ]
}
```

## 画面效果

# 2.7 推拉流

## 拉流端
```json
{
  "Name": "Basic_MCS",
  "Type": "MCS",
  "Description": "The four-channel AI scenario Basic MCS",
  "Version": "0.3",
  "AudioSpecs": [
    {
      "Name": "AudioInDefault",
      "SampleRate": 48000,
      "Channels": 2
    }
  ],
  "AudioCodecSpecs": [
    {
      "Name": "AudioInDefault_aac_Codec",
      "SourceName": "AudioInDefault",
      "Codec": "aac"
    }
  ],
  "VideoSpecs": [
    {
      "Name": "Teacher",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Student",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Computer",
      "DeviceId": "0400-0002",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Blackboard",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    }
  ],
  "VideoCodecSpecs": [
    {
      "Name": "Teacher_Codec",
      "SourceName": "Teacher",
      "Codec": "h.264"
    }
  ],
  "CodecStreamSpecs": [
    {
      "Name": "Remote_pull",
      "VideoCodec": "h.264",
      "URI": "tcp://0.0.0.0:6671"
    },
    {
      "Name": "Audio_pull",
      "AudioCodec": "aac",
      "SampleRate": 48000,
      "Channels": 2,
      "URI": "tcp://0.0.0.0:6672"
    }
  ],
  "PlaySpecs": [
    {
      "Name": "TcpAudioPull_Play",
      "Sources": [
        {
          "SourceName": "Audio_pull",
          "Volume": 70
        }
      ]
    }
  ],
  "RenderSpecs": [
    {
      "Name": "Render_test",
      "DeviceId": "0800-0000",
      "CompositionSpec": [
        {
          "Geometry": [
            0,
            0,
            960,
            540
          ],
          "SourceName": "Teacher"
        },
        {
          "Geometry": [
            960,
            0,
            960,
            540
          ],
          "SourceName": "Student"
        },
        {
          "Geometry": [
            0,
            540,
            960,
            540
          ],
          "SourceName": "Blackboard"
        },
        {
          "Geometry": [
            960,
            540,
            960,
            540
          ],
          "SourceName": "Remote_pull"
        }
      ]
    }
  ]
}
```
- TCP方式需要接触UFW释放对应端口号(sudo ufw disable 关闭防火墙也可)
- TCP方式推流音视频要分开推送,RTSP/RTMP方式不用

###  补充RTMP,RTSP的推拉六

## 推流端
```json
{
  "Name": "Director_push",
  "Type": "MCS",
  "Description": "Far-End Director Push and Preview",
  "Version": "0.3",
  "AudioSpecs": [
    {
      "Name": "AudioInDefault",
      "SampleRate": 48000,
      "Channels": 2
    }
  ],
  "AudioCodecSpecs": [
    {
      "Name": "AudioInDefault_aac_Codec",
      "SourceName": "AudioInDefault",
      "Codec": "aac"
    }
  ],
  "VideoSpecs": [
    {
      "Name": "Teacher",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Student",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    }
  ],
  "VideoCodecSpecs": [
    {
      "Name": "Teacher_codec",
      "SourceName": "Teacher",
      "Codec": "h.264",
      "iFrameInterval": 30,
      "idrInterval": 30,
      "BitRateMode": "vbr",
      "BitRate": "4mbps"
    }
  ],
  "ServerSpecs": [
    {
      "Name": "Teacher_Server",
      "VideoCodecName": "Teacher_codec",
      "URI": "wp://10.12.224.135:6671"
    },
    {
      "Name": "Teacher_Audio_Server",
      "AudioCodecName": "AudioInDefault_aac_Codec",
      "URI": "wp://10.12.224.135:6672"
    }
  ],
  "RenderSpecs": [
    {
      "Name": "Render_test",
      "CompositionSpec": [
        {
          "Geometry": [0, 0, 960, 540],
          "SourceName": "Director"
        },
        {
          "Geometry": [960, 0, 960, 540],
          "SourceName": "Student"
        },
        {
          "Geometry": [0, 540, 960, 540],
          "SourceName": "Teacher"
        }
      ]
    }
  ]
}
```

# 2.8 Transform视频流修改分辨率
```json
{
  "Name": "TransformMCS",
  "Type": "MCS",
  "Description": "Far-End Director Push and Preview",
  "Version": "0.3",
  "VideoSpecs": [
    {
      "Name": "Teacher",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    },
    {
      "Name": "Student",
      "DeviceId": "",
      "Width": 1920,
      "Height": 1080,
      "FrameRate": 30
    }
  ],
    "VideoTransformSpecs": [
        {
            "Name": "VideoTransform",
            "SourceName": "Teacher",
            "Operation": "Scale",
            "Width": 720,
            "Height": 480
        }
    ],
    "VideoCodecSpecs": [
        {
            "Name": "VideoTransform_Codec",
            "SourceName": "VideoTransform",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "2mbps",
            "iFrameInterval": "30",
            "idrInterval": "30"
        }
    ],
  "RenderSpecs": [
    {
      "Name": "Render_test",
      "CompositionSpec": [
        {
          "Geometry": [0, 0, 960, 540],
          "SourceName": "VideoTransform"
        },
        {
          "Geometry": [960, 0, 960, 540],
          "SourceName": "Student"
        },
        {
          "Geometry": [0, 540, 960, 540],
          "SourceName": "Teacher"
        }
      ]
    }
  ]
}
```



# 2.n. 带算法的导播视频流

```json
{
    "Name": "Basic_MCS",
    "Type": "MCS",
    "Description": "The four-channel AI scenario Basic MCS",
    "Version": "0.3",
    "VideoSpecs": [
        {
            "Name": "Teacher",
            "DeviceId": "0400-0000",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Student",
            "DeviceId": "0400-0001",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Computer",
            "DeviceId": "0400-0002",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Blackboard",
            "DeviceId": "0403-0001",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        }
    ],
    "VideoAiSpecs": [
        {
            "Name": "Teacher_Ai",
            "SourceName": "Teacher",
            "Algorithm": "Teacher Tracking",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Student_Ai",
            "SourceName": "Student",
            "Algorithm": "Student Tracking",
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Computer_Ai",
            "SourceName": "Computer",
            "Algorithm": "Ppt Tracking",
            "ProcessRate": 10,
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        },
        {
            "Name": "Blackboard_Ai",
            "SourceName": "Blackboard",
            "Algorithm": "Blackboard Tracking",
            "ProcessRate": 10,
            "Width": 1920,
            "Height": 1080,
            "FrameRate": 30
        }
    ],
    "VideoCodecSpecs": [
        {
            "Name": "Teacher_h264_Codec",
            "SourceName": "Teacher",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "4mbps",
            "iFrameInterval": 30,
            "idrInterval": 30
        },
        {
            "Name": "Student_h264_Codec",
            "SourceName": "Student",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "4mbps",
            "iFrameInterval": 30,
            "idrInterval": 30
        },
        {
            "Name": "Computer_h264_Codec",
            "SourceName": "Computer",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "4mbps",
            "iFrameInterval": 30,
            "idrInterval": 30
        },
        {
            "Name": "Director_h264_Codec",
            "SourceName": "Director",
            "Codec": "h.264",
            "BitRateMode": "VBR",
            "BitRate": "4mbps",
            "iFrameInterval": 30,
            "idrInterval": 30
        }
    ],
    "VideoDirectorSpec": {
        "Name": "Director",
        "Width": 1920,
        "Height": 1080,
        "FrameRate": 30,
        "VideoSourceSet": [
            "Student",
            "Teacher",
            "Student_Ai",
            "Teacher_Ai",
            "Computer_Ai",
            "Blackboard_Ai"
        ],
        "FrameSpec": {
            "Template": "single frame",
            "LayoutSpecs": [
                {
                    "Position": 1,
                    "SelectionSpecs": [
                        {
                            "State": "Stand_N",
                            "Priority": 1,
                            "VideoSource": "Student",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 180
                        },
                        {
                            "State": "Stand_1",
                            "Priority": 2,
                            "VideoSource": "Student_Ai",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 180
                        },
                        {
                            "State": "PptMouseAction",
                            "Priority": 3,
                            "VideoSource": "Computer_Ai",
                            "Delay": 0,
                            "Hold": 15,
                            "Timeout": 3600
                        },
                        {
                            "State": "Many",
                            "Priority": 4,
                            "VideoSource": "Teacher_Ai",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Write",
                            "Priority": 6,
                            "VideoSource": "Blackboard_Ai",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Move",
                            "Priority": 7,
                            "VideoSource": "Teacher_Ai",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Stand",
                            "Priority": 8,
                            "VideoSource": "Teacher_Ai",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Out",
                            "Priority": 9,
                            "VideoSource": "Teacher",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Sit",
                            "Priority": 10,
                            "VideoSource": "Student",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "NoTeacher",
                            "Priority": 11,
                            "VideoSource": "Teacher",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        },
                        {
                            "State": "Others",
                            "Priority": 12,
                            "VideoSource": "Teacher",
                            "Delay": 0,
                            "Hold": 6,
                            "Timeout": 3600
                        }
                    ]
                }
            ]
        }
    },
    "CodecStreamSpecs": [
        {
            "Name": "Remote_pull",
            "VideoCodec": "h.264",
            "URI": "wp://0.0.0.0:6671"
        },
        {
            "Name": "Remote_pull_2",
            "VideoCodec": "h.264",
            "URI": "wp://0.0.0.0:6673"
        },
        {
            "Name": "Audio_pull_2",
            "AudioCodec": "aac",
            "SampleRate": 48000,
            "Channels": 2,
            "URI": "wp://0.0.0.0:6674"
        },
        {
            "Name": "Remote_pull_3",
            "VideoCodec": "h.264",
            "URI": "wp://0.0.0.0:6675"
        },
        {
            "Name": "Audio_pull_3",
            "AudioCodec": "aac",
            "SampleRate": 48000,
            "Channels": 2,
            "URI": "wp://0.0.0.0:6676"
        }
    ],
    "PlaySpecs": [
        {
            "Name": "TcpAudioPull_Play",
            "Sources": [
                {
                    "SourceName": "Audio_pull_2",
                    "Volume": 70
                },
                {
                    "SourceName": "Audio_pull_3",
                    "Volume": 70
                }
            ]
        }
    ],
    "RenderSpecs": [
        {
            "Name": "Render_test",
            "DeviceId": "0800-0000",
            "Background": "NA",
            "CompositionSpec": [
                {
                    "Geometry": [
                        0,
                        0,
                        960,
                        540
                    ],
                    "SourceName": "Director"
                },
                {
                    "Geometry": [
                        960,
                        0,
                        960,
                        540
                    ],
                    "SourceName": "Remote_pull"
                },
                {
                    "Geometry": [
                        0,
                        540,
                        960,
                        540
                    ],
                    "SourceName": "Remote_pull_2"
                },
                {
                    "Geometry": [
                        960,
                        540,
                        960,
                        540
                    ],
                    "SourceName": "Remote_pull_3"
                }
            ]
        }
    ],
    "RecordSpecs": [
        {
            "Name": "Director_Record",
            "AudioCodecName": "AudioInDefault_aac_Codec",
            "VideoCodecName": "Director_h264_Codec",
            "Format": "mp4",
            "Path": "Basic_yyyy-mm-dd-hh-mm-ss.mp4"
        }
    ]
}
```


## 注
- 我们提供了一份默认的导播策略如上


  ![docker_image](picture/docker_success.png)

