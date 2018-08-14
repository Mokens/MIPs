---
mip: 4
title: Integrating Mokens
status: Draft
author: Nick Mudge <nick@mokens.io>
discussions-to: https://github.com/Mokens/MIPs/issues/4
created: 2018-08-11
---

There are different ways to integrate mokens into projects. This document covers some of the ways it can be done.

The [mokens.io website](https://mokens.io) is just one user interface for minting and displaying mokens. There can be any number of user interfaces for minting 
and/or displaying and using mokens. 

The minting, display and use of mokens is decentralized because anyone can create appliations or implement functionality to do these things.
With knowledge and creative imagination the number of use cases of mokens is infinite.

## Mint Mokens in Your Project

The [Mokens contract](https://etherscan.io/address/0xaaf401585b72c678afc09036510d3ef759bdaf7e#code) has two mint functions, `mint` and `contractMint`, 
that take care of minting new mokens.

#### The `mint` Function
```solidity
/// @param _tokenOwner The Ethereum address that will own the newly minted moken.
/// @param _mokenName The unique name of the newly minted moken.
/// @param _linkHash A hash that can be used to link off-chain data with the newly minted moken.
/// @return mokenId The sequential moken number of the newly minted moken.
function mint(
  address _tokenOwner, 
  string _mokenName, 
  bytes32 _linkHash
) 
  external 
  payable 
  returns (uint256 mokenId)
```


