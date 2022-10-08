# Frontend library for PaywithTerra

*The full source code will be published later*

## Connect
1. Add styles before the `</head>`
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/paywithterra/frontend@0.0.x/dist/css/app.css">
```
2. Add launch script `window.payWithTerra.start` with your configuration (see full example below)
3. Add script before the `</body>`
```html
<script async src="https://cdn.jsdelivr.net/gh/paywithterra/frontend@0.0.x/dist/js/app.js"></script>
```
## Frontend API
### Events
```javascript
[window] "payWithTerra-destroy-app"
[window] "payWithTerra-ready"
```

### Methods
```javascript
window.payWithTerra.start({
  showTestnetWarning: false,
  //chainId: "phoenix-1", // "pisco-1" or "phoenix-1"
  networkName: "testnet", // "mainnet" or "testnet"
  merchantAddress: "terra14wvwnyjgsljobxdzjGo6pkQazrhtlp4zMwu6tb",
  merchantEndpoint: "http://yourwebsite.com/payment-callback",
  memo: "Order-1",
  total: 0.01, // Amount in domestic currency (for display only)
  currency: "USD", // Domestic currency (for display only)
  denom: "ibc/B3504E092456BA618CC28AC671A71FB08C6CA0FD0BE7C8A5B5A3E2DD933CC9E4",
  amount: 10000, // Amount in denom (for transaction create)
  finderTxUrl: "https://finder.terra.money/pisco-1/tx/",

  onClose: (hash = null) => {
      console.log("onClose", hash);
  },
  onSuccess: (hash) => {
      console.log("onSuccess", hash);
  }
})
          
window.payWithTerra.close()
```

### Server Response (as expected)
```
JSON
{
    "redirectUrl": string
    "closeUrl": string
}
```
