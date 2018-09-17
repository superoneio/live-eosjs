[![NPM](https://img.shields.io/npm/v/live-eosjs.svg)](https://www.npmjs.org/package/live-eosjs)

# live-eosjs

Javascript SDK for EOS LIVE Dapp

### Usage

* Npm

```js
import live from 'live-eosjs/browser';
console.log(live.isConnect());
```

* Html script tag.

```html
<html>
<head>
    <meta charset="utf-8">
    <script src="./node_modules/live-eosjs/dist/browser.umd.js"></script>
    <script>
        var live = window.WebViewInvoke;
        console.log(live.isConnect());
    </script>
</head>
</html>
```

### Start to use

Firstly, bind some functions which exposed from EOS LIVE.

```js
const EosTokenTransfer = live.bind('eosTokenTransfer');
const PushEosAction = live.bind('pushEosAction');
```

Now, we can use them.

```js
let result = await EosTokenTransfer();
// 'return result'
let result = await PushEosAction();
// 'return result'
```

In addition, you can use them without definition too.

```js
let result = await live.fn.eosTokenTransfer();
// 'return result'
let result = await live.fn.pushEosAction();
// 'return result'
```

### API

#### `live.eosTokenTransfer`

```js
live.eosTokenTransfer(params);
```

##### Parameters

`params` - `Object`:
- `from`: `String`
- `to`: `String`
- `amount`: `String | Number`
- `symbol`: `String`
- `precision`: `Number | String`
- `contract`: `String`
- `memo`: `String` - (optional)

##### Returns

`Object`:

- `status`: `Number`
- `data`: `Object`
    - `transactionId`: `Stirng`
- `message`: `String`

##### Example

```javascript
let result = await live.eosTokenTransfer({
    from: 'superoneioaa',
    to: 'superoneiobb',
    amount: '0.0100',
    tokenName: 'EOS',
    precision: 4,
    contract: 'eosio.token',
    memo: 'test'
});

> {
    status: 200,
    data: { transactionId: '' },
    message: 'success'
}
```



#### `live.getCurrentWallet`

```javascript
live.getCurrentWallet()
```

##### Returns

`Object`:
- `status`: `Number`
- `data`: `Object`
    - `name`: `String`
- `message`: `String`

##### Example

```javascript
let result = await live.getCurrentWallet();

> {
    status: 200,,
    data: {
        name: 'superoneioaa',
    },
    message: 'success'
}
```



#### `live.getEosBalance`

```js
live.getEosBalance(params);
```

##### Parameters

`params` - `Object`:
- `account`: `String`
- `contract`: `String`
- `symbol`: `String`

##### Returns

`Object`:
- `status`: `Number`
- `data`: `Object`
    - `symbol`: `String`
    - `balance`: `String`
    - `contract`: `String`
    - `account`: `String`
- `message`: `String`

##### Example

```javascript
let result = await live.getEosBalance({
    account: 'superoneioaa',
    contract: 'eosio.token',
    symbol: 'EOS'
});

> {
    status: 200,
    data: { "symbol": "EOS", "balance": "["100 EOS"]", "contract": "eosio.token", "account": "superoneioaa" },
    message: 'success'
}
```
