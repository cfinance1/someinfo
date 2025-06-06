# MToken

## Overview

#### License: AGPL-3.0-or-later

```solidity
contract MToken is ERC20, ERC20Permit, AccessControl
```


## Events info

### FeeRatioChanged

```solidity
event FeeRatioChanged(uint256 ratio)
```


### EventAllotFeeWithoutReferrer

```solidity
event EventAllotFeeWithoutReferrer(uint256 allotTime, uint256 allotAmount, uint256 allotedReferrerAmount)
```


### EventToLp

```solidity
event EventToLp(uint256 toLpAmount, uint256 liquidity, uint256 costToken, uint256 costETH)
```


### EventToLpBonus

```solidity
event EventToLpBonus(uint256 toLpBonusAmount)
```


### EventToBottomPool

```solidity
event EventToBottomPool(uint256 toBottomAmount)
```


### EventToMarketing

```solidity
event EventToMarketing(address marketing, uint256 amount)
```


### EventToBackBurn

```solidity
event EventToBackBurn(uint256 toBackBurnAmount)
```


### FeeTaken

```solidity
event FeeTaken(address indexed payer, address indexed receiver, bool isBuy, uint256 left, uint256 fee)
```


### FeeToReferrer

```solidity
event FeeToReferrer(address indexed user, address indexed referrer, uint256 fee)
```


## Constants info

### BLACK_HOLE (0x55eda4e8)

```solidity
address constant BLACK_HOLE = 0x000000000000000000000000000000000000dEaD
```


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


### MAX_SWAP_LIMIT (0x7d155108)

```solidity
uint256 constant MAX_SWAP_LIMIT = 1e9*1e18
```


### MAX_TOTAL (0xcd60fe35)

```solidity
uint256 constant MAX_TOTAL = 2100*1e8*1e18
```


## State variables info

### MARKETING_POOL (0xfa164f62)

```solidity
address immutable MARKETING_POOL
```


### BOTTOM_POOL (0x38fca36f)

```solidity
address immutable BOTTOM_POOL
```


### COMMUNITY (0xf8d7f790)

```solidity
address immutable COMMUNITY
```


### MLAUNCHPAD (0x16d031e0)

```solidity
address immutable MLAUNCHPAD
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
uint256 minAllotFee = 1e25
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
uint256 swapLimitPeriod = 3600
```


### swapLimitEndTime (0x868eedbf)

```solidity
uint256 swapLimitEndTime
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
    address mLaunchPad_
) ERC20(name_, symbol_) ERC20Permit(name_)
```


### setMainPair (0xf30e85bc)

```solidity
function setMainPair(address pair_) external onlyDefaultAdmin
```


### allotFee (0x56f0ef4b)

```solidity
function allotFee() external onlyFeeManager
```


### setSwapRouter (0x41273657)

```solidity
function setSwapRouter(address router_) external onlyFeeManager
```


### setMinAllotFee (0x96b3fe8a)

```solidity
function setMinAllotFee(uint256 value_) external onlyFeeManager
```

