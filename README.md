# lightwallet-api

## 钱包接口

### 通用

####  查看币种信息 

> 查询平台支持的币种，以及该币种的精度、最小提币数、手续费等等配置。

####  查询余额

> 用户查询账户下某币种的当前余额

#### internal-addr/内部地址查询

> 查询地址是否属于内部地址


### 充值类

####  deposit/获取充值地址

> 为某币种申请充值使用的地址

####  deposit/获取充值记录


### 提币类

> 通过条件查询用户充值记录

#### withdraw/查询提币记录

> 查询用户提币记录

#### withdraw/查询提币工单状态

> 查询用户某笔提币订单状态

#### withdraw/提币预校验接口

> 提币前的预检查，不会产生提币订单

#### withdraw/提交提币工单

> 正式提交一笔提币请求


## 用户接口

### withdraw/提币回调接口

> 用户搭建提币回调接口的格式规范

### deposit/充值回调接口

> 用户搭建充值回调接口的格式规范

## 限频规则

> 每个appid在1秒内限制10次


## 提币说明

用户提币时填写的数量会直接发送，而额外的手续费会在用户的剩余余额中扣减。
