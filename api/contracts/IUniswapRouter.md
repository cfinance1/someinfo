# IUniswapRouter

## Overview

#### License: AGPL-3.0-or-later

```solidity
interface IUniswapRouter
```


## Functions info

### WETH (0xad5c4648)

```solidity
function WETH() external pure returns (address)
```


### swapExactTokensForETHSupportingFeeOnTransferTokens (0x791ac947)

```solidity
function swapExactTokensForETHSupportingFeeOnTransferTokens(
    uint256 amountIn,
    uint256 amountOutMin,
    address[] memory path,
    address to,
    uint256 deadline
) external
```


### addLiquidityETH (0xf305d719)

```solidity
function addLiquidityETH(
    address token,
    uint256 amountTokenDesired,
    uint256 amountTokenMin,
    uint256 amountETHMin,
    address to,
    uint256 deadline
)
    external
    payable
    returns (uint256 amountToken, uint256 amountETH, uint256 liquidity)
```

