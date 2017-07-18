## 接口说明

### 创建微信机器人
- 请求地址: **POST /robots**
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
        "errorMsg": "string, 错误描述"
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

### 微信登录
- 请求地址: **POST /robots/<string:robot_id>/login**
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
        "errorMsg": "string, 错误描述"
        "data": {
            "robot": {
                "id": "string, 机器人唯一标识",
                "status": "string, 状态",
                "username": "string, 微信号",
                "nickname": "string, 微信昵称"
            },
            "qrcode_url": "string, 微信登录二维码链接"
        }
    }
```

### 获取微信群列表
- 请求地址: **GET /robots/<string:robot_id>/rooms**
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
        "errorMsg": "string, 错误描述"
        "data": {
            "rooms": [
                {
                    "id": "string, 微信群唯一标识",
                    "nickname": "string, 微信群备注"
                },
                ...
            ]
        }
    }
```

### 发送消息
- 请求地址: **POST /robots/<string:robot_id>/message**
- 请求参数:
```json
    {
        "token": "string, 访问令牌，由平台分配",
        "to_user":"string, 微信群唯一标识",
        "msg_type": "string, 类型，text代表文本，image代表图片",
        "content": "string, 消息内容，如果msg_type是image类型，请放图片链接"
    }
```
- 成功响应:
```json
    {
        "RetCode": "int, 错误码，0代表成功，其它代表错误",
        "errorMsg": "string, 错误描述"
    }
```

### 退出登录
- 请求地址: **POST /robots/<string:robot_id>/logout**
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
        "errorMsg": "string, 错误描述"
    }
```

## 错误码
- 1205：图片发送太频繁，被限制发送
- 1102：微信已经退出登录
- 1: 请求接口失败
- -1: 消息发送失败
- -1001：微信群不存在
- -1002：未发现登录信息
- -1003：加载登录信息失败
