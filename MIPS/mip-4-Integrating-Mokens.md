---
mip: 4
title: Integrating Mokens
status: Draft
author: Nick Mudge <nick@mokens.io>
discussions-to: https://github.com/Mokens/MIPs/issues/4
created: 2018-08-11
---

There are different ways to integrate mokens into projects. This document covers some of the ways it can be done.

The Mokens project uses a single instance of the Mokens contract to mint non-fungible tokens that comply with the [ERC721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) and [ERC998](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md) standards. Information about the Mokens contract is here: <https://mokens.io/about/mokens-contract>. Integration is done with that contract instance at that address. 

One thing to note is that all the mokens functionality is too much to fit in one contract. So the Mokens contract delegates function calls to delegate contracts. 

The [mokens.io website](https://mokens.io) is just one user interface for minting and displaying mokens. There can be any number of user interfaces for minting 
and/or displaying and using mokens. 

The minting, display and use of mokens is decentralized because anyone can create applications or implement functionality to do these things.
With knowledge and creative imagination the number of use cases of mokens is infinite.



#### Moken Metadata
Various meta data about mokens can be retreived by using the https://api.mokens.io api. 
Here is an example at: https://api.mokens.io/moken/28

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

Projects can request that additional metadata be received and stored with mokens.

## Displaying Mokens in Your Project

Projects can integrate mokens in their project by displaying mokens. The metadata for displaying mokens can be found using the https://api.mokens.io API. The `tokenURI(uint256 _tokenId)` function uses the https://api.mokens.io API. It returns the appropriate URL for the supplied tokenId. For example here is the URL for Moken 5:  https://api.mokens.io/moken/5.json

## Integrating with Mokens at the Contract Level

Your project can integrate mokens with your contracts to create various functionality for users. 

#### Querying Mokens

Your project can query the Mokens contract to get and use data about specific mokens for your features and functionality. For each moken you can query and get the moken id, the moken collection and moken name. You can query how many mokens a user has. You can query for who owns a moken. You can iterate through all the mokens or all the mokens owned by a specific user. You can query and get all the child NFTs that are owned by a moken. You can query and get all the ERC20 balances owned by a moken. You can query and get the NFT that owns a moken. And more.

#### Attach Properties to Mokens

In your contracts you can attach properties, or data to specific mokens giving those mokens characteristics, traits, functionality, and advantages of your own design. You can use these properties in your game play or for the functionality of your system. These added properties can be added to the metadata of mokens and displayed and used in other places across the Internet. If you choose the functionality that you add to mokens with contracts can be used by other systems and applications.

Mokens is a platform of one NFT contract instance upon which functionality can be built and shared and reused. You can build on top of mokens.

#### Use the Composable Capability of Mokens

Useful references:

[Top-Down and Bottom-Up Composables, What’s the Difference and Which One Should You Use?](https://hackernoon.com/top-down-and-bottom-up-composables-whats-the-difference-and-which-one-should-you-use-db939f6acf1d)

[ERC998 Standard](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md)

The Mokens contract fully implements the [ERC998ERC721TopDown](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc721-top-down-composable), [ERC998ERC20TopDown](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc20-top-down-composable), [ERC998ERC721BottomUp](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-998.md#erc721-bottom-up-composable) functionality.

Use the composable functionality of mokens for your project. 

**Here is an example:**

Let's say that you have an Ethereum adventure game. 
1. In your game you have an avatar which is an NFT. 
2. You decide to use mokens as pets in the game.
3. You let the user select what kind of pet to mint and automatically generate an image of the pet.
4. You let the user choose a name for the pet.
5. When the user clicks a button to mint the moken pet your contract mints the moken and transfers (bottom-up style) ownership of the moken pet to the user's avatar so that the pet stays with the avatar. 
6. Depending on what kind of pet was chosen, the pet can give the avatar an advantage like increased strength or health or speed so users have a game play reason to mint a moken pet.

## Contact

Join the discussion on the [Mokens Discord](https://discord.gg/ZyaqFhE).

To get updates about mokens [join the mokens email list](https://mokens.gr8.com/).
