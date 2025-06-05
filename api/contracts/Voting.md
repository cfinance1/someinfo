# Voting

## Overview

#### License: GPL-3.0

```solidity
contract Voting is AccessControlUpgradeable
```


## Modifiers info

### onlyManager

```solidity
modifier onlyManager()
```


### onlyLaunchPad

```solidity
modifier onlyLaunchPad()
```


## Functions info

### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### startVote (0x2b39b39b)

```solidity
function startVote(
    address meToken_,
    address foundation_,
    uint256 destructionAmount_,
    address challenger_,
    uint256 challengerDestAmt_
) external onlyLaunchPad
```

