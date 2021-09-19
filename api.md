# Site API 

# GET /uc/coin_lists
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
 * earnings_24h: 最近24小时收益
 * earnings_usd_24h: 最近24小时收益(美元)
 * status: 状态(0: 未启用,1: 耕种中)

## Authenticate
Authorization