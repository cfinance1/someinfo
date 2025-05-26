# BottomPool

## Overview

#### License: GPL-3.0

```solidity
contract BottomPool is AccessControlUpgradeable
```


## Events info

### EventSellMEToken

```solidity
event EventSellMEToken(address indexed meToken, address indexed recipient, uint256 costMETokenAmount, uint256 buyTokenAmount)
```

出售MEMEtoken，购买sCSM


Parameters:

| Name              | Type    | Description |
| :---------------- | :------ | :---------- |
| meToken           | address | MEME地址      |
| recipient         | address | 接受sCSM的地址   |
| costMETokenAmount | uint256 | 消耗MEME数量    |
| buyTokenAmount    | uint256 | 购买到的sCSM的数量 |

### EventBottomBuyBack

```solidity
event EventBottomBuyBack(address indexed meToken, uint256 backMETokenAmount, uint256 buyTokenAmount, uint256 newTokenBalance, uint256 newGonsBalance)
```

MEME的transfer触发手续费分配的拖底池回购


Parameters:

| Name              | Type    | Description   |
| :---------------- | :------ | :------------ |
| meToken           | address | MEME地址        |
| backMETokenAmount | uint256 | 用来回购的MEME数量   |
| buyTokenAmount    | uint256 | 买到的token数量    |
| newTokenBalance   | uint256 | 拖底池的CSM本金数量   |
| newGonsBalance    | uint256 | 拖底池的sCSM的gons |

## Constants info

### UID (0x5cc99e35)

```solidity
uint256 constant UID = 1
```


## State variables info

### UNISWAPV2ROUTER (0xa8b62f7b)

```solidity
contract IUniswapV2Router immutable UNISWAPV2ROUTER
```


### UNISWAPV2FACTORY (0x17f30e43)

```solidity
contract IUniswapV2Factory immutable UNISWAPV2FACTORY
```


### WBNB (0x8dd95002)

```solidity
address immutable WBNB
```


### USDT (0xc54e44eb)

```solidity
address immutable USDT
```


### TOKEN (0x82bfefc8)

```solidity
address immutable TOKEN
```


### sTOKEN (0x726ed7c4)

```solidity
address immutable sTOKEN
```


### STAKING (0x97610f30)

```solidity
address immutable STAKING
```


### METoken (0xad577be3)

```solidity
contract IERC20Token METoken
```


### tokenPrincipal (0xc06107d7)

```solidity
mapping(address => uint256) tokenPrincipal
```


### gonsPrincipal (0x4364a38f)

```solidity
mapping(address => uint256) gonsPrincipal
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


## Functions info

### constructor

```solidity
constructor(
    address WBNB_,
    address USDT_,
    address TOKEN_,
    address sTOKEN_,
    address STAKING_,
    address uniswapV2Router_
)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### sellMEToken (0x9d90e94a)

```solidity
function sellMEToken(
    address meToken_,
    uint256 amount_,
    address recipient_
) external
```

出售MEME


Parameters:

| Name       | Type    | Description |
| :--------- | :------ | :---------- |
| meToken_   | address | MEME地址      |
| amount_    | uint256 | meme的数量     |
| recipient_ | address | 接收sCSM的地址   |

### getMETokenPrice (0xe132a9d7)

```solidity
function getMETokenPrice(
    address meToken_
) external view returns (uint256 price_)
```

MEME的价格


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEME地址      |


Return values:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| price_ | uint256 | 1个MEME购买到的token的数量 |

### getMETokenRedeemCount (0xc3f4ad06)

```solidity
function getMETokenRedeemCount(
    address meToken_,
    uint256 metTokenAmount_
) external view returns (uint256 price_)
```

MEME兑换到的sToken的数量


Parameters:

| Name            | Type    | Description |
| :-------------- | :------ | :---------- |
| meToken_        | address | MEME地址      |
| metTokenAmount_ | uint256 | MEME的数量     |


Return values:

| Name   | Type    | Description   |
| :----- | :------ | :------------ |
| price_ | uint256 | 兑换到的sToken的数量 |

### buyBack (0xd1b8df22)

```solidity
function buyBack(address meToken_, uint256 amount_) external
```


### transferTokenOut (0xc15ded67)

```solidity
function transferTokenOut(
    address token_,
    address addr_,
    uint256 amount
) external onlyManager
```

