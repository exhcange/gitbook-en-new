# Coingecko docking

### Coin quotes

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/ticker`

**Request parameters**

no

**Response parameters**

| Name             | type   | Example                | description                                                               |
| ---------------- | ------ | ---------------------- | ------------------------------------------------------------------------- |
| ticker\_id       | string | BTC\_USDT              | token pair                                                                |
| base\_currency   | string | BTC                    | base currency                                                             |
| target\_currency | string | USDT                   | currency of account                                                       |
| last\_price      | number | 98000.0000000000000000 | last traded price of the base currency based on the given target currency |
| base\_volume     | number | 1.1200                 | 24-hour single side volume of the pair (in base units)                    |
| target\_volume   | number | 99000.0000000000       | 24-hour single side volume of the pair (denominated currency units)       |
| bid              | number | 97000                  | Current highest buy price                                                 |
| ask              | number | 98000                  | Current high and low order price                                          |
| high             | number | 98000                  | Rolling 24-hour highest trading price                                     |
| low              | number | 98000                  | Rolling 24-hour lowest trading price                                      |

**Sample response**

{% tabs %}
{% tab title="200" %}
```json
{
    "ETH_USDT": {
        "ticker_id": "ETH_USDT",
        "base_currency": "ETH",
        "target_currency": "USDT",
        "last_price": 238.2000000000000000,
        "base_volume": 0.0000,
        "target_volume": 0.000000,
        "bid": 0,
        "ask": 0,
        "high": 238.2,
        "low": 238.2
    },
    "BCH_USDT": {
        "ticker_id": "BCH_USDT",
        "base_currency": "BCH",
        "target_currency": "USDT",
        "last_price": 1.0000000000000000,
        "base_volume": 0.000000,
        "target_volume": 0E-10,
        "bid": 0,
        "ask": 0,
        "high": 1,
        "low": 1
    }
}
```
{% endtab %}
{% endtabs %}

### Disc data

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/orderbook`

**Request parameters**

| Name       | Type           | Description |
| ---------- | -------------- | ----------- |
| ticker\_id | string         | token pair  |
| depth      | integer(int32) | Order depth |

**Response parameters**

| Name       | type           | Example                     | description                                                              |
| ---------- | -------------- | --------------------------- | ------------------------------------------------------------------------ |
| ticker\_id | string         | BTC\_USDT                   | token pair                                                               |
| timestamp  | integer(int64) | 1766976278000               | Unix timestamp, in milliseconds, of the last update                      |
| bids       | array          | \[\[1000,0.1], \[2000,0.2]] | An array with two elements, the bid and quantity for each purchase       |
| asks       | array          | \[\[2000,0.2], \[3000,0.3]] | An array of two elements with the price and quantity for each sell order |

**Sample response**

{% tabs %}
{% tab title="200" %}
```json
{
    "ticker_id": "BTC_USDT",
    "timestamp": 1766976278000,
    "bids": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ],
    "asks": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ]
}
```
{% endtab %}
{% endtabs %}

### contracts

<mark style="color:blue;">`GET`</mark>` ``https://futuresopenapi.xxx.xx/pub/coingecko/contracts`&#x20;

**Request parameters**

| Name       | Type   | Description                                |
| ---------- | ------ | ------------------------------------------ |
| ticker\_id | string | contract\_name【Optional】, eg. "E-BTC-USDT" |

**Response parameters**

| ticker\_id                     | string  | E-BTC-USDT    | Identifier of a ticker with delimiter to separate base/target, eg. BTC-PERP     |
| ------------------------------ | ------- | ------------- | ------------------------------------------------------------------------------- |
| base\_currency                 | string  | BTC           | Symbol/currency code of base pair, eg. BTC                                      |
| target\_currency               | string  | USDT          | Symbol/currency code of target pair, eg. ETH                                    |
| last\_price                    | decimal | 92000.36      | Last transacted price of base currency based on given target currency           |
| base\_volume                   | decimal | 0.2           | 24 hour trading single sided volume in base pair volume                         |
| target\_volume                 | decimal | 0.2           | 24 hour trading single sided volume in target pair volume                       |
| bid                            | decimal | 92000.36      | Current highest bid price                                                       |
| ask                            | decimal | 92000.36      | Current lowest ask price                                                        |
| high                           | decimal | 92100.36      | Rolling 24-hours highest transaction price                                      |
| low                            | decimal | 91900.36      | Rolling 24-hours lowest transaction price                                       |
| product\_type                  | string  | Perpetual     | What product is this? Futures, Perpetual, Options?                              |
| open\_interest                 | decimal | 1116.3655     | The open interest in the last 24 hours in contracts (in base currency)          |
| open\_interest\_usd            | decimal | 102573030.064 | The open interest in the last 24 hours in contracts (in USD)                    |
| index\_price                   | decimal | 92100.36      | Underlying index price                                                          |
| index\_name                    | string  | BTC-USDT      | Name of the underlying index if any                                             |
| index\_currency                | string  | BTC           | Underlying currency for index                                                   |
| start\_timestamp               | integer | 0             | Starting of this derivative product (relevant for expirable futures or options) |
| end\_timestamp                 | integer | 0             | Ending of this derivative product (relevant for expirable futures or options)   |
| funding\_rate                  | decimal | 0             | Current funding rate                                                            |
| next\_funding\_rate            | decimal | 0             | Upcoming predicted funding rate                                                 |
| next\_funding\_rate\_timestamp | integer | 1768291200000 | Timestamp of the next funding rate change                                       |
| contract\_type                 | string  | Vanilla       | Describes the type of contract - Vanilla, Inverse or Quanto?                    |
| contract\_price\_currency      | string  | USDT          | Describes the currency which the contract is priced in.                         |
| contract\_price                | decimal | 92100.36      | Describes the price per contract. (If not same as last price)                   |
| timestamp                      | integer | 1768289995029 | query data timestamp                                                            |

**Sample request**

```
https://futuresopenapi.xxx.xx/pub/coingecko/contracts?ticker_id=E-BTC-USDT
```

**Sample response**

```json
{
    "code": "0",
    "msg": "success",
    "data": {
        "contracts": [
            {
                "ticker_id": "E-BTC-USDT",
                "base_currency": "BTC",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": 9.8E+4,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 1116.3655,
                "open_interest_usd": 102573030.06495740245,
                "index_price": 0,
                "index_name": "BTC-USDT",
                "index_currency": "BTC",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            },
            {
                "ticker_id": "E-ETH-USDT",
                "base_currency": "ETH",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": null,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 3004.17,
                "open_interest_usd": 9383427.795980901,
                "index_price": 0,
                "index_name": "ETH-USDT",
                "index_currency": "ETH",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            }
        ]
    }
}

```

### contract-orderbook

<mark style="color:blue;">`GET`</mark>` ``https://futuresopenapi.xxx.xx/pub/coingecko/orderbook`&#x20;

**Request parameters**

| Name       | Type           | Description                     |
| ---------- | -------------- | ------------------------------- |
| ticker\_id | string         | contract\_name, e. "E-BTC-USDT" |
| depth      | integer(int32) | Order depth                     |

**Response parameters**

| ticker\_id | string      |   E-BTC-USDT                                           | A pair such as "BTC-PERP", with delimiter between different cryptoassets        |
| ---------- | ----------- | ------------------------------------------------------ | ------------------------------------------------------------------------------- |
| timestamp  |   timestamp |   1768289995029                                        | Unix timestamp in milliseconds for when the last updated time occurred.         |
| bids       |   decimal   | <p>[<br>[98000,0.469387],<br>[98500.93,0.1]<br>]</p>   | An array containing 2 elements. The offer price and quantity for each bid order |
| asks       |   decimal   | <p>[<br>[97000,0.46938777],<br>[96500.93,0.1]<br>]</p> | An array containing 2 elements. The ask price and quantity for each ask order   |

**Sample request**

```
https://futuresopenapi.xxx.xx/pub/coingecko/orderbook?ticker_id=E-BTC-USDT&dept=100
```

**Sample response**

```json
{
    "code": "0",
    "msg": "success",
    "data": {
        "orderbook": {
            "ticker_id": "E-BTC-USDT",
            "asks": [
                [
                    98000,
                    0.46938777
                ],
                [
                    98500.93,
                    0.1
                ],
                [
                    100000,
                    3
                ],
                [
                    1800000,
                    1.111
                ],
                [
                    2000000,
                    1
                ]
            ],
            "bids": [
                [
                    97000,
                    0.46938777
                ],
                [
                    96500.93,
                    0.1
                ],
                [
                    96000,
                    3
                ],
                [
                    95500,
                    1.111
                ],
                [
                    95000,
                    1
                ]
            ],
            "timestamp": 1768289995029
        },
        "ticker_id": "E-BTC-USDT"
    }
}
```







