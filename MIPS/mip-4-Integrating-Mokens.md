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

The minting, display and use of mokens is decentralized because anyone can create applications or implement functionality to do these things.
With knowledge and creative imagination the number of use cases of mokens is infinite.

## Mint Mokens in Your Project

The [Mokens contract](https://etherscan.io/address/0xaaf401585b72c678afc09036510d3ef759bdaf7e#code) has two mint functions, `mint` and `contractMint`, 
that take care of minting new mokens.

Any new or existing project can choose which mint function to use.

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

The `mint` function is a simple function that can be called by any dapp or user interface or Ethereum contract. It calculates the current mint price and stores ether that is sent in the contract. It reverts if the ether that is sent is less than the mint price. If the ether that is sent is greater than the mint price then the extra ether is refunded.

The [mokens.io user interface](https://mokens.io) mints new mokens by calling the `mint` function directly.

The advantage of the `mint` function is that it is easier and simpler to use.

#### The `contractMint` Function
```solidity
/// @param _tokenOwner The Ethereum address that will own the newly minted moken.
/// @param _mokenName The unique name of the newly minted moken.
/// @param _linkHash A hash that can be used to link off-chain data with the newly minted moken.
/// @param _currencyName The name of the ERC20 token that is used to pay the mint price, or 'Ether'.
/// @param _pricePaid The mint price that was paid to mint the new moken.
/// @return mokenId The sequential moken number of the newly minted moken.
function contractMint(
  address _tokenOwner, 
  string _mokenName, 
  bytes32 _linkHash, 
  bytes32 _currencyName, 
  uint256 _pricePaid
) 
  external 
  returns (uint256 mokenId)
```

The `contractMint` function enables projects to mint new mokens and take a portion of the mint fee. 

For example Project Moon could integrate the minting of mokens in their project. Their project calls `contractMint` to mint new mokens and they collect 30 percent of the mint fee. The portion of the mint fee taken by a project is determined on a case by case basis.



