---
mip: 3
title: New Era Proposals
status: Draft
author: Nick Mudge <nick@mokens.io>
discussions-to: https://github.com/Mokens/MIPs/issues/3
created: 2018-08-11
---
> **Note:** While this MIP is in "draft" status it is not in force. New moken eras are not currently being created. When the draft status of this MIP is "active" then this document is active and new eras are started based on it.

## What is an Era?

An era is a name/label/branding for newly minted mokens for a period of time. The Moken community decides to start a new era or not each month. For example the Moken community could decide to have a Roman era for a month. During that time all mokens that are minted are mokens of the roman era. There could be a Silver era or Gold era or Olympics era or any label or branding. The era is stored with each moken in the Mokens contract and can be queried. 

Eras also determine the price to mint new mokens and the mint increase amount.

The era name, when it starts, the starting mint price, and it's increasing mint price are all determined by the moken community.

## Creating New Era Proposals

Anybody can submit a New Era Proposal at any time by [creating an issue](https://github.com/Mokens/MIPs/issues/new) with a title that starts with "New Era Proposal".

A New Era Proposal should consist of the following:
1. The name of the author.
2. The date the proposed era would start.
3. The name of the era. The era name must be 32 ASCII characters or shorter. 
4. The starting mint price.
5. The mint increase amount.
6. The status of the proposal, either "draft" or "active".   
7. The rationale for the era. 

### Status

The status is "draft" until the author feels the proposal is complete and final. The author changes the status to "active" when he/she feels it is ready.

### Rational

New eras should help the Mokens project in some way and the rational of a proposed era should explain how it helps the Mokens project.   

Here are examples of things to consider when writing a New Era Proposal:
1. Does the proposed era help get mokens accepted and integrated with other Ethereum projects?
2. Will the proposed era cause more people to adopt mokens?
3. Does the proposed era distinguish itself from past eras?
4. Will the proposed era satisfy existing moken holders (molders)?
5. Does the proposed era support or assist projects that use mokens?
6. Is the proposed era exciting and interesting and useful for something?
7. Does the proposed era balance moken scarcity: increase moken supply if they are too scarce or restrict moken creation if there are too many available at low prices on exchanges?

## Selecting New Era Proposals

People should show their interest and support for New Era Proposals by adding various emojis to them. Here are examples of emojis that can be used: :thumbsup:, :thumbsdown:, :heart:, :smiley:, 🎉

Up to 3 of the most popular New Era Proposals are selected for voting. Similar New Era Proposals should be consolidated. For example 2 or 3 similar proposals should be combined to 1.

## Voting for a New Era

Voting for a new era or keeping the current one is done on the 15th of every month.

The selected eras and the option for no new era are put into an Ethereum contract. A simple web user interface is used to interact with the voting contract. Moken holders (molders) vote on the era they want. The weight of each molder's vote depends on how many mokens he/she owns, however in the future this may be limited to prevent any one user from having too much influence.

The winning era will start on the 1st of the coming month, or there will be no change if the no new era option won the vote.

The same process repeats each month.


