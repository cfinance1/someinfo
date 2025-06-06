# MLaunchPad

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract MLaunchPad is AccessControlUpgradeable
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


### UserLpBonusInfo

```solidity
struct UserLpBonusInfo {
	uint256 claimed;
	uint256 claimable;
	uint256 claimedGapCount;
	uint256 lastPerLPBonus;
}
```


### LpBonusInfo

```solidity
struct LpBonusInfo {
	uint256 lpGapCount;
	uint256 perLPBonus;
}
```


### CreateConfig

```solidity
struct CreateConfig {
	uint256 createCostBNB;
	uint256 subscribeDuration;
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


### TokenFeeInfo

```solidity
struct TokenFeeInfo {
	address builder;
	uint256 donatePoints;
	bool isVoting;
}
```


### RetMETokenList

```solidity
struct RetMETokenList {
	uint256 tokenId;
	address meToken;
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
	uint256 nextUnlockTime;
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
event EventCompleteSubscribe(address indexed meToken, uint256 subscribeState, MLaunchPad.StakeInfo stakeData, MLaunchPad.LpInfo lpLockData)
```

认购结束事件，记录完成资金操作后的全部信息


Parameters:

| Name           | Type                        | Description                                 |
| :------------- | :-------------------------- | :------------------------------------------ |
| meToken        | address                     | MEME地址                                      |
| subscribeState | uint256                     | 认购状态，0是未认购结束，1是已正常完成认购，2是完成认购时人数未凑足，3是认购失败  |
| stakeData      | struct MLaunchPad.StakeInfo | StakeInfo数据                                 |
| lpLockData     | struct MLaunchPad.LpInfo    | LpInfo数据                                    |

### EventCreateToken

```solidity
event EventCreateToken(uint256 indexed newMETokenId_, address indexed meToken, address indexed user, string name, string symbol, uint256 subscribeNum, uint256 label)
```


### EventCreateTokenInfo

```solidity
event EventCreateTokenInfo(address meToken, MLaunchPad.LaunchConfig meTokenConf)
```


### EventDonateForMEToken

```solidity
event EventDonateForMEToken(address indexed meToken, address indexed user, uint256 addDonatePoint, bool isOpen)
```


### EventAddDonatePointForMEToken

```solidity
event EventAddDonatePointForMEToken(address indexed meToken, address indexed user, uint256 addDonatePoint, uint256 userDonatePoint, uint256 meTokenDonatePoint)
```


### EventLpBonusInfo

```solidity
event EventLpBonusInfo(address indexed meToken, uint256 unlockMaxGapNum, uint256 unlockGapNum, MLaunchPad.LpBonusInfo bonusInfo, uint256 lockingGapNum, uint256 addClaimable, MLaunchPad.UserLpBonusInfo userInfo)
```


### EventClaimLPBonus

```solidity
event EventClaimLPBonus(address indexed meToken, address indexed user, uint256 lockingGapNum, uint256 claimable, MLaunchPad.UserLpBonusInfo userInfo)
```


### EventAllotBonus

```solidity
event EventAllotBonus(address indexed meToken, uint256 amount, uint256 bonusAmt, uint256 addPerLPBonus, MLaunchPad.LpBonusInfo info)
```


### EventChangeMETokenBuilder

```solidity
event EventChangeMETokenBuilder(address indexed meToken, address indexed user)
```


## Constants info

### UID (0x5cc99e35)

```solidity
uint256 constant UID = 1
```


### BLACK_HOLE (0x55eda4e8)

```solidity
address constant BLACK_HOLE = 0x000000000000000000000000000000000000dEaD
```


### INTERN_SYSTEM (0x1f9bbe20)

```solidity
bytes32 constant INTERN_SYSTEM = keccak256("INTERN_SYSTEM")
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


### BOTTOM_POOL (0x38fca36f)

```solidity
address immutable BOTTOM_POOL
```


### MARKETING_POOL (0xfa164f62)

```solidity
address immutable MARKETING_POOL
```


### FTOKEN (0x976fe91a)

```solidity
address immutable FTOKEN
```


### VOTING (0x269e1d1a)

```solidity
address immutable VOTING
```


### launchConfig (0x24f33ce7)

```solidity
mapping(address => struct MLaunchPad.LaunchConfig) launchConfig
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
mapping(address => struct MLaunchPad.StakeInfo) stakeData
```


### lpLockData (0x7fdf099a)

```solidity
mapping(address => struct MLaunchPad.LpInfo) lpLockData
```


### userLpBonusInfo (0xf2801aa5)

```solidity
mapping(address => mapping(address => struct MLaunchPad.UserLpBonusInfo)) userLpBonusInfo
```


### lpBonusInfo (0xcdb8242d)

```solidity
mapping(address => struct MLaunchPad.LpBonusInfo) lpBonusInfo
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


### createTokenConfig (0x3e934217)

```solidity
mapping(uint256 => struct MLaunchPad.CreateConfig) createTokenConfig
```


### userDonatePoints (0xa51ad287)

```solidity
mapping(address => mapping(address => uint256)) userDonatePoints
```

token => user => amount
### meTokenFeeInfo (0x50529f3f)

```solidity
mapping(address => struct MLaunchPad.TokenFeeInfo) meTokenFeeInfo
```


### meTokenList (0xb4556b2f)

```solidity
mapping(uint256 => address) meTokenList
```


### meTokenIdMap (0x5279e328)

```solidity
mapping(address => uint256) meTokenIdMap
```


### meTokenListLength (0x122783e7)

```solidity
uint256 meTokenListLength
```


### meTokenLastId (0xb250e200)

```solidity
uint256 meTokenLastId
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


### onlyVoting

```solidity
modifier onlyVoting()
```


## Functions info

### receive

```solidity
receive() external payable
```


### constructor

```solidity
constructor(
    address WBNB_,
    address USDT_,
    address TOKEN_,
    address sTOKEN_,
    address FTOKEN_,
    address staking_,
    address community_,
    address bottomPool_,
    address voting_,
    address MARKETING_POOL_,
    address uniswapV2Router_
)
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### addNewMETokenList (0x9b87f9ab)

```solidity
function addNewMETokenList(
    address[] calldata meTokenList_
) external onlyManager
```


### initCreateTokenConfig (0x0918f840)

```solidity
function initCreateTokenConfig(
    uint256 subscribeNum_,
    MLaunchPad.CreateConfig calldata config_
) external onlyManager
```


### getMETokenList (0x64969b5b)

```solidity
function getMETokenList(
    uint256 startId_
) external view returns (MLaunchPad.RetMETokenList[] memory meTokenList_)
```

获取MEME token地址和id


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| startId_ | uint256 | 起始id        |


Return values:

| Name         | Type                               | Description                                                |
| :----------- | :--------------------------------- | :--------------------------------------------------------- |
| meTokenList_ | struct MLaunchPad.RetMETokenList[] | 元素为RetMETokenList(uint256, address).[[tokenId, meToken], ] |

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
        MLaunchPad.LaunchConfig memory configInfo_,
        MLaunchPad.RetStakeInfo memory stakeInfo_,
        MLaunchPad.RetLpInfo memory lpInfo_
    )
```

获取MEME的当前认购信息


Parameters:

| Name     | Type    | Description |
| :------- | :------ | :---------- |
| meToken_ | address | MEME地址      |
| user_    | address | 用户地址        |


Return values:

| Name            | Type                           | Description                                 |
| :-------------- | :----------------------------- | :------------------------------------------ |
| subscribeState_ | uint256                        | 认购状态，0是未认购结束，1是已正常完成认购，2是完成认购时人数未凑足，3是认购失败  |
| isSubscribe_    | bool                           | 是否已认购                                       |
| subscribeNum_   | uint256                        | 当前认购人数                                      |
| configInfo_     | struct MLaunchPad.LaunchConfig | 参考LaunchConfig类型数据                          |
| stakeInfo_      | struct MLaunchPad.RetStakeInfo | 参考RetStakeInfo类型数据                          |
| lpInfo_         | struct MLaunchPad.RetLpInfo    | 参考RetLpInfo类型                               |

### getClaimableLPBonus (0xb3f7486f)

```solidity
function getClaimableLPBonus(
    address meToken_,
    address user_
) external view returns (uint256)
```

获取用户可领取的分红数量


Parameters:

| Name     | Type    | Description   |
| :------- | :------ | :------------ |
| meToken_ | address | meme token地址  |
| user_    | address | 用户地址          |


Return values:

| Name | Type    | Description |
| :--- | :------ | :---------- |
| [0]  | uint256 | CSF分红数量     |

### createToken (0x56f698a3)

```solidity
function createToken(
    string memory name_,
    string memory symbol_,
    uint256 subscribeNum_,
    uint256 label_
) external payable
```


### donateForMEToken (0xc183c454)

```solidity
function donateForMEToken(address meToken_, uint256 amount_) external
```

为MEME捐献CSF


Parameters:

| Name     | Type    | Description  |
| :------- | :------ | :----------- |
| meToken_ | address | memetoken地址  |
| amount_  | uint256 | 捐献CSF数量      |

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

### claimLPBonus (0x403782ef)

```solidity
function claimLPBonus(address meToken_) external
```

领取分红


Parameters:

| Name     | Type    | Description  |
| :------- | :------ | :----------- |
| meToken_ | address | meme token地址 |

### allotBonus (0x3544f27a)

```solidity
function allotBonus(address meToken_, uint256 amount_) external
```


### addDonatePointsByVoting (0x61d623ec)

```solidity
function addDonatePointsByVoting(
    address meToken_,
    address user_,
    uint256 donatePoints_
) external onlyVoting
```


### changeMETokenBuilder (0x66ba31db)

```solidity
function changeMETokenBuilder(
    address meToken_,
    address user_
) external onlyVoting
```


### updateMETokenSubscribe (0xda949d56)

```solidity
function updateMETokenSubscribe(
    address meToken_,
    MLaunchPad.LaunchConfig calldata config_
) external onlyManager
```


### setMETokenLp (0xed4920db)

```solidity
function setMETokenLp(
    address meToken_,
    address meTokenLp_
) external onlyManager
```

