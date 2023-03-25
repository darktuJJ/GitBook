---
description: 与价格数据源进行交互的详细信息：
---

# 综合价格馈送

与价格数据源进行交互：

从合并价格数据源中检索价格的主要功能是：

```
function getPricesUSD(address[] tokenAddresses) view returns (uint256[])
```

该功能接受一个资产地址的数组，并返回以美元计价的价格数组。

### 示例：

以下是一个检索（封装的）比特币和USDC价格的示例。请注意，这里使用的是Polygon资产地址。

{% tabs %}
{% tab title="Solidity" %}
```solidity
interface IConsolidatedPriceFeed {
    function getPricesUSD(address[] memory baseAssets) external view returns (uint256[] memory);
}

address oracle = IConsolidatedPriceFeed(0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7);

address[] memory assets = new address[](2);
assets[0] = 0x1BFD67037B42Cf73acF2047067bd4F2C47D9BfD6; // WBTC
assets[1] = 0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174; // USDC
uint256[] memory prices = oracle.getPricesUSD(assets);
```
{% endtab %}

{% tab title="JavaScript(ethers)" %}
```javascript
const ethers = require("ethers");
const provider = new ethers.providers.JsonRpcProvider("https://polygon-rpc.com");
const oracleAddress = "0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7";
const oracleAbi = [
  "function getPricesUSD(address[] tokenAddresses) view returns (uint256[])"
];

const oracle = new ethers.Contract(oracleAddress, oracleAbi, provider);

const assets = [
  "0x1BFD67037B42Cf73acF2047067bd4F2C47D9BfD6", // WBTC
  "0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174" // USDC
];
const prices = await oracle.getPricesUSD(assets);
console.log(prices);
```
{% endtab %}
{% endtabs %}

## 部署的合约：

目前，综合价格馈送已在以下网络上部署：

* Polygon mainnet: [0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7](https://polygonscan.com/address/0xBa116c6f9e631413847747dF3cF6Dc5cDD1455C7)
