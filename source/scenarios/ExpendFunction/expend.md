## 4.0.1. LogFile功能

Log File 设计：  
- 脚本路径： **/home/user/Metis-MCS/03_Scenario_Driven_Tests/ ``GeneralCtrl.py``**  

- 说明：  
    1. 跟参数 `-logfile=XXXX` （log文件名）会开启Log File功能，运行其他Scenario脚本后，会将其流程调用的接口以及使用的MCS
       记录在对应的Log文件里。如果 ``-logfile=OFF`` ，则会关闭Log File功能。
    2. 也可以通过配置/home/user/Metis-MCS/Libraries目录下的配置文件 `MCSConfiguration.json` ,将 `IsLogFile` 设置为true
       也可开启Log File功能。

- Log存放路径
    - Linux 系统：/home/user/Metis-MCS/MCS_Log
    - Windows系统：为运行的脚本所在的路径

## 4.0.2. Others

    To Be Designed...
