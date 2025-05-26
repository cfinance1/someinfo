# LaunchPad

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract LaunchPad is AccessControlUpgradeable
```


## Enums info

### State

```solidity
enum State {
	 EMPTY,
	 OVER,
	 FORCEOVER,
	 CANCEL
}
```


## Structs info

### LaunchConfig

```solidity
struct LaunchConfig {
	uint256 startSubscribeTime;
	uint256 endSubscribeTime;
	uint256 maxSubscribeNum;
	uint256 subscribeAmount;
	uint256 toStaking;
	uint256 toMarketing;
	uint256 toLp;
	uint256 stakingLockDuration;
	uint256 lpLockDuration;
	uint256 lpUnlockGapNum;
	uint256 lpUnlockGap;
}
```


### StakeInfo

```solidity
struct StakeInfo {
	uint256 tokenAmount;
	uint256 sTOKENGons;
	uint256 startTime;
	uint256 endTime;
}
```


### LpInfo

```solidity
struct LpInfo {
	uint256 lpAmt;
	uint256 startTime;
	uint256 endTime;
}
```


### RetStakeInfo

```solidity
struct RetStakeInfo {
	uint256 tokenAmount;
	uint256 sTOKENGons;
	uint256 sTokenAmount;
	uint256 sTokenUnlockedAmount;
	uint256 startTime;
	uint256 endTime;
}
```


### RetLpInfo

```solidity
struct RetLpInfo {
	uint256 lpAmt;
	uint256 unlockAmt;
	uint256 unlockedAmt;
	uint256 startTime;
	uint256 endTime;
}
```


## Events info

### EventSubscribe

```solidity
event EventSubscribe(address indexed meToken, address indexed user, uint256 amount)
```

认购事件


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| meToken | address | MEME地址      |
| user    | address | 用户地址        |
| amount  | uint256 | 认购数量        |

### EventUnlockStaking

```solidity
event EventUnlockStaking(address indexed meToken, address indexed user, uint256 amount)
```

用户解锁staking事件


Parameters:

| Name    | Type    | Description |
| :------ | :------ | :---------- |
| meToken | address | MEME地址      |
| user    | address | 用户地址        |
| amount  | uint256 | 用户拿到sCSM的数量 |

### EventUnlockLp

```solidity
event EventUnlockLp(address indexed meToken, address indexed user, uint256 amountLp, uint256 amountETH, uint256 amountMEToken, uint256 unlockLpAmt)
```

用户解锁LP事件


Parameters:

| Name          | Type    | Description   |
| :------------ | :------ | :------------ |
| meToken       | address | MEME地址        |
| user          | address | 用户地址          |
| amountLp      | uint256 | 移除的LP数量       |
| amountETH     | uint256 | 移除后返还的eth数量   |
| amountMEToken | uint256 | 移除后返还的MEME数量  |
| unlockLpAmt   | uint256 | 用户已解锁LP数量     |

### EventSubscribeCompleteInfo

```solidity
event EventSubscribeCompleteInfo(address indexed meToken, uint256 num, uint256 stakeAmount, uint256 marketAmount, uint256 lpAmount)
```

认购结束事件，记录完成资金操作后的资金信息


Parameters:

| Name         | Type    | Description      |
| :----------- | :------ | :--------------- |
| meToken      | address | MEME地址           |
| num          | uint256 | 认购的用户数量          |
| stakeAmount  | uint256 | 质押的CSM的数量        |
| marketAmount | uint256 | 发送到market的bnb数量  |
| lpAmount     | uint256 | 添加的流动性数量         |

### EventCompleteSubscribe

```solidity
event EventCompleteSubscribe(address indexed meToken, uint256 subscribeState, LaunchPad.StakeInfo stakeData, LaunchPad.LpInfo lpLockData)
```

认购结束事件，记录完成资金操作后的全部信息


Parameters:

| Name           | Type                       | Description                                 |
| :------------- | :------------------------- | :------------------------------------------ |
| meToken        | address                    | MEME地址                                      |
| subscribeState | uint256                    | 认购状态，0是未认购结束，1是已正常完成认购，2是完成认购时人数未凑足，3是认购失败  |
| stakeData      | struct LaunchPad.StakeInfo | StakeInfo数据                                 |
| lpLockData     | struct LaunchPad.LpInfo    | LpInfo数据                                    |

## Constants info

### UID (0x5cc99e35)

```solidity
uint256 constant UID = 1
```


### BLACK_HOLE (0x55eda4e8)

```solidity
address constant BLACK_HOLE = 0x000000000000000000000000000000000000dEaD
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


### COMMUNITY (0xf8d7f790)

```solidity
address immutable COMMUNITY
```


### FUN_RECEIVER (0x4e090742)

```solidity
address immutable FUN_RECEIVER
```


### launchConfig (0x24f33ce7)

```solidity
mapping(address => struct LaunchPad.LaunchConfig) launchConfig
```


### isSubscribe (0xad2f91b7)

```solidity
mapping(address => mapping(address => bool)) isSubscribe
```


### userUnstakeToken (0x6cc207eb)

```solidity
mapping(address => mapping(address => uint256)) userUnstakeToken
```


### userUnlockedLp (0xb438fcb6)

```solidity
mapping(address => mapping(address => uint256)) userUnlockedLp
```


### stakeData (0xc691d191)

```solidity
mapping(address => struct LaunchPad.StakeInfo) stakeData
```


### lpLockData (0x7fdf099a)

```solidity
mapping(address => struct LaunchPad.LpInfo) lpLockData
```


### minSubscribeNum (0x3520ee09)

```solidity
mapping(address => uint256) minSubscribeNum
```


### subscribeNum (0xd0c71c50)

```solidity
mapping(address => uint256) subscribeNum
```


### subscribeState (0xd353c0b7)

```solidity
mapping(address => uint256) subscribeState
```


### pairMETokenLP (0xd25f8c8a)

```solidity
mapping(address => address) pairMETokenLP
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


## Functions info

### receive

```solidity
receive() external payable
```


### constructor

```solidity
constructor(
    address _FUN_RECEIVER,
    address _TOKEN,
    address _sTOKEN,
    address _WBNB,
    address _USDT,
    address _staking,
    address _community,
    address _uniswapV2Router
)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### initMETokenSubscribe (0xdc90fff5)

```solidity
function initMETokenSubscribe(
    address meToken_,
    LaunchPad.LaunchConfig calldata config_
) external onlyManager
```


### setMETokenLp (0xed4920db)

```solidity
function setMETokenLp(
    address meToken_,
    address meTokenLp_
) external onlyManager
```


### getUsersSubscribeState (0x299ae9ee)

```solidity
function getUsersSubscribeState(
    address meToken_,
    address[] calldata usersList_
) external view returns (bool[] memory stateList_)
```

获取用户的meme认购状态


Parameters:

| Name       | Type      | Description  |
| :--------- | :-------- | :----------- |
| meToken_   | address   | MEMEtoken地址  |
| usersList_ | address[] | 用户地址数组       |


Return values:

| Name       | Type   | Description       |
| :--------- | :----- | :---------------- |
| stateList_ | bool[] | 用户的认购状态数组，元素是bool |

### subscribeInfo (0x8fadf79e)

```solidity
function subscribeInfo(
    address meToken_,
    address user_
)
    external
    view
    returns (
        uint256 subscribeState_,
        bool isSubscribe_,
        uint256 subscribeNum_,
        LaunchPad.LaunchConfig memory configInfo_,
        LaunchPad.RetStakeInfo memory stakeInfo_,
        LaunchPad.RetLpInfo memory lpInfo_
    )
```

获取MEME的当前认购信息


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEME地址      |
| user_    | address | 用户地址        |


Return values:

| Name            | Type                          | Description                                 |
| :-------------- | :---------------------------- | :------------------------------------------ |
| subscribeState_ | uint256                       | 认购状态，0是未认购结束，1是已正常完成认购，2是完成认购时人数未凑足，3是认购失败  |
| isSubscribe_    | bool                          | 是否已认购                                       |
| subscribeNum_   | uint256                       | 当前认购人数                                      |
| configInfo_     | struct LaunchPad.LaunchConfig | 参考LaunchConfig类型数据                          |
| stakeInfo_      | struct LaunchPad.RetStakeInfo | 参考RetStakeInfo类型数据                          |
| lpInfo_         | struct LaunchPad.RetLpInfo    | 参考RetLpInfo类型                               |

### subscribe (0x41a7726a)

```solidity
function subscribe(address meToken_) external payable
```

认购MEME


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEMEtoken地址 |

### completeSubscribe (0x0b68a1aa)

```solidity
function completeSubscribe(address meToken_) external
```


### unlockStaking (0x4f88865c)

```solidity
function unlockStaking(address meToken_) external
```

解锁Staking CSM


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEMEtoken地址 |

### unlockLP (0x973cbbb0)

```solidity
function unlockLP(address meToken_) external
```

解锁LP


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEMEtoken地址 |
