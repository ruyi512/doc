## 接口说明

### 创建微信机器人
- 请求地址: **POST /api/robots**
- 请求参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "username":"string, 微信号"
    }
```
- 成功响应:
```json
    {
        "RetCode": "int, 错误码，0代表成功，其它代表错误",
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            }
        }
    }
```

### 获取微信登录二维码
- 请求地址: **GET /api/robots/<string:robot_id>/qrcode**
- 请求参数:
    - token: 访问令牌
- 成功响应:
    QRCode图片

### 获取微信群列表
- 请求地址: **GET /api/robots/<string:robot_id>/rooms**
- 请求参数:
```json
    {
        "token": "string, 访问令牌，由平台分配"
    }
```
- 成功响应:
```json
    {
        "RetCode": "int, 错误码，0代表成功，其它代表错误",
        "data": {
            "rooms": [
                {
                    "id": "string, 房间唯一标识",
                    "status": "int, 状态",
                    "nickname": "string, 微信群名"
                },
                ...
            ]
        }
    }
```

### 发送消息
- 请求地址: **POST /api/robots/<string:robot_id>/message**
- 请求参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "username":"string, 微信号",
        "msg_type": "string, 类型，text代表文本，image代表图片",
        "content": "string, 消息内容"
    }
```
- 成功响应:
```json
    {
        "RetCode": "int, 错误码，0代表成功，其它代表错误"
    }
```

### 退出登录
- 请求地址: **POST /api/robots/<string:robot_id>/logout**
- 请求参数:
```json
    {
        "token": "string, 访问令牌，由平台分配"
    }
```
- 成功响应:
```json
    {
        "RetCode": "int, 错误码，0代表成功，其它代表错误",
    }
```

## 错误码
1205：图片发送太频繁，被限制发送
1102：微信已经退出登录
-1001：微信群不存在
-1002：未发现登录信息
-1003：加载登录信息失败
