# BM18 (BestMenger digital securities)

BM18 以太坊智能合约核心代码。

# BM18 Interface

## 工作原理
BM18 Token 必须实现 `verifyTransfer` 方法，这个方法在转账（`transfer`，`transferFrom`）时会被调用。`verifyTransfer` 方法用来判断转账是否允许发生，默认的实现是检查转账双方是否在白名单中，当然也可以有其他实现。

## The BM18 Interface
```
contract BM18 {

    // off-chain document with checksum
    string public documentUrlWithChecksum;

    // transfer, transferFrom must respect the result of verifyTransfer
    function verifyTransfer(address _from, address _to, uint256 _amount) view public returns (bool success);

    // used to create tokens
    function mint(address _investor, uint256 _amount) public returns (bool success);
}
```

# BM18 架构
![BM18 architecture](https://github.com/BestMenger/digital-securities-standard/blob/master/docs/images/bm18-architecture.png)
