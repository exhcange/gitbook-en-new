# Coingecko dockin

### Coin quotes

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/ticker`

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

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/orderbook`

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
