## 接口改动

### 1、balance.php接口

请求json结构由:

```json
{
    "appid": "dafdfdafd", 
    "cryptype": 0,        
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", 
            "timestamp": 1234567890 
        },
        "coins": [
            "coin":"usdt"
        ]
    }
}
```

变更为：

```json
{
    "appid": "dafdfdafd", 
    "cryptype": 0,        
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", 
            "timestamp": 1234567890 
        },
        "coins": [
            {
                "chain":"eth",
                "coin":"usdt"
            }
        ]
    }
}

```

响应由:

```json
{
    "data": {
        "eth":{
            "coin"
            "balance"
            "as_cny"
        },
    }
}
```

变更为：

```json
{
    "data": [
        {
            "chain"
            "coin"
            "balance"
            "as_cny"
        },
    ]
}
```

### 2、deposit/history.php接口

请求：
```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fdafdafd", // 调用端子账号，字符串，平台不管其含义
        "coin": "usdt",          // 币名
        "fromid": 0,             // 整数，从哪个充值序号开始，从0开始
        "limit": 10              // 最多查询多少条记录，包含fromid这条记录
    }
}
```

更改为:

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fdafdafd", // 调用端子账号，字符串，平台不管其含义
        "chain": "eth",          // 主链
        "coin": "usdt",          // 币名
        "fromid": 0,             // 整数，从哪个充值序号开始，从0开始
        "limit": 10              // 最多查询多少条记录，包含fromid这条记录
    }
}
```

响应：

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "coin": "usdt",  // 币名
            "history": [ // 充值记录列表
                {
                    "id": 23,               // 内部充值序号
                    "subuserid": "dafdfds", // 调用端子账号，字符串，平台不管其含义
                    "chain": "eth",         // 哪条主链上充值进来的
                    "addr": "xfdaadad",     // 充值到哪个地址
                    "txid": "wefafdafd",    // 交易ID
                    "amount": 20.5,         // 充值数量
                    "balance": 56.5         // 充值后余额
                }
            ]
        }
    }
 }
```



更改为:

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": [
            {
                "id": 23,               // 内部充值序号
                "subuserid": "dafdfds", // 调用端子账号，字符串，平台不管其含义
                "chain": "eth",         // 哪条主链上充值进来的
                "coin": "eth",         // 哪条主链上充值进来的
                "from_addr":"addr1",    // 发送地址
                "addr": "xfdaadad",     // 充值到哪个地址
                "txid": "wefafdafd",    // 交易ID
                "amount": 20.5,         // 充值数量
                "balance": 56.5,         // 充值后余额
                "time":"2020-05-11 17:00:00" // 时间戳
            }
        ]
    }
 }
```

### 3、withdraw/history.php接口

请求：
```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fdafdafd", // 调用端子账号，字符串，平台不管其含义
        "coin": "usdt",          // 币名
        "fromid": 0,             // 整数，从哪个充值序号开始，从0开始
        "limit": 10              // 最多查询多少条记录，包含fromid这条记录
    }
}
```

更改为:

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fdafdafd", // 调用端子账号，字符串，平台不管其含义
        "chain": "eth",          // 主链
        "coin": "usdt",          // 币名
        "fromid": 0,             // 整数，从哪个充值序号开始，从0开始
        "limit": 10              // 最多查询多少条记录，包含fromid这条记录
    }
}
```

响应：

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "coin": "usdt",  // 币名
            "history": [ // 充值记录列表
                {
                    "id": 12,                 // 内部提币序号
                    "subuserid": "fdafdafd",  // 调用端子账号，字符串，平台不管其含义
                    "chain": "eth",           // 主链
                    "coin": "usdt",           // 币名
                    "addr": "dfaddaf",        // 提币目标地址
                    "amount": 12,             // 提币数量
                    "amount_sent": 11,        // 实际发送的提币数量=(amount-fee_amount)
                    "memo": "cvzcv",          // 提币备注，比如用户ID之类的，可以是任意内容，入库，防止SQL注入
                    "status": 0,              // 提币状态, 见外部提币状态定义: WITHDRAW_STATUS_*
                    "status_desc": "",        // 提币状态描述
                    "txid": "rtwfsfda",       // 链上的交易ID
                    "fee_coin": "eth",         // 手续费币种
                    "fee_amount": 1,          // 手续费数量
                    "time": "2019-10-10 00:00:00" // 订单创建时间
                }
            ]
        }
    }
 }
```
更改为:

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": [
            {
                "id": 12,                 
                "subuserid": "fdafdafd",  
                "chain": "eth",           
                "coin": "usdt",           
                "from_addr": "dfaddaf",   
                "addr": "dfaddaf",        
                "amount": 12,             
                "amount_sent": 11,        
                "sub_balance": 11, 
                "memo": "cvzcv",          
                "status": 0,              
                "status_desc": "",        
                "txid": "rtwfsfda",       
                "fee_coin": "eth",        
                "fee_amount": 1,    
                "usertags": "eth",                   
                "time": "2019-10-10 00:00:00" 
            }
        ]
    }
 }
```

### 4、withdraw/status.php接口

请求：

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "coin": "usdt",   // 币名
        "withdrawid": 12  // 提币ID，提币内部序号
    }
}
```

更改为:

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "chain": "usdt",  
        "coin": "usdt",   
        "withdrawid": 12  
    }
}
```

响应：

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "id": 12,                 // 内部提币序号
            "subuserid": "fdafdafd",  // 调用端子账号，字符串，平台不管其含义
            "chain": "eth",           // 主链
            "coin": "usdt",           // 币名
            "addr": "dfaddaf",        // 提币目标地址
            "amount": 12,             // 提币数量
            "amount_sent": 11,        // 实际发送的提币数量=(amount-fee_amount)
            "memo": "cvzcv",          // 提币备注，比如用户ID之类的，可以是任意内容，入库，防止SQL注入
            "status": 0,              // 提币状态, 见外部提币状态定义: WITHDRAW_STATUS_*
            "status_desc": "",        // 提币状态描述
            "txid": "rtwfsfda",       // 链上的交易ID
            "fee_coin": "eth",         // 手续费币种
            "fee_amount": 1,          // 手续费数量
            "time": "2019-10-10 00:00:00" // 订单创建时间
        }
    }
 }
```
更改为:

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "id": 12,                 
            "subuserid": "fdafdafd",  
            "chain": "eth",           
            "coin": "usdt",           
            "from_addr": "dfaddaf",   
            "addr": "dfaddaf",        
            "amount": 12,             
            "amount_sent": 11,        
            "sub_balance": 11, 
            "memo": "cvzcv",          
            "status": 0,              
            "status_desc": "",        
            "txid": "rtwfsfda",       
            "fee_coin": "eth",        
            "fee_amount": 1,    
            "usertags": "eth",                  
            "time": "2019-10-10 00:00:00" 
        }
    }
}
```

### 5、withdraw/submit.php接口

请求：

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fafafd", // 调用端子账号，字符串，平台不管其含义
        "chain": "eth",        // 主链
        "coin": "usdt",        // 币名
        "addr": "qwdfad",      // 提币目标地址
        "amount": 20,          // 提币数量
        "memo": "dafafe",      // 提币备注，比如用户ID之类的，可以是任意内容，入库，防止SQL注入
        "sign": "fafdafdaf"    // 提币请求签名, md5("{appid}+{salt}+{userid}+{timestamp}+{addr}+{memo}"), {name}代表变量
    }
}
```

更改为:

```json
{
    "appid": "dafdfdafd", // 用户身份ID, 一个唯一的随机字符串
    "cryptype": 0,        // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data": {
        "auth" : {
            "token": "cvzcvdafdad", // md5("{appid}+{salt}+{userid}+{timestamp}"), {name}代表变量
            "timestamp": 1234567890 // 时间戳,单位秒
        },
        "subuserid": "fafafd", // 调用端子账号，字符串，平台不管其含义
        "chain": "eth",        // 主链
        "coin": "usdt",        // 币名
        "addr": "qwdfad",      // 提币目标地址
        "amount": 20,          // 提币数量
        "memo": "dafafe",      // 提币备注，比如用户ID之类的，可以是任意内容，入库，防止SQL注入
        "usertags": "dafafe",  // 用户标签，用于用户作侧ID使用
        "sign": "fafdafdaf"    // 提币请求签名, md5("{appid}+{salt}+{userid}+{timestamp}+{addr}+{memo}"), {name}代表变量
    }
}
```

响应：

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "id": 12,                 // 内部提币序号
            "subuserid": "fdafdafd",  // 调用端子账号，字符串，平台不管其含义
            "chain": "eth",           // 主链
            "coin": "usdt",           // 币名
            "addr": "dfaddaf",        // 提币目标地址
            "amount": 12,             // 提币数量
            "amount_sent": 11,        // 实际发送的提币数量=(amount-fee_amount)
            "memo": "cvzcv",          // 提币备注，比如用户ID之类的，可以是任意内容，入库，防止SQL注入
            "status": 0,              // 提币状态, 见外部提币状态定义: WITHDRAW_STATUS_*
            "status_desc": "",        // 提币状态描述
            "txid": "rtwfsfda",       // 链上的交易ID
            "fee_coin": "eth",         // 手续费币种
            "fee_amount": 1,          // 手续费数量
            "time": "2019-10-10 00:00:00" // 订单创建时间
        }
    }
}
```
更改为:

```json
{
    "cryptype": 0,  // 0=data未加密(json格式),1=data已加密(加密字符串)
    "data" : {
        "eno": 0,          // 错误码
        "emsg": "dafdafd", // 错误信息
        "data": {
            "id": 12,                 
            "subuserid": "fdafdafd",  
            "chain": "eth",           
            "coin": "usdt",           
            "from_addr": "dfaddaf",   
            "addr": "dfaddaf",        
            "amount": 12,             
            "amount_sent": 11,        
            "sub_balance": 11, 
            "memo": "cvzcv",          
            "status": 0,              
            "status_desc": "",        
            "txid": "rtwfsfda",       
            "fee_coin": "eth",        
            "fee_amount": 1,    
            "usertags": "eth",                  
            "time": "2019-10-10 00:00:00" 
        }
    }
}
```

### 6、充值回调接口

请求内容从原来的:

```json
{
    "orderid": 12,
    "subuserid":"",
    "chain":"eth",
    "coin":"eth",
    "from_addr":"addr1", 
    "addr":"add2",
    "txid":"",
    "amount":100,
    "balance":1000,
    "time":"2020-05-01"
}

```

更改为:

```json
{
    "id": 12,
    "subuserid":"",
    "chain":"eth",
    "coin":"eth",
    "from_addr":"addr1", 
    "addr":"add2",
    "txid":"",
    "amount":100,
    "balance":1000,
    "time":"2020-05-01"
}
```

### 7、提币回调接口

请求内容从原来的:

```json
{
    "withdrawid": 1,
    "subuserid":"",
    "chain":"",
    "coin":"",
    "from_addr":"",
    "addr":"",
    "txid":"",
    "amount":"",
    "amount_sent":0,
    "memo":"",
    "status":"",
    "status_desc":"",
    "fee_coin":"",
    "fee_amount":20,
    "time":"2020-05-01"
}
```

更改为:

```json
{
    "id": 1,
    "subuserid":"",
    "chain":"",
    "coin":"",
    "from_addr":"",
    "addr":"",
    "txid":"",
    "amount":"",
    "amount_sent":0,
    "sub_balance":10,
    "memo":"",
    "status":"",
    "status_desc":"",
    "fee_coin":"",
    "fee_amount":20,
    "usertags":"",
    "time":"2020-05-01"
}
```