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


### EventToLp

```solidity
event EventToLp(uint256 toLpAmount, uint256 liquidity, uint256 costToken, uint256 costETH)
```


### EventToBottomPool

```solidity
event EventToBottomPool(uint256 toBottomAmount)
```


### EventToFoundation

```solidity
event EventToFoundation(address foundation, uint256 amount)
```


### EventToBackBurn

```solidity
event EventToBackBurn(uint256 toBuyBackAmount)
```


### FeeRatioChanged

```solidity
event FeeRatioChanged(uint256 ratio)
```


### FeeTaken

```solidity
event FeeTaken(address indexed payer, address indexed receiver, bool isBuy, uint256 left, uint256 fee)
```


## Constants info

### FEE_MANAGER (0xea26266c)

```solidity
bytes32 constant FEE_MANAGER = keccak256("FEE_MANAGER")
```


### INTERN_SYSTEM (0x1f9bbe20)

```solidity
bytes32 constant INTERN_SYSTEM = keccak256("INTERN_SYSTEM")
```


### MIN_SWAP_LIMIT (0x9c3638c1)

```solidity
uint256 constant MIN_SWAP_LIMIT = 1e9 * 1e18
```


### PRECISION (0xaaf5eb68)

```solidity
uint256 constant PRECISION = 100e3
```


## State variables info

### WBNB (0x8dd95002)

```solidity
address immutable WBNB
```


### BOTTOM_POOL (0x38fca36f)

```solidity
address immutable BOTTOM_POOL
```


### LPLOCK_POOL (0x0b31b97b)

```solidity
address immutable LPLOCK_POOL
```


### UNISWAPV2ROUTER (0xa8b62f7b)

```solidity
contract IUniswapRouter immutable UNISWAPV2ROUTER
```


### mainPair (0x85af30c5)

```solidity
address mainPair
```


### minAllotFee (0x3c69a8d2)

```solidity
uint256 minAllotFee = 100*1e18
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


### allotTime (0xc3dd80c7)

```solidity
uint256 allotTime
```


### swapLimitPeriod (0x1f465ac5)

```solidity
uint256 swapLimitPeriod = 3600
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
    address bottomPool_,
    address lpLockPool_,
    address funSubscribe_,
    address foundation_
) ERC20(name_, symbol_) ERC20Permit(name_)
```


### setMainPair (0xf30e85bc)

```solidity
function setMainPair(address pair_) external onlyDefaultAdmin
```


### setMinAllotFee (0x96b3fe8a)

```solidity
function setMinAllotFee(uint256 value_) external onlyFeeManager
```


### setFoundation (0xdb3543f5)

```solidity
function setFoundation(address foundation_) external onlyFeeManager
```


### setAllotTime (0x84969c2b)

```solidity
function setAllotTime(uint256 allotTime_) external onlyFeeManager
```

