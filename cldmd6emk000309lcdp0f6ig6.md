# Soulbound Token : Complete Guide

Soulbound Tokens (SBTs) are a new type of token that have recently gained popularity in the decentralized world. They are similar to Non-Fungible Tokens (NFTs), but with some key differences. In this blog, we will explore what SBTs are, the differences between SBTs and NFTs, the advantages and disadvantages of SBTs, and how they can benefit the Ethereum network.

## What are SBTs?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675297932195/9a13594d-7f56-4e42-a868-515d04197a40.jpeg align="center")

A Soulbound Token is a type of token that is tied to a specific user and cannot be transferred or traded to another user. This makes SBTs unique and allows for the creation of new and innovative use cases for digital assets. Unlike NFTs, which can be bought, sold, and traded freely, SBTs are designed to stay with their owner for life.

## NFTs vs SBTs

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675297573555/3ec7f5ff-1a0c-4d65-a42c-ed85bd378b67.png align="center")

The main difference between SBTs and NFTs is that NFTs are designed to be traded, while SBTs are designed to be tied to a specific user. NFTs can be traded freely on various marketplaces, and their value is determined by supply and demand. On the other hand, SBTs are tied to a specific user and have no real value in the open market.

## Advantages of SBT

One of the biggest advantages of SBTs is that they provide a new and innovative way for digital assets to be used. SBTs can be used for a variety of purposes, such as gaming, collectibles, or even digital identity. Another advantage of SBTs is that they provide a new level of security and protection for digital assets. Since SBTs are tied to a specific user, they cannot be stolen or lost in the same way that NFTs can.

## Disadvantages of SBT

One of the main disadvantages of SBTs is that they are not as versatile as NFTs. Since SBTs cannot be traded or transferred, they may not be as useful for certain applications, such as collectibles or gaming. Additionally, SBTs can only be used by their owner, which may limit their potential use cases.

## Example Code for SBT token

Here is an example of a Solidity code for a Soulbound Token:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;

/**
 * An experiment in Soul Bound Tokens (SBT's) following Vitalik's
 * co-authored whitepaper at:
 * https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4105763
 *
 * I propose for a rename to Non-Transferable Tokens NTT's
 */

contract SBT {

    struct Soul {
        string identity;
        // add issuer specific fields below
        string url;
        uint256 score;
        uint256 timestamp;
    }

    mapping (address => Soul) private souls;
    mapping (address => mapping (address => Soul)) soulProfiles;
    mapping (address => address[]) private profiles;

    string public name;
    string public ticker;
    address public operator;
    bytes32 private zeroHash = 0xc5d2460186f7233c927e7db2dcc703c0e500b653ca82273b7bfad8045d85a470;
    
    event Mint(address _soul);
    event Burn(address _soul);
    event Update(address _soul);
    event SetProfile(address _profiler, address _soul);
    event RemoveProfile(address _profiler, address _soul);

    constructor(string memory _name, string memory _ticker) {
      name = _name;
      ticker = _ticker;
      operator = msg.sender;
    }

    function mint(address _soul, Soul memory _soulData) external {
        require(keccak256(bytes(souls[_soul].identity)) == zeroHash, "Soul already exists");
        require(msg.sender == operator, "Only operator can mint new souls");
        souls[_soul] = _soulData;
        emit Mint(_soul);
    }

    function burn(address _soul) external {
        require(msg.sender == _soul || msg.sender == operator, "Only users and issuers have rights to delete their data");
        delete souls[_soul];
        for (uint i=0; i<profiles[_soul].length; i++) {
            address profiler = profiles[_soul][i];
            delete soulProfiles[profiler][_soul];
        }
        emit Burn(_soul);
    }

    function update(address _soul, Soul memory _soulData) external {
        require(msg.sender == operator, "Only operator can update soul data");
        require(keccak256(bytes(souls[_soul].identity)) != zeroHash, "Soul does not exist");
        souls[_soul] = _soulData;
        emit Update(_soul);
    }

    function hasSoul(address _soul) external view returns (bool) {
        if (keccak256(bytes(souls[_soul].identity)) == zeroHash) {
            return false;
        } else {
            return true;
        }
    }

    function getSoul(address _soul) external view returns (Soul memory) {
        return souls[_soul];
    }

    /**
     * Profiles are used by 3rd parties and individual users to store data.
     * Data is stored in a nested mapping relative to msg.sender
     * By default they can only store data on addresses that have been minted
     */
    function setProfile(address _soul, Soul memory _soulData) external {
        require(keccak256(bytes(souls[_soul].identity)) != zeroHash, "Cannot create a profile for a soul that has not been minted");
        soulProfiles[msg.sender][_soul] = _soulData;
        profiles[_soul].push(msg.sender);
        emit SetProfile(msg.sender, _soul);
    }

    function getProfile(address _profiler, address _soul) external view returns (Soul memory) {
        return soulProfiles[_profiler][_soul];
    }

    function listProfiles(address _soul) external view returns (address[] memory) {
        return profiles[_soul];
    }

    function hasProfile(address _profiler, address _soul) external view returns (bool) {
        if (keccak256(bytes(soulProfiles[_profiler][_soul].identity)) == zeroHash) {
            return false;
        } else {
            return true;
        }
    }

    function removeProfile(address _profiler, address _soul) external {
        require(msg.sender == _soul, "Only users have rights to delete their profile data");
        delete soulProfiles[_profiler][msg.sender];
        emit RemoveProfile(_profiler, _soul);
    }
}
```

### Explanation of the Code

* A soul has the following data fields: identity, url, score, and timestamp. The contract maintains a mapping of address to soul and a mapping of address to a mapping of address to soul, which allows for creating profiles for each soul by third parties and individual users.
    
* The contract implements several functions for managing souls, including: mint, burn, update, and hasSoul. The mint function creates a new soul and assigns it to a given Ethereum address. The burn function deletes a soul and all associated profiles. The update function allows the operator to modify an existing soul's data. The hasSoul function returns a boolean indicating if a soul exists for a given address.
    
* The contract also implements functions for managing profiles, including: setProfile, getProfile, listProfiles, hasProfile, and removeProfile. The setProfile function creates a profile for a soul by a third party or individual user. The getProfile function retrieves a profile for a soul. The listProfiles function lists all the profiles associated with a soul. The hasProfile function returns a boolean indicating if a profile exists for a soul by a given profiler. The removeProfile function allows the user to delete their profile.
    
* The contract emits events for important actions, such as minting, burning, updating, setting, and removing profiles. The contract is licensed under the MIT License.
    

## SBT and Ethereum

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675297233012/5e4408c8-d71f-4a71-aaeb-b526f09b1e7e.png align="center")

SBTs have the potential to greatly benefit the Ethereum network. By providing a new and innovative way for digital assets to be used, SBTs can help drive innovation and adoption of decentralized technology. Additionally, since SBTs are tied to a specific user, they can provide a new level of security and protection for digital assets, which can help increase trust in the Ethereum network.

## Conclusion

In conclusion, Soulbound Tokens are a new and exciting type of token that have the potential to greatly benefit the Ethereum network. By providing a new and innovative way for digital assets to be used, SBTs can help drive innovation and adoption of decentralized technology. Additionally, by providing a new level of security and protection for digital assets, SBTs can help increase trust in the Ethereum network.