# LpLockPool

## Overview

#### License: GPL-3.0

```solidity
contract LpLockPool is AccessControlUpgradeable
```


## State variables info

### flag (0x890eba68)

```solidity
bool flag
```


### lpReleaseTime (0x48b98721)

```solidity
uint256 lpReleaseTime
```


## Modifiers info

### onlyAdmin

```solidity
modifier onlyAdmin()
```


## Functions info

### constructor

```solidity
constructor()
```


### initialize (0x8129fc1c)

```solidity
function initialize() public initializer
```


### addLock (0x7fa3f3d0)

```solidity
function addLock(uint256 _time) public onlyAdmin
```

