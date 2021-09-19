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
            "coin": "",
            "icon": "",
            "symbol": "",
            "address": "xch1nxtu7cw7f8dl8kucljf4e9r3mdyued2g8wlx75cqplxsnksfkq5swld3dd",
            "created_at": "2021-09-19T15:45:01+08:00"
        }
    ]
}
```


## Authenticate
Authorization