# DemoMCS脚本使用教程

标签（空格分隔）： DemoMCS

---
[TOC]
## 重新规划

1.给客户展示MCS内容
2.

###1.脚本架构

#### 1.1 目录结构安排
![image_1gb48vsb77vm4ud1671f101fuf1t.png-25.5kB][1]

#### 1.2 运行脚本的小站IP设置
![image_1gb494uuh1jbq1ttedu1he51q472a.png-26.4kB][2]

- `set_environment_linux.py`
如果MCS脚本放在linux开发机上运行该脚本安装`request`库
- `set_environment_windows.py`
如果MCS脚本放在windows上运行该脚本安装`request`库**(推荐)**
- `set_environment_Metis.py`
如果MCS脚本放在MetisStaton小站上运行该脚本安装`request`库

<br />
#### 1.3 环境配置

##### 1.3.1 小站IP地址设置
MCS目录下存在libraries目录，该目录下存放5个py文件，其中
`mediatasklib.py 、mediadevicelib.py 、mediatasklib.py`
三个库文件封装了对应的3个MA接口类
`functionlib.py`封装了一些便于开发的函数
`environment.py`文件设定了指定下发MCS的小站IP
```python
# 设置对应小站IP函数
def check_eth_connect():
    ip_get_cmd = "ifconfig eth0 | grep 'inet ' | awk '{print $2}'"
    if sys.platform.startswith("win"):
        # 如果是Windows系统，需要手动设置修改下面IP地址
        HOST_IP = '10.12.224.135'
        # print(HOST_IP)
    else:
        while True:
            # 如果是linux系统，而且脚本放在小站上,可以自动获取IP地址
            # 但如果是放在开发机上，就不能调用这个函数获取IP地址
            # 需要手动修改其他4个lib.py文件里HOST_IP的值
            HOST_IP = os.popen(ip_get_cmd).read().strip()
            if HOST_IP is None or HOST_IP == "":
                continue
            else:
                # print(HOST_IP)
                break
    return HOST_IP

```
如上述所说，脚本在**Windows**上运行,需要修改该`environment.py`文件上述第6行变量 `HOST_IP` 的值，如果脚本放在**小站**上运行，可以自动获取小站的IP，不用修改任何文件

##### 1.3.2 脚本运行环境设置
- 方式一：
    DemoMCS目录下存放`set_environment_linux.py`脚本，在终端输入下述内容安装环境
    > python set_environment_linux.py
    
    - 优点：执行方式简单
    - 缺点：会修改系统环境，将python软链接指向python3而不是python2
<br>

- 方式二：
    通过Docker技术配置脚本运行环境，依次执行下述指令来配置环境。
    ```shell
$ sudo usermod -aG docker user   # 解决Docker sudo权限
$ su - user 
$ docker pull sameswinhub/sam-story-python:1.0 # 从dockerhub上下载需要使用的image
    ```
    镜像文件下载完成后，终端输入下述指令查看是否成功


| 序号| 参数名称 | 值类型 |   说明  |
|:----:|:----:|:----:|:----:|
|1	|DeviceName|	string|	对应摄像头的DeviceName属性值



###2.通用模板General_Module
在 **Tier3**目录下存放General_Module目录，该目录下存放对应通用性较高的脚本
json_templates目录下存放的是要下发的MCS

> 脚本统一运行方式为 python XXXX.py 
大部分脚本可以带参数

</br>
</br>
####2.1 create_update.py

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -jf:指定脚本读取的`json_templates`目录下的json文件

举例
>python create_update.py -ip=10.12.224.135 -js=1

对应就是读取1.json里的MCS，并且下发给10.12.224.135小站
</br>
</br>
####2.2 delete_all_tasks.py

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP

举例:
> python delete_all_tasks.py -ip=10.12.224.135 

该脚本实际上通过`get mediatask/v3/tasks`接口获取当前所有的Task的`MCS Name`，再调用`delete mediatask/v3/[MCS Name]`接口删除当前所有任务
</br>
</br>

####2.3 delete_task_by_name.py

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -n: 指定的MCS Name

举例:
> python delete_all_tasks.py -ip=10.12.224.135 -n=MCSName

该脚本实际上就是使用`delete mediatask/v3/[MCS Name]`接口删除指定n参数的任务
</br>
</br>
####2.4 remove.py

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -mn: 指定的MCS Name
* -sn: 指定MCS对应Spec的Name字段


举例:
> python one_cam_preview.py -ip=10.12.224.135 -mn=MCSV3 -ct=USB -g=0,0,960,540
创建一个USB单路回显画面，宫格位置为0，0，960，540

</br>
</br>
####3.2 one_cam_push.py
该脚本对应读取的是`json_templates`目录下`one_cam_push.json`文件
**作用：对指定MCS Name 下发对应参数的推流任务**

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -mn: 指定的MCS `Name`,缺省值为MCSV3
* -t: 进行推流的方式，可选参数有 tcp、rtsp
* -c: 即MCS中的`VideoCodecSpecs`字段，可选参数有h264，h265，缺省值为h264

举例:
> python one_cam_push.py -ip=10.12.224.135 -mn=MCSName -t=tcp -c=h264

下发MCS `Name` 为 **MCSName** 的 **TCP** 推流任务，推流编码为**h.264**

</br>
</br>

####3.3 one_pull_preview.py
该脚本对应读取的是`json_templates`目录下`one_pull_preview.json`文件
**作用：对指定MCS Name 下发对应参数的拉流任务**

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -mn: 指定的MCS `Name`,缺省值为MCSV3
* -vc: 指定MCS对应`VideoCodec`字段内容,可选参数有h264，h265，缺省值为h264
* -t: 指定的拉流类型,可选参数有 tcp、rtsp
举例:
> python one_pull_preview.py -ip=10.12.224.135 -mn=MCSName -t=tcp -vc=h264

    下发MCS `Name` 为 **MCSName** 的 **TCP** 拉流任务，拉流编码为**h.264**
</br>
</br>


####3.4 pull_record.py
该脚本对应读取的是`json_templates`目录下`pull_record.json`文件
**作用：对指定MCS Name拉流任务进行对应编码格式的录制，生成对应格式的视频文件**

举例:
> python pull_record.py -ip=10.12.224.135 -mn=MCSName -c=h264 -rt=mp4

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -mn: 指定的MCS `Name`,缺省值为MCSV3
* -c: 指定录制视频编码对应`Codec`字段内容,可选参数有h264，h265，缺省值为h264
* -rt：生成的视频文件格式，缺省值为mp4

下发MCS `Name` 为 **MCSName** 拉流任务的录制，录制的编码格式为h.264,生成MP4文件

####3.5 push_record.py
该脚本对应读取的是`json_templates`目录下`push_record.json`文件
**作用：对指定MCS Name推流任务进行对应编码格式的录制，生成对应格式的视频文件**

举例:
> python push_record.py -ip=10.12.224.135 -mn=MCSName -rt=mp4

* -ip:指定下发MCS小站的IP，缺省为默认的当前小站IP
* -mn: 指定的MCS `Name`,缺省值为MCSV3
* -rt：生成的视频文件格式，缺省值为mp4

下发MCS `Name` 为 **MCSName** 推流任务的录制，生成MP4文件

####3.6 此外其他脚本
该部分包含`remove.py、inspection.py、delete_task_by_name.py、delete_all_tasks.py`几个脚本，作用与前文第二部分脚本相同。

####3.7 Act_Story.py
区别于第二部分的`Act_Story.py`脚本，由于Complex_Module目录下其他脚本都是参数化构建，迁移性较高
```python
import sys
sys.path.append('../../libraries')
from functionlib import *

scriptlist = ['one_cam_preview.py -ct=IPC',
              'one_pull_preview.py -t=tcp',
              'one_cam_push.py',
              'push_record.py',
              'pull_record.py',
              'remove.py -sn=Pull_Record',
              'remove.py -sn=Push_Record',
              'remove.py -sn=Main_Display',
              'remove.py -sn=OneCam_Server',
              'remove.py -sn=Pull_Display,CodecStreamSpec_pull,Pull_Codec',
              'delete_all_tasks.py'
              ]

if __name__ == '__main__':
    act_story(scriptlist, sleeptime=2)
```
该部分的第**5**行代码，通过修改`-ct`参数值
> one_cam_preview.py -ct=IPC

`-ct=HDMI`或者`-ct=USB`，即可实现下图3种类型的HDMI摄像头测试

---
![image_1g4d2md5r1j781j5a1quo1pcbaoa13.png-12.5kB][7]

---

同样的，通过修改第**8、9**行的代码，可以实现下图


> 'one_pull_preview.py -t=tcp'  
> 'one_cam_push.py -t=tcp' 

修改成
> 'one_pull_preview.py -t=rtsp'  
> 'one_cam_push.py -t=rtsp' 

此外，经过调整顺序，增加或者减少列表内脚本内容，一个Complex_Moudule目录理论上可以实现下图涵盖的所有测试

---
![image_1g4d2pe9g11uj7esq2k1l2e1s551g.png-39.6kB][8]
---

####3.8 总结
通过增加单个功能脚本的复杂性，参数化构建复杂度，使得一个脚本读取单个json模板文件，根据参数不同，替换对应json文件MCS的内容，实现MCS **json模板文件高复用**的特点，同时，**单功能脚本可迁移性较高，可以方便后续其他内容的测试**。
相比于第二部分General_Module是单脚本对应多json文件，此处Complex_Module是单脚本对应单json文件。


  [1]: http://static.zybuluo.com/gamerxtc/g6zns68x045diz2pwgjy5v87/image_1gb48vsb77vm4ud1671f101fuf1t.png
  [2]: http://static.zybuluo.com/gamerxtc/vj12zz49ee8115ypcxkqjv7e/image_1gb494uuh1jbq1ttedu1he51q472a.png
  [3]: http://static.zybuluo.com/gamerxtc/a5auqgkaapag0uced4saak4h/image_1gd9s1flfqsd1q7n21693cc569.png
  [4]: C:%5CUsers%5CXtc_Work_PC%5CDesktop%5CDemoMCS%20Document
  [5]: http://static.zybuluo.com/gamerxtc/nlspz7pznkp4xfdhe0lddmof/image_1g4ctrco7gua1578vim1tfa3tr9.png
  [6]: http://static.zybuluo.com/gamerxtc/6k8ksvibvk8hbf8s14np26v9/image_1g4d15j9v17fmuge1dv7k6lskcm.png
  [7]: http://static.zybuluo.com/gamerxtc/x69pknwaduw6e54myv152rh1/image_1g4d2md5r1j781j5a1quo1pcbaoa13.png
  [8]: http://static.zybuluo.com/gamerxtc/k7lb3xnje9f5pv5v0hm6wanm/image_1g4d2pe9g11uj7esq2k1l2e1s551g.png