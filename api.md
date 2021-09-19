# Site API 

## GET /uc/coin_lists
获取用户资产列表

返回示例:
```
{
    "coins": [
        {
            "coin": "chia",
            "display_name": "Chia",
            "icon": "https://assets.alltheblocks.net/icons/forks/chia.png",
            "symbol": "xch",
            "space": 35.018,
            "balance": 100,
            "earnings_24h": 0,
            "earnings_usd_24h": 0,
            "status": 1
        }
    ]
}
```

字段说明
 * coin: 币名
 * display_name: 币种显示名
 * symbol: 币符
 * space: 空间大小 (单位: EiB)
 * earnings_24h: 最近24小时收益
 * earnings_usd_24h: 最近24小时收益(美元)
 * status: 状态(0: 未启用,1: 耕种中)


## GET /uc/transactions
获取账单流水

返回示例:
```
{
    "transactions": [
        {
            "id": "1",
            "coin": "chia",
            "icon": "https://assets.alltheblocks.net/icons/forks/chia.png",
            "symbol": "xch",
            "type": 1,
            "amount": 2,
            "address": "",
            "processed_at": "2021-09-19T17:25:31+08:00"
        },
        {
            "id": "2",
            "coin": "chia",
            "icon": "https://assets.alltheblocks.net/icons/forks/chia.png",
            "symbol": "xch",
            "type": 2,
            "amount": 20,
            "address": "",
            "processed_at": "2021-09-19T17:26:04+08:00"
        }
    ]
}
```

字段说明
* coin: 币名
* type: 交易类型 (1: 耕种奖励, 2: 提现)
* address: 外部钱包地址 (提现)
* space: 空间大小 (单位: EiB)
* processed_at: 最近24小时收益

## GET /market/coins
获取各币种收益率列表

```
{
    "coins": [
        {
            "coin": "chaingreen",
            "display_name": "Chaingreen",
            "icon": "https://assets.alltheblocks.net/icons/forks/chaingreen.png",
            "symbol": "cgn",
            "space": 0.563,
            "space_change": 0.01,
            "height": 629510,
            "reward": 2,
            "price": 200,
            "hourly_earnings": 0.1,
            "hourly_earnings_usd": 12,
            "daily_earnings": 2,
            "daily_earnings_usd": 160,
            "monthly_earnings": 60,
            "monthly_earnings_usd": 2000,
            "etw": 3600,
        }
    ]
}
```

字段说明
  * coin: 币名
  * display_name: 币种显示名
  * symbol: 币符
  * space_change: 空间变化 (百分比)
  * height: 高度
  * reward: 奖励
  * price: 价格(美元)
  * hourly_earnings: 小时收益
  * hourly_earnings_usd: 小时收益(美元)
  * etw: 预计赢得奖励时间


## POST /uc/addresses
创建新外部钱包地址

请求示例:
```
{
    "name": "我的chia钱包",
    "address": "xch12szpttkl37gl26ndhsme5hdw2lpf6drf3y62u8tljj804fx7jmcszeedfp"
}
```
字段说明
  * name: 备注名
  * address: 地址

## DELETE /uc/addresses/:id

删除钱包地址

请求示例:
```
DELETE /uc/addresses/c53ekv59481d1i62bncg
```

## GET /uc/addresses
获取用户外部钱包地址
```
{
    "addresses": [
        {
            "id": "c53ekv59481d1i62bncg",
            "name": "我的chia钱包",
            "coin": "chia",
            "icon": "https://assets.alltheblocks.net/icons/forks/chia.png",
            "symbol": "xch",
            "address": "xch1nxtu7cw7f8dl8kucljf4e9r3mdyued2g8wlx75cqplxsnksfkq5swld3dd",
            "created_at": "2021-09-19T15:45:01+08:00"
        }
    ]
}
```


## GET /uc/payouts
提现记录

```
{
    "payouts": [
        {
            "id": "111",
            "coin": "chia",
            "icon": "https://assets.alltheblocks.net/icons/forks/spare.png",
            "symbol": "spare",
            "amount": 2,
            "to_address": "xch1nxtu7cw7f8dl8kucljf4e9r3mdyued2g8wlx75cqplxsnksfkq5swld3dd",
            "processed": true,
            "created_at": "2021-09-19T16:32:28+08:00"
        }
    ]
}
```

字段说明
 * amount: 提现金额
 * to_address: 收款地址
 * processed: 是否处理


## GET /uc/partials
查询贡献点

```
{
    "partials": [
        {
            "timestamp": 1632041216965,
            "difficulty": 10,
            "harvester_id": "abcd",
            "proof": "akdlskj39we"
        }
    ]
}
```

字段说明
 * timestamp: 时间戳
 * difficulty: 难度
 * harvester_id: 收割机
 * proof: 证明


## GET /uc/harvesters
获取收割机列表

响应示例:
```
{
    "harvesters": [
        {
            "id": "11",
            "name": "wei-Legion",
            "plots": 98,
            "is_online": true,
            "created_at": "2021-09-19T16:57:58Z",
            "updated_at": "2021-09-19T16:57:58Z"
        }
    ]
}
```

字段说明
 * id: ID
 * name: 主机名
 * plots: 图数
 * is_online: 是否在线

## GET /uc/configuration

获取配置(FarmerKey)

```
{
    "farmer_key": "9a38901bfe8a936957db1422c83403c088f04509f0e4d5581312b0cdc21e0304_5dbd52248c0909ddb20f677d96b135bbe26e244d37c94ae00a641c7d2ae24499"
}
```


## GET /uc/login_logs
获取登录日志 

响应示例:
```
{
    "login_logs": [
        {
            "id": "aaa",
            "ip": "139.227.3.56",
            "login_at": "2021-09-19T17:18:24+08:00"
        }
    ]
}
```

## Authenticate
Authorization