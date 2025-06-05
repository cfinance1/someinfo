# MarketingPool

## Overview

#### License: GPL-3.0

```solidity
contract MarketingPool is AccessControlUpgradeable
```


## State variables info

### feeTotal (0x84767996)

```solidity
mapping(address => uint256) feeTotal
```


### builderClaimed (0x3ec13569)

```solidity
mapping(address => uint256) builderClaimed
```


### platformClaimed (0x69da8f4c)

```solidity
mapping(address => uint256) platformClaimed
```


### platformWallet (0xfa2af9da)

```solidity
address platformWallet
```


### MLaunchPad (0xfe92dafc)

```solidity
address MLaunchPad
```


## Modifiers info

### onlyMananger

```solidity
modifier onlyMananger()
```


## Functions info

### receive

```solidity
receive() external payable
```


### constructor

```solidity
constructor()
```


### initialize (0xc4d66de8)

```solidity
function initialize(address wallet_) public initializer
```

