# 3.1 Auth——authlib

## 3.1.1 post_auth

- 描述： 用于向Media Agent认证，以获得后续操作的令牌。对应 MA 文档 **<font color=#FF7F00>POST</font>** **`/auth`** 接口
- 输入参数说明

  | 参数名称 |      类型      |       描述       |    备注    |
  |:------------:| :------: |:--------:| :--------------------: |
  | username    |    string    |      用户名      | 缺省值admin |
  | password    |    string    | 用户密码 |    缺省值admin      |

- 输出参数说明

  | 参数名称 |        类型        |      描述       |               备注               |
  |:----------------:|:------:|:------------------------------:|:--------------------:|
  | response    |     Response     | 响应体特殊结构   |      参考响应体描述[Response](/api/response.html)       |