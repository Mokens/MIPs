---
mip: 4
title: Integrating Mokens
status: Draft
author: Nick Mudge <nick@mokens.io>
discussions-to: https://github.com/Mokens/MIPs/issues/4
created: 2018-08-11
---

There are different ways to integrate mokens into projects. This document covers some of the ways it can be done.

The Mokens project uses an instance of the Mokens contract to mint non-fungible tokens that comply with the [ERC721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) and [ERC998](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md) standards. The Mokens project uses a single instance of the Mokens contract that is at this address: [0xaaf401585b72c678afc09036510d3ef759bdaf7e](https://etherscan.io/address/0xaaf401585b72c678afc09036510d3ef759bdaf7e#code). Integration is done with that contract instance at that address. The Moken contract is not upgradable and will not change.

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

The `mint` function is a simple function that can be called by any dapp or user interface or Ethereum contract. It calculates the current price of the fee to mint a moken and stores the fee in the contract. The function reverts if the ether that is sent to pay the mint fee is less than the current price. If the ether that is sent is greater than the current price then the extra ether is refunded.

The [mokens.io user interface](https://mokens.io) mints new mokens by calling the `mint` function directly.

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

For example Project Moon could integrate the minting of mokens in their project. Their project could call `contractMint` to mint new mokens and collect 30 percent of the mint fee. The percentage of the mint fee taken by a project is determined on a case by case basis. A project may not mint mokens for itself and later sell them at a discount.

Only contracts in an approved list that is stored in the Mokens contract can call the `contractMint` function. A project that wants to mint mokens should contact Nick Mudge <nick@mokens.io> to get their minting contract added to the approved list.

The `contractMint` function enables the minting fee to be paid in Ether or in ERC20 tokens.

A contract that calls `contractMint` needs to collect the correct mint fee, refund any overpayment, keep a portion of the fee  and send the rest to a designated address.

#### Moken Metadata

Just before a project mints a moken it should send an HTTP POST request to https://api.mokens.io with the metadata of the moken. The metadata can include a URI to an image, a description, tags and more. When the moken is minted the metadata will be associated with the moken and can be accessed through the http://api.mokens.io API. For example the metadata for Moken 28 is found at this URL https://api.mokens.io/moken/28.json

When a moken is minted the moken name, the linkHash and the moken owner address are used to find the metadata to be associated with it.

Here is an example of metadata that is currently being used with mokens. This is Moken 28:
```javascript
{
   "name":"Sweety",
   "image":"https://res.cloudinary.com/mokens/image/upload/v1533932717/ua0hgqwbzpjfjoemz44s.jpg",
   "description":"Street dog from Bali that found me and became my buddy. I gave her the name \"Sweety\" - Buying Bali Dog collectibles will lead to a donation to street dogs in Bali.",
   "external_url":"https://mokens.io/moken/28",
   "tags":[
      "dogs",
      "animals",
      "bali",
      "charity"
   ],
   "original":null
}
```

In the metadata if the value for `original` is null then it means that the moken is not a forgery. If the metadata for `original` is a number then it means that the moken is a forgery and the number is the moken Id of the original moken.

Projects can request that additional metadata be received and stored with mokens.

## Displaying Mokens in Your Project

Projects can integrate mokens in their project by displaying mokens. The metadata for displaying mokens can be found using the https://api.mokens.io API. The `tokenURI(uint256 _tokenId)` function uses the https://api.mokens.io API. It returns the appropriate URL for the supplied tokenId.

## Integrating with Mokens at the Contract Level

Your project can integrate mokens with your contracts to create various funtionality for users. 

#### Querying Mokens

Your project can query the Mokens contract to get and use data about specific mokens for your features and functionality. You can query and get the moken id, the moken era and moken name. You can query how many mokens a user has. You can query for who owns a moken. You can iterate through all the mokens or all the mokens owned by a specific user. You can query and get a mokens linkHash. You can query and get all the child NFTs that are owned by a moken. You can query and get all the ERC20 balances owned by a moken. You can query and get the NFT that owns a moken. And more.

#### Attach Properties to Mokens

In your contracts you can attach properties, or data to specific mokens giving those mokens characteristics, traits, functionality, and advantages of your own design. You can use these properties in your game play or for the functionality of your system. These added properties can be added to the metadata of mokens and displayed and used in other places accross the Internet. If you choose the functionality that you add to mokens with contracts can be used by other systems and applications.

Mokens is a platform of one NFT contract instance upon which functionality can be built and shared and reused. You can build on top of mokens.

#### Use the Composable Capability of Mokens

Useful references:

[Top-Down and Bottom-Up Composables, What’s the Difference and Which One Should You Use?](https://hackernoon.com/top-down-and-bottom-up-composables-whats-the-difference-and-which-one-should-you-use-db939f6acf1d)

[ERC998 Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md)

The Mokens contract fully implements the [ERC998ERC721TopDown](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc721-top-down-composable), [ERC998ERC20TopDown](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc20-top-down-composable), [ERC998ERC721BottomUp](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc721-bottom-up-composable) functionality.

Use the composable functionality of mokens for your project. 

**Here is an example:**

Let's say that you have an Ethereum game about adventure. 
1. In your game you have an avatar which is an NFT. 
2. You allow users to mint a moken to represent a pet for your avatar. 
3. You let the user select what kind of pet to mint and automatically generate an image of the pet.
4. You let the user choose a name for the pet.
5. When the user clicks a button to mint the pet moken your contract mints the moken and transfers (bottom-up style) ownership of the moken pet to the user's avatar so that the pet stays with the avatar. 
6. Depending on what kind of pet was chosen, the pet can give the avatar an advantage like increased strength or health or speed so users have a game play reason to mint a moken pet.
