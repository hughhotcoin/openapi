

### 成交记录
#### GET /api/v1/perpetual/admin/deal-record

请求参数：


#### 请求参数：


##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
contractCode|n|string|合约code||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
startId|n|long|开始id||
endId|n|long|结束id||
userId|y|long|userId||



```json
{
    "code": 200,
    "data": {
        "data": [
            {
                "amount": "6.0000000000000000",
                "contractCode": "btcusdt",
                "contractCodeDisplayName":"btcusdt",
                "createDate": "2021-11-14 20:52:03",
                "currencyCode": "usdt",
                "currencyCodeDisplayName":"usdt",
                "dealType": 1,
                "env":0,
                "detailSide": "close_long",
                "fee": "1.3579752900000000",
                "id": "666746374653476864",
                "makerTaker": "maker",
                "orderId": 125090120907072,
                "price": "64665.4900000000000000",
                "profit": "0.9555748956901509",
                "refOrderId": 125090122965326,
		"refUserId": 10000,
                "size": "3879.9294000000000000",
                "userId": "2000011"
            }
        ],
        "pageNum": 1,
        "pageSize": 20,
        "totalCount": 112677
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
amount|y|string|成交数量||
contractCode|y|string|合约code||
contractCodeDisplayName|y|string|合约Code 显示名||
createDate|y|string|创建时间||
currencyCode|y|string|币种||
currencyCodeDisplayName|y|string|币种显示名||
dealType|y|string|成交类型，1：自成交，2：与其他用户成交||
detailSide|y|string|开平方向||
fee|y|string|手续费||
id|y|long|成交记录id||
makerTaker|y|string|maker or taker||
orderId|y|long|订单id||
price|y|string|成交价格||
profit|y|string|收益||
refOrderId|y|long|关联订单id||
refUserId|y|long|关联userId||
size|y|string|成交价值||
userId|y|long|uid||
env|y|int|0-实盘/1-模拟盘||


### 历史订单记录
#### GET /api/v1/perpetual/admin/{contractCode}/order/list

请求参数：


#### 请求参数：

##### 路径参数
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
contractCode|y|string|合约code||

##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
userIds|n|List<long>|用户id||

```json
{
    "code": 200,
    "data": {
        "rows": [
            {
                "amount": "1",
                "avgPrice": "23000",
                "base": "usdt",
                "brokerId": 1,
                "contractCode": "btcusdt",
                "contractDirection": 0,
                "createdDate": 1659685346000,
                "dealAmount": "1",
                "detailSide": "open_short",
                "direction": "",
                "env": 0,
                "fee": "-0.1495",
                "id": 148428130610224,
                "indexBase": "btc",
                "indexBaseDisplayName": "BTC",
                "lever": "125",
                "modifyDate": 1659685346000,
                "orderPriceType": 0,
                "orderSize": "232.968878",
                "positionType": 0,
                "price": "23000",
                "profit": "0",
                "quote": "usdt",
                "reason": 0,
                "refConditionOrderId": 0,
                "refOrderCondition": null,
                "side": "short",
                "source": "WEB",
                "status": 2,
                "stopLimitType": 0,
                "stopLoss": null,
                "stopProfit": null,
                "systemType": 10,
                "triggerBy": "",
                "triggerDate": 0,
                "triggerPrice": "",
                "userId": 20100195
            }
        ],
        "total": 18
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
id|y|string|订单id||
lever|y|string|杠杆||
userId|y|long|uid||
contractCode|y|string|合约code||
userId|y|long|uid||
base|y|string|基础币||
quote|y|string|计价币||
indexBase|y|string|指数币||
env|y|int|0-实盘/1-模拟盘||
contractDirection|y|string|合约方向：0:正向,1:反向||
side|y|string|仓位方向：long多，short空||
detailSide|y|string|详细仓位方向：1.开多open_long 2.开空open_short 3.平多close_long 4.平空close_short||
amount|y|string|委托数量||
dealAmount|y|string|已成交数量||
avgPrice|y|string|平均成交价格||
price|y|string|委托价格||
orderSize|y|string|委托价值||
status|y|int|委托状态：0 等待成交 1 部分成交 2 已经成交 -1 已经撤销||
systemType|y|long|委托类型：全部、10:限价 11:市价 13:强平单 14:爆仓单 15：穿仓 16：强减||
direction|y|long|触发方向，greater大于，less小于||
profit|y|string|该笔订单成交后对应的盈亏: 正表示盈利,负表示亏损||
fee|y|string|手续费||
modifyDate|y|Long|最后操作时间||
createdDate|y|date|创建时间||


### 当前持仓
#### GET /api/v1/perpetual/admin/{contractCode}/position

请求参数：

#### 请求参数：

##### 路径参数
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
contractCode|y|string|合约code||

##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
contractCode|n|string|合约code||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|
userIds|n|List<long>|用户id||

```json
{
    "code": 200,
    "data": {
        "rows": [
            {
                "amount": "1.0000000000000000",
                "base": "usdt",
                "baseDisplayName": "USDT",
                "brokerPrice": "100000000.0000000000000000",
                "closingAmount": "0E-16",
                "contractCode": "btcusdt",
                "contractCodeDisplayName": "BTCUSDT",
                "createdDate": 1608185501000,
                "env": 0,
                "fee": "0E-16",
                "gear": "",
                "indexBase": "btc",
                "indexBaseDisplayName": "BTC",
                "lever": "125.0000000000000000",
                "liqudatePrice": "100000000.0000000000000000",
                "maintenanceMargin": "0.9200000000000000",
                "markPrice": "",
                "minQuoteDigit": 0,
                "minTradeDigit": 0,
                "openMaginRate": "",
                "openMargin": "1.8400000000000000",
                "orderAmount": "0E-16",
                "preLiqudatePrice": "0E-16",
                "price": "23000.0000000000000000",
                "profitRate": "",
                "quote": "usdt",
                "quoteDisplayName": "USDT",
                "realizedSurplus": "0E-16",
                "risk": "",
                "side": "short",
                "size": "230.0000000000000000",
                "type": 0,
                "unRealizedSurplus": "-1.9787",
                "userId": 20100195
            }
        ],
        "total": 3
    },
    "msg": "success"
}

```

#### 返回：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
env|y|int|0-实盘/1-模拟盘||
createdDate|y|int|创建时间||
orderAmount|y|int|订单数量||
userId|y|long|uid||
contractCode|y|string|合约code||
base|y|string|基础币||
quote|y|string|计价币||
indexBase|y|string|指数币||
type|y|int|0全仓，1逐仓||
side|y|string|仓位类型，long多，short空||
lever|y|string|杠杆||
gear|y|string|风险限额||
closingAmount|y|string|正在平仓的数量||
realizedSurplus|y|string|已实现盈亏||
unRealizedSurplus|y|string|未实现盈亏||
price|y|string|成交均价||
amount|y|string|持仓数量||
openMargin|y|string|持仓保证金||
maintenanceMargin|y|string|维持保证金||
liqudatePrice|y|string|强平价||
size|y|string|强平价||
brokerPrice|y|string|爆仓价||

### 修改资金费率
#### PUT /api/v1/perpetual/admin/{contractCode}/fee-rate

请求参数：

#### 请求参数：

参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
value|y|doublue|资金费率值||绝对值<0.005

##### 路径参数
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
contractCode|y|string|合约code||

##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||


```json
{
    "code": 200,
    "msg": "success"
}

```



### 保证金账户查询
#### GET  /api/v1/perpetual/admin/insurance-account/bills
请求参数：
#### 请求参数：
##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
AccessKeyId|y|string|访问key||
SignatureVersion|y|string|版本||
SignatureMethod|y|string|签名方法||HmacSHA256
Signature|y|string|签名||
Timestamp|y|string|时间戳||
startDate|n|long|开始时间||
endDate|n|long|结束时间||
contractCode|n|string|合约code||
page|n|integer|页数|1|
pageSize|n|integer|每页数量|20|

```json
{
    "bills": [
        {
            "amount": "1",
            "balance": "36157.9579",
            "bizType": "",
            "brokerId": 0,
            "contractCode": "ethusdt",
            "contractType": "",
            "createdDate": 1715200522733,
            "currencyCode": "usdt",
            "currencyCodeDisplayName": "USDT",
            "currencyPairDTO": null,
            "dealMarket": 0,
            "deductedFee": "0.000000",
            "detailSide": "close_long",
            "dualPosition": 1,
            "env": 0,
            "fee": "0.000000",
            "feeCurrencyCode": "",
            "lever": 0,
            "liquidationDate": 0,
            "makerTaker": 0,
            "marginDigit": 0,
            "positionType": 0,
            "price": "2943.4000",
            "profit": "0.0887",
            "referId": 3284410737869312,
            "selectedMode": 0,
            "size": "29.434",
            "type": 48,
            "typeDesc": ""
        }
    ],
    "paginate": {
        "page": 1,
        "pageSize": 10,
        "total": 520,
        "totalPage": 52
    },
    "total": ""
}
```
#### 返回：
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
id|y|number|订单id||
amount|y|string|成交数量||
balance|y|string|余额||
bizType|y|string|类型||
brokerId|y|string|业务方ID||
contractCode|y|string|合约code||
contractType|y|string|合约类型||
createDate|y|string|创建时间||
currencyCode|y|string|币种||
currencyCodeDisplayName|y|string|币种显示名||
dealMarket|y|number|0：普通单   1：带单   2：跟单||
deductedFee|y|string|已减免的手续费费用||
detailSide|y|string|交易类型 1.开多open_long 2.开空open_short 3.平多close_long 4.平空close_short||
dualPosition|y|number|持仓模式||
env|y|int|0-实盘/1-模拟盘||
fee|y|string|手续费||
feeCurrencyCode|y|string|手续费对应的币种，可能是币种，可能是点卡||
lever|y|number|杠杆||
liquidationDate|y|number|清算时间||
makerTaker|y|number|1: maker 2: taker||
marginDigit|y|number|保证金精度||
positionType|y|number|持仓类型||
price|y|string|成交价格||
profit|y|string|收益||
referId|y|number|账单关联记录 id||
selectedMode|y|number|||
positionType|y|number|持仓类型||
refUserId|y|number|关联用户id||
size|y|string|成交价值||
type|y|number|类型（48.强平注入 49.穿仓亏损）||
typeDesc|y|string|类型描述||
currencyPairDTO|y|object|||
--id|y|number|id||
--biz|y|string|业务分类:perpetual,regular||
--indexBase|n|string|指数基础货币,如BTC、ETH||
--base|n|string|基础货币名,如BTC、FBTC||
--quote|n|string|计价货币名，USD,CNY,USDT||
--quoteDisplayName|n|string|计价币转换成的名称||
--baseDisplayName|n|string|计价币转换成的名称||
--indexBaseDisplayName|n|string|指数币||
--pairCode|n|string|是Base和Quote之间的组合，如P_BTC_USDT，R_BTC_USDT||
--insuranceAccount|n|number|保险金账号||
--minTradeUnit|n|number|最小交易单位||
--unitAmount|n|number|一张合约对应的计价货币面值，默认1||
--minOrderAmount|n|number|每笔最小挂单张数||
--maxOrderAmount|n|number|每笔最大挂单张数||
--maxOrders|n|integer|单人最大挂单订单数||
--minTradeDigit|n|integer|基础货币最小交易小数位||
--minQuoteDigit|n|integer|计价货币最小交易小数位||
--maxLevel|n|number|最大杠杆，全仓使用最大杠杆||
--type|n|string|合约类型，可选值：week,nextweek,month,quarter（分别表示周、次周、月、季度），空字符串表示永续合约||
--preLiqudatePriceThreshold|n|number|预强平价格阈值，计算方式：强平价格 + (开仓价格 - 强平价格) * 阈值||
--premiumMinRange|n|number|溢价指数阈值下限||
--premiumMaxRange|n|number|溢价指数阈值上限||
--premiumDepth|n|number|溢价指数加权买卖价的取值深度，单位为基础货币||
--fundingCeiling|n|number|绝对的资金费率上限，计算方式：起始保证金 - 维持保证金 的 百分比||
--minAmount|n|number|最低交易档位，单位是基础货币||
--diffAmount|n|number|单位是base，表示每档的差值||
--maxAmount|n|number|单位是base，表示最高档位||
--maintainRate|n|number|维持保证金费率，每升一档都增加一个维持保证金费率||
--liquidationHour|n|integer|清算周期，以小时为单位，从北京中午12:00点开始计算||
--dkFee|n|integer|点卡抵扣手续费，0表示不使用，1表示使用||
--env|n|integer|是否测试盘，0表示线上盘，1表示测试盘||
--online|n|integer|状态，0表示下线，1表示预发，2表示线上可用||
--direction|n|integer|方向，0表示正向，1表示反向||
--interestRate|n|number|利率，用于计算资金费率||
--createdDate|n|string|创建时间，格式为YYYY-MM-DD HH:MM:SS||
--modifyDate|n|string|更新时间，格式为YYYY-MM-DD HH:MM:SS||
--marketPriceDigit|n|integer|标记价格最小单位，表示价格的精度（小数点后的位数）||
--marginDigit|n|integer|保证金精度，表示保证金的精度（小数点后的位数）||
--positionRiskRemind|n|string|持仓风险率提醒，用于提示用户持仓风险率的阈值||
--sort|n|integer|排序||
--openTradeTime|n|string|开盘时间，格式为YYYY-MM-DD HH:MM:SS||
--feeAccount|n|number|手续费账号，用于记录手续费收支的账户||



### websocket订阅预订单

#### 请求参数：
##### Query
参数名称|是否必须|类型|描述|默认值|取值范围
------------- | ------------- |  ------------- | ------------- |  ------------- | -------------
event|y|string|订阅的事件||
params|y|object|订阅入参|||
biz|y|string|业务参数||
type|y|string|数据类型||
zip|y|boolean|是否压缩||
contractCode|y|string|合约代码||
serialize|y|boolean|是否序列化||


```json
#订阅请求
{
    "event": "subscribe",
    "params": {
        "biz": "perpetual",
        "type": "pre_order",
        "zip": false,
        "contractCode": "BTCUSDT",
        "serialize": false
    }
}
#订阅成功
{
    "biz": "perpetual",
    "data": {
        "result": true #订阅成功 ，false 为订阅失败
    },
    "channel": "subscribe",
    "type": "pre_order",
    "env": 0,
    "contractCode": "BTCUSDT"
}
```
#### 订阅推送数据
| 序号  | 字段名                | 类型     | 是否必须 | 描述                 |
|------|-----------------------|---------|---------|----------------------|
| 1    | id                    | int64   | y       | 订单唯一标识符        |
| 2    | contractCode          | string  | y       | 合约代码              |
| 3    | contractDirection     | int32   | y       | 合约方向              |
| 4    | base                  | string  | y       | 基础货币              |
| 5    | quote                 | string  | y       | 计价货币名，USD,CNY,USDT|
| 6    | userId                | int64   | y       | 用户ID               |
| 7    | side                  | string  | y       | 仓位类型，long多，short空   |
| 8    | detailSide            | string  | y       | 交易类型 1.开多open_long 2.开空open_short 3.平多close_long 4.平空close_short |
| 9    | clazz                 | int32   | y       | 0:下单 1:撤单 |
| 10   | mustMaker             | int32   | y       | 被动委托：0:不care 1:只做maker，如何是taker就撤单            |
| 11   | amount                | string  | y       | 委托数量              |
| 12   | price                 | string  | y       | 用户订单委托或者破产价格             |
| 13   | avgPrice              | string  | y       | 平均成交价格             |
| 14   | dealAmount            | string  | y       | 已成交数量            |
| 15   | orderSize             | string  | y       | 订单大小              |
| 16   | dealSize              | string  | y       | 已成交大小            |
| 17   | openMargin            | string  | y       | 开仓保证金             |
| 18   | extraMargin           | string  | y       | 额外价格偏移保证金             |
| 19   | avgMargin             | string  | y       | 每张合约摊到的保证金             |
| 20   | systemType            | int32   | y       | 10:限价 11:市价 13:强平单 14:爆仓单              |
| 21   | profit                | string  | y       | 该笔订单成交后对应的盈亏: 正表示盈利,负表示亏损|
| 22   | fee                   | string  | y       | 该笔订单成交后交的手续费: 正表示得手续费,负表示付手续费|
| 23   | reason                | int32   | y       | 该笔订单取消的理由，0是默认值，没有理由 |
| 24   | createdDate           | int64   | y       | 创建日期              |
| 25   | triggerPrice          | string  | y       | 触发价格              |
| 26   | indexBase             | string  | y       | 指数基准              |
| 27   | direction             | int32   | y       | 方向                 |
| 28   | stopLimitType         | int32   | y       | 止损类型               |
| 29   | lever                 | int32   | y       | 杠杆                 |
| 30   | orderPriceType        | int32   | y       | 订单价格类型            |
| 31   | triggerBy             | string  | y       | 触发者                |
| 32   | refConditionOrderId   | int64   | y       | 关联的条件单id          |
| 33   | marginDigit           | int32   | y       | 保证金数字位            |
| 34   | positionType          | int32   | y       | 0全仓, 1逐仓, 2未知֪               |
| 35   | status                | int32   | y       |  等待成交 1 部分成交 2 已经成交 -1 已经撤销                |
| 36   | stopLoss              | (message)| y       | 止损条件               |
| 37   | stopProfit            | (message)| y       | 止盈条件               |
| 38   | modifyDate            | int64   | y       | 修改日期               |
| 42   | baseDisplayName       | string  | y       | 计价币转换成的名称       |
| 43   | quoteDisplayName      | string  | y       | 计价币转换成的名称         |
| 44   | contractCodeDisplayName | string | y       | 合约代码显示名称       |
| 45   | indexBaseDisplayName  | string  | y       | 指数基准显示名称         |
| 46   | env                   | int64   | y       | 环境                 |
| 47   | dualPosition          | int32   | y       | 持仓模式，0-单向持仓/1-双向持仓            |
| 48   | reduceOnly            | int32   | y       | 是否只减仓,0-否/1-是                |
| 49   | orderType             | int32   | y       | 0：普通单，1：止盈止损，2：计划委托 |
| 50   | growthType            | int32   | y       | 持仓增长类型：1：开仓单   2：平仓单   0：无法确定               |
| 51   | brokerId              | int32   | y       | 经纪人ID              |
| 52   | dealMarket            | int32   | y       | 成交市场               |
| 53   | deductedFee           | string  | y       | 已减免手续费            |
| 54   | mode                  | int32   | y       | 持仓模式  0：合仓  1：分仓                |
| 56   | positionId            | int64   | y       | 持仓ID                |
| 57   | traderNickname        | string  | y       | 交易员昵称              |
| 58   | traderPhoto           | string  | y       | 交易员头像              |
| 59   | isNftPhoto            | int32   | y       | 是否NFT头像            |
| 60   | liquidatePrice        | string  | y       | 强平价格               |
| 61   | orderFee              | string  | y       | 订单手续费              |
| 62   | liquidationDate       | int64   | y       | 强平日期               |
| 63   | contractType          | string  | y       | 合约类型               |
| 64   | bizType               | string  | y       | 业务类型               |
| 65   | ioc                   | int32   | y       | IOC (Immediately or Cancel) 订单若不能立即成交则未成交的部分立即取消。                  |


```json
#订阅响应数据
{
    "biz": "perpetual",
    "data": {
        "reason": 0,
        "orderType": 0,
        "contractType": "perpetual",
        "fee": "0.000000",
        "ratioDeductedFee": 0,
        "quoteDisplayName": "USDT",
        "liquidationDate": 1715415600000,
        "matchStatus": 0,
        "quote": "usdt",
        "price": "0",
        "indexBase": "btc",
        "growthType": 0,
        "dealAmount": "0",
        "showAmount": 1.00000000000000000000000000000000,
        "contractDirection": 0,
        "deductedFee": 0,
        "availableDeductedFee": 0,
        "indexBaseDisplayName": "BTC",
        "size": "0",
        "reduceOnly": 0,
        "unitAmount": 0.0010000000000000,
        "orderFrom": 0,
        "status": 0,
        "brokerSize": 0,
        "extraMargin": "0",
        "bizType": "perpetual",
        "avgPrice": "0.00",
        "marginDigit": 6,
        "orderFee": "0.000000",
        "dualPosition": 1,
        "relationOrderId": 0,
        "baseDisplayName": "USDT",
        "marketPriceDigit": 2,
        "contractCodeDisplayName": "BTCUSDT",
        "systemType": 11,
        "dealMarket": 0,
        "profit": "0.000000",
        "avgFee": 0,
        "amount": "1",
        "brokerId": 1,
        "side": "long",
        "openMargin": "0",
        "dealSize": "0",
        "avgMargin": "0",
        "env": 0,
        "mustMaker": 0,
        "userId": 100300231,
        "detailSide": "open_long",
        "createdDate": 1715407263681,
        "ioc": 0,
        "clazz": 0,
        "contractCode": "btcusdt",
        "base": "usdt"
    },
    "type": "pre_order",
    "env": 0,
    "contractCode": "btcusdt",
    "timestamp": 1715407263882
}
```

#### python demo 
```python
import websocket
import json

def on_message(ws, message):
    print("Received message:", message)

def on_error(ws, error):
    print("Error:", error)

def on_close(ws):
    print("### Connection closed ###")

def on_open(ws):
    print("### Connection opened ###")
    # 登录
    login_data = {
        "event": "signin",
        "params": {
            "token": "eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJob3Rjb2luIiwidWlkIjoiRUwyK2FISXdPYXJJaXVLSlZEM01qZz09Iiwic291cmNlIjoiTlVqaUVWREJLRndnVVY4K3dQT1FLQT09IiwiaWF0IjoxNzE1MjE5MzkyLCJqdGkiOiI0NzkwNDI3Yy0wZDVmLTQ0NTMtODFhOS1kYzFiNThmYThiNTAiLCJpcCI6IjNRaDFPaVh6WVlYdXkwMnZWWGF5Unc9PSJ9.vhvov4ruhgXVslMvjjueHk3wXquAvLDnLxk9n9AfQ1Q$eyJhbGciOiJIUzI1NiJ9.eyJqdGkiOiJjZWM4ODNjMC1jYWM5LTRiYjEtODlkZS00NzYzZGQ0YzFhYWU0Nzk5OTA0MDEiLCJ1aWQiOiJFTDIrYUhJd09hcklpdUtKVkQzTWpnPT0iLCJpcCI6IjIvSkpaUU9RWXRkS3FIRU9vOFEwQXc9PSIsImRldiI6IkE4b0xOZVJWdkZHb3hMOVBaZWhrcEE9PSIsInN0cyI6MCwiaWF0IjoxNzE1MjE5MzkyLCJleHAiOjE3MTU4MjQxOTIsImlzcyI6Im5ld2V4In0.G18N5u4-uLDyQuNcT7hPgyS7je5PVC6hEfoQneEH3_Y"
        }
    }
    ws.send(json.dumps(login_data))

    # 订阅数据，需要是管理员id 才能订阅
    subscribe_data = {
        "event": "subscribe",
        "params": {
            "biz": "perpetual",
            "type": "pre_order",
            "zip": False,
            "contractCode": "BTCUSDT",
            "serialize": False
        }
    }
    ws.send(json.dumps(subscribe_data))

if __name__ == "__main__":
    websocket.enableTrace(True)
    ws = websocket.WebSocketApp("ws://127.0.0.1:8104/",
                                on_open=on_open,
                                on_message=on_message,
                                on_error=on_error,
                                on_close=on_close)
    ws.run_forever()

