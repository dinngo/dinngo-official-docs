# Public RESTful API for Dinngo

## General

- The Dinngo API endpoint: **https://exchange-metadata-api.dinngo.co**

- HTTP `GET` Parameters must be `query string`

- HTTP `POST` ,  `PUT` and  `DELETE` Parameters will write in `request body` and content type must be `application/json` .

- If error occurred and the response pattern will be

  ```json
  {
    "code": "",
    "message": "",
  }
  ```



## API Guide

### API List

- Trade Pair
- Server Time
- Trading History
- Order Book

### API

#### Trade Pair

Get listing trade pairs in market.

```http
[GET] /api/v1/market
```

**Parametes: ** None

**Response:**

```json
{
  "symbols": ["DGOETH","BATETH","BATPAX"]
}
```



#### Server Time

Get Server time.

```http
[GET] /api/v1/time
```

**Parameters:** None

**Response:**

```json
{
  "serverTime": 1499865549600
}
```



#### Trading History

Get trading history.

```http
[GET] /api/v1/trading_history
```

**Parametes: **

| Name     | Type   | Required | Description                            |
| -------- | ------ | -------- | -------------------------------------- |
| symbol   | string | Yes      | Which trade pair information you want. |
| page     | int    | No       | Page index. Default: 1                 |
| per_page | int    | No       | Page size. Default: 500                |

**Response:**

```json
{
  "trades": [
    {
    	"price": "0.01",
	    "qty": "100",
  	  "time": 1499865549600,
    	"isBuy": true
  	}
  ]
}
```



#### Order Book

Get the orders of the specified market.

```http
[GET] /api/v1/orderbook
```

**Parameters:**

| Name     | Type   | Required | Description                            |
| -------- | ------ | -------- | -------------------------------------- |
| symbol   | string | Yes      | Which trade pair information you want. |
| page     | int    | No       | Page index. Default: 1                 |
| per_page | int    | No       | Page size. Default: 500                |

**Response:**

```json
{
  "orders": {
    "bids":[
      ["0.1", "100"] // price, qty
    ],
    "asks":[
      ["0.3","200"] // price, qty
    ]
  }
}
```



### Error

- HTTP `403` is forbidden, because you don't have permsion to access the API.
- HTTP `404` is API not found, please check your API path.
