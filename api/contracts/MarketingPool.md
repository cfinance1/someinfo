# MarketingPool

## Overview

#### License: GPL-3.0

```solidity
contract MarketingPool is AccessControlUpgradeable
```


## Events info

### EventClaimToPlatform

```solidity
event EventClaimToPlatform(address indexed meToken, address user, uint256 feeMax, uint256 feeClaimable)
```


### EventClaimToBuilder

```solidity
event EventClaimToBuilder(address indexed meToken, address user, uint256 feeMax, uint256 feeClaimable)
```


### EventClaimReferrerFee

```solidity
event EventClaimReferrerFee(address indexed meToken, address user, uint256 amountMEME, uint256 amountFToken)
```


### EventReceiveFeeFromSubscribe

```solidity
event EventReceiveFeeFromSubscribe(address indexed meToken, uint256 amountNative, uint256 feeTotal)
```


### EventReceiveFeeFromToken

```solidity
event EventReceiveFeeFromToken(address indexed meToken, uint256 amountMEME, uint256 amountNative, uint256 feeTotal)
```


### EventRecordReferrerFee

```solidity
event EventRecordReferrerFee(address indexed meToken, address referrer, uint256 amountMEME)
```


## State variables info

### UNISWAPV2ROUTER (0xa8b62f7b)

```solidity
contract IUniswapV2Router immutable UNISWAPV2ROUTER
```


### WBNB (0x8dd95002)

```solidity
address immutable WBNB
```


### FTOKEN (0x976fe91a)

```solidity
address immutable FTOKEN
```


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


### referrerFee (0x9e1e96fe)

```solidity
mapping(address => mapping(address => uint256)) referrerFee
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
constructor(address WBNB_, address FTOKEN_, address uniswapV2Router_)
```


### initialize (0xc4d66de8)

```solidity
function initialize(address wallet_) public initializer
```


### getPlatformClaimable (0x0f764a20)

```solidity
function getPlatformClaimable(address meToken_) external view returns (uint256)
```


### getBuilderClaimable (0xbca0d703)

```solidity
function getBuilderClaimable(address meToken_) external view returns (uint256)
```


### getClaimableFees (0xebf34712)

```solidity
function getClaimableFees(
    address meToken_,
    address user_
)
    external
    view
    returns (
        uint256 platform_,
        uint256 builder_,
        uint256 referrer_,
        uint256 referrerMEMEAmt_
    )
```

获取可领取手续费


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | token地址     |
| user_    | address | 用户地址        |


Return values:

| Name             | Type    | Description         |
| :--------------- | :------ | :------------------ |
| platform_        | uint256 | 项目方可领取的手续费          |
| builder_         | uint256 | token的owner可领取的手续费  |
| referrer_        | uint256 | 推荐人可领取的手续费(CSF)     |
| referrerMEMEAmt_ | uint256 | 推荐人可领取的手续费(MEME)    |

### claimToPlatform (0x1b883dbf)

```solidity
function claimToPlatform(address meToken_) external
```

项目方领取营销手续费


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | token地址     |

### claimToBuilder (0xee88a17a)

```solidity
function claimToBuilder(address meToken_) external
```

token的owner领取营销手续费


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | token地址     |

### claimReferrerFee (0x8924e40e)

```solidity
function claimReferrerFee(address meToken_) external
```

推荐人领取手续费


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | token地址     |

### receiveFeeFromSubscribe (0x1d0a6771)

```solidity
function receiveFeeFromSubscribe(
    address meToken_,
    uint256 amount_
) external payable
```


### receiveFeeFromToken (0xb7a12db0)

```solidity
function receiveFeeFromToken(address meToken_, uint256 amount_) external
```


### recordReferrerFee (0xc9d36af9)

```solidity
function recordReferrerFee(
    address meToken_,
    address referrer_,
    uint256 amount_
) external
```


### setPlatformWallet (0x8831e9cf)

```solidity
function setPlatformWallet(address wallet_) external onlyMananger
```


### setMLaunchPad (0xa548b80d)

```solidity
function setMLaunchPad(address mlaunchPad_) external onlyMananger
```

