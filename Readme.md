# ERC20 API

This service queries transactions of ERC20 contracts via Infura.io. It will store them in a db and let's you query the transcations by symbol and sender / receiver. 

## Config

```json
{
  "dbpath": "./db/store.sqlite", // path to sqlite file, usually ./db/storeq.sqlite
  "infura": "https://mainnet.infura.io/v3/xxxx", // infura url, the trailing string is your infura project ID
  // array of objects, that represent the tokens to track
  "tokens": [
    {
      "symbol": "WBTC", // symbol used for querying, e.g. WBTC
      "contract": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599", // contract address in hex format. Must be erc20 contract
      "scanFrom": 11471983, // block number, start scanning from here
      "interval" : 100 // amount of blocks that will be queried together. bugg interval = more calls to infura
    }
  ]
}
```

## API

`/:symbol/to/:address` get all transactions of symbol by receiver  
`/:symbol/from/:address` get all transactions of symbol by sender  

`:symbol` is case sensitive
