# TokenFun

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract TokenFun is ERC20, ERC20Permit, AccessControl
```


## Events info

### EventAllotFee

```solidity
event EventAllotFee(uint256 allotTime, uint256 allotAmount, uint256 amountToFoundation)
```

分配手续费事件


Parameters:

| Name               | Type    | Description     |
| :----------------- | :------ | :-------------- |
| allotTime          | uint256 | 下次分配手续费时间       |
| allotAmount        | uint256 | 分配手续费数量         |
| amountToFoundation | uint256 | 分配到market的手续费数量 |

### EventToLp

```solidity
event EventToLp(uint256 toLpAmount, uint256 liquidity, uint256 costToken, uint256 costETH)
```

部分手续费用来添加LP


Parameters:

| Name       | Type    | Description   |
| :--------- | :------ | :------------ |
| toLpAmount | uint256 | 用来添加LP的手续费数量  |
| liquidity  | uint256 | 添加的LP数量       |
| costToken  | uint256 | LP的MEME数量     |
| costETH    | uint256 | LP的ETH数量      |

### EventToBottomPool

```solidity
event EventToBottomPool(uint256 toBottomAmount)
```

部分手续费用来添加到拖底池


Parameters:

| Name           | Type    | Description  |
| :------------- | :------ | :----------- |
| toBottomAmount | uint256 | 添加到拖底池的手续费数量 |

### EventToFoundation

```solidity
event EventToFoundation(address foundation, uint256 amount)
```

部分手续费用来转移到market


Parameters:

| Name       | Type    | Description     |
| :--------- | :------ | :-------------- |
| foundation | address | 接收手续费的地址        |
| amount     | uint256 | 转移到market的手续费数量 |

### EventToBackBurn

```solidity
event EventToBackBurn(uint256 toBackBurnAmount)
```

部分手续费用来回购销毁


Parameters:

| Name             | Type    | Description |
| :--------------- | :------ | :---------- |
| toBackBurnAmount | uint256 | 销毁CSF数量     |

### FeeRatioChanged

```solidity
event FeeRatioChanged(uint256 ratio)
```


### FeeTaken

```solidity
event FeeTaken(address indexed payer, address indexed receiver, bool isBuy, uint256 left, uint256 fee)
```


## Constants info

### INTERN_SYSTEM_MANAGER (0xc2524a4a)

```solidity
bytes32 constant INTERN_SYSTEM_MANAGER = keccak256("INTERN_SYSTEM_MANAGER")
```


### FEE_MANAGER (0xea26266c)

```solidity
bytes32 constant FEE_MANAGER = keccak256("FEE_MANAGER")
```


### INTERN_SYSTEM (0x1f9bbe20)

```solidity
bytes32 constant INTERN_SYSTEM = keccak256("INTERN_SYSTEM")
```


### PRECISION (0xaaf5eb68)

```solidity
uint256 constant PRECISION = 100e3
```


## State variables info

### MAX_SWAP_LIMIT (0x7d155108)

```solidity
uint256 immutable MAX_SWAP_LIMIT
```


### BOTTOM_POOL (0x38fca36f)

```solidity
address immutable BOTTOM_POOL
```


### LPLOCK_POOL (0x0b31b97b)

```solidity
address immutable LPLOCK_POOL
```


### uniswapV2Router (0x1694505e)

```solidity
contract IUniswapRouter uniswapV2Router
```


### WETH (0xad5c4648)

```solidity
address WETH
```


### mainPair (0x85af30c5)

```solidity
address mainPair
```


### minAllotFee (0x3c69a8d2)

```solidity
uint256 minAllotFee = 1000000*1e18
```


### feeRatio (0x41744dd4)

```solidity
uint256 feeRatio
```


### feeStageTime (0xc59f0fb0)

```solidity
uint256 feeStageTime
```


### feeConfigs (0xb1872b55)

```solidity
uint256[2][] feeConfigs
```


### swapLimitPeriod (0x1f465ac5)

```solidity
uint256 swapLimitPeriod
```


### swapLimitEndTime (0x868eedbf)

```solidity
uint256 swapLimitEndTime
```


### foundation (0x41fbb050)

```solidity
address foundation
```


## Modifiers info

### onlyDefaultAdmin

```solidity
modifier onlyDefaultAdmin()
```


### onlyFeeManager

```solidity
modifier onlyFeeManager()
```


### lockTheAllot

```solidity
modifier lockTheAllot()
```


## Functions info

### receive

```solidity
receive() external payable
```


### constructor

```solidity
constructor(
    string memory name_,
    string memory symbol_,
    uint256 mintTotal,
    address uniswapV2Router_,
    address launchPad_,
    address bottomPool_,
    address lpLockPool_,
    address foundation_,
    uint256 swapLimitPeriod_,
    uint256 maxSwapLimit_,
    uint256[2][] memory feeConfigs_
) ERC20(name_, symbol_) ERC20Permit(name_)
```


### setMainPair (0xf30e85bc)

```solidity
function setMainPair(address pair_) external onlyDefaultAdmin
```


### setSwapRouter (0x41273657)

```solidity
function setSwapRouter(address router_) external onlyFeeManager
```


### setMinAllotFee (0x96b3fe8a)

```solidity
function setMinAllotFee(uint256 value_) external onlyFeeManager
```


### setFoundation (0xdb3543f5)

```solidity
function setFoundation(address foundation_) external onlyFeeManager
```


### allotFee (0x56f0ef4b)

```solidity
function allotFee() external onlyFeeManager
```

