---
title: "Crowdfunding Smart Contract for Beginners"
datePublished: Wed May 24 2023 11:50:12 GMT+0000 (Coordinated Universal Time)
cuid: cli1n8abk001209mo2gblgmli
slug: crowdfunding-smart-contract-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684928971272/f166177b-a542-4286-acdf-713e5e94ff21.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684929006632/14908a12-54e4-4804-a80d-588ed8632c77.jpeg
tags: bitcoin, crowdfunding, ethereum, web3, smart-contracts

---

## **This smart contract is for learning purpose and not recommended for professional use**  

## Smart Contract  

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;
contract CrowdFunding{

    struct Request{
        string description;
        address payable recepient;
        uint value;
        uint noOfVoters;
        bool completed;
        mapping (address=>bool) voters;
    }

    mapping (address=>uint) public contributors;
    mapping (uint=>Request) public requests;
    uint public numberOfRequests;
    address public manager;
    uint public minimumContribution;
    uint public deadline;
    uint public target;
    uint public raisedAmount;
    uint public noOfContributors;

    constructor(uint _target, uint _deadline){
        target=_target;
        deadline=block.timestamp+_deadline;
        manager=msg.sender;
        minimumContribution=1000 wei;
    }

    modifier onlyManager(){
        require(msg.sender==manager,"You are not the manager, Only manager can call this function");
        _;
    }

    function createRequest(string calldata _description,address payable _recepient, uint _value )public onlyManager {
        Request storage newRequest= requests[numberOfRequests];
        numberOfRequests++;
        newRequest.description=_description;
        newRequest.recepient=_recepient;
        newRequest.value=_value;
        newRequest.noOfVoters=0;
        newRequest.completed=false;
    }

    function contribution()public payable {
        require(block.timestamp<deadline,"The deadline has passed");
        require(msg.value>minimumContribution,"The minimum contribution is 1000 wei");
        if (contributors[msg.sender]==0){
            noOfContributors++;
        }
        contributors[msg.sender]+=msg.value;
        raisedAmount+=msg.value;

    }

    function getContractBalance() public view returns(uint){
        return address(this).balance;
    }

    function refund() public {
        require(block.timestamp>deadline && raisedAmount<target && contributors[msg.sender]>0,"You are not eligible for refund");
        payable(msg.sender).transfer(contributors[msg.sender]);
        contributors[msg.sender]=0;
    }

    function voteRequest(uint _requestNo) public{
        require(contributors[msg.sender]>0,"You are not a contributor");
        Request storage thisRequest= requests[_requestNo];
        require(thisRequest.voters[msg.sender]==false,"You have already voted");
        thisRequest.voters[msg.sender]=true;
        thisRequest.noOfVoters++;
    }

    function takePayment(uint _requestNo) public payable {
        require(raisedAmount>target,"The target is not achieved");
        Request storage thisRequest= requests[_requestNo];
        require(thisRequest.completed==false,"The payment has already been claimed");
        require(thisRequest.noOfVoters>noOfContributors/2,"Your request is not approved by community");
        thisRequest.recepient.transfer(thisRequest.value);
        thisRequest.completed=true;
        thisRequest.value=0;
    }


}
```

## Smart Contract breakdown + explanation

1. Solidity Version and License Identifier:
    

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;
```

The SPDX-License-Identifier specifies the license under which the code is released. In this case, it's the MIT license. `pragma solidity ^0.8.17;` indicates that the code should be compiled using a Solidity compiler of version 0.8.17 or higher.

1. Contract Declaration and State Variables:
    

```solidity
contract CrowdFunding {
    struct Request {
        string description;
        address payable recipient;
        uint value;
        uint noOfVoters;
        bool completed;
        mapping (address => bool) voters;
    }

    mapping (address => uint) public contributors;
    mapping (uint => Request) public requests;
    uint public numberOfRequests;
    address public manager;
    uint public minimumContribution;
    uint public deadline;
    uint public target;
    uint public raisedAmount;
    uint public noOfContributors;
```

The contract `CrowdFunding` is defined. It contains a struct `Request`, which represents a funding request made by the manager. The struct has fields for description, recipient, value, number of voters, completion status, and a mapping of voters.

The contract also declares several state variables:

* `contributors`: A mapping that stores the contribution amount of each contributor.
    
* `requests`: A mapping that stores the funding requests made by the manager.
    
* `numberOfRequests`: The total number of funding requests.
    
* `manager`: The address of the contract manager.
    
* `minimumContribution`: The minimum amount required for a contribution.
    
* `deadline`: The deadline (in UNIX timestamp) for accepting contributions.
    
* `target`: The target amount to be raised.
    
* `raisedAmount`: The total amount raised so far.
    
* `noOfContributors`: The total number of contributors.
    

1. Constructor:
    

```solidity
constructor(uint _target, uint _deadline){
        target = _target;
        deadline = block.timestamp + _deadline;
        manager = msg.sender;
        minimumContribution = 1000 wei;
    }
```

The constructor initializes the contract by setting the target amount, deadline, manager address, and minimum contribution required.

1. Modifier:
    

```solidity
modifier onlyManager(){
        require(msg.sender == manager, "You are not the manager. Only the manager can call this function");
        _;
    }
```

The `onlyManager` modifier is used to restrict access to certain functions only to the manager of the contract. It ensures that only the manager can call those functions.

1. Creating a Funding Request:
    

```solidity
function createRequest(string calldata _description, address payable _recipient, uint _value) public onlyManager {
        Request storage newRequest = requests[numberOfRequests];
        numberOfRequests++;
        newRequest.description = _description;
        newRequest.recipient = _recipient;
        newRequest.value = _value;
        newRequest.noOfVoters = 0;
        newRequest.completed = false;
    }
```

The `createRequest` function allows the manager to create a funding request. It takes a description, recipient address, and value as parameters. The function creates a new request, increments the `numberOfRequests`, and initializes the request's fields.

1. Contribution:
    

```solidity
function contribution() public payable {
        require(block.timestamp < deadline, "The deadline has passed");
        require(msg.value > minimumContribution, "The minimum contribution is 1000 wei");

        if (contributors[msg.sender] == 0) {
            noOfContributors++;
        }

        contributors[msg.sender] += msg.value;
        raisedAmount += msg.value;
    }
```

The `contribution` function allows users to contribute funds to the contract. It requires that the current timestamp is before the deadline and the contributed value is greater than the minimum contribution.

If the contributor is contributing for the first time (`contributors[msg.sender] == 0`), the `noOfContributors` is incremented. The contribution amount is added to the contributor's balance and the total `raisedAmount` is updated.

1. Contract Balance:
    

```solidity
function getContractBalance() public view returns(uint){
        return address(this).balance;
    }
```

The `getContractBalance` function returns the current balance of the contract.

1. Refund:
    

```solidity
function refund() public {
        require(block.timestamp > deadline && raisedAmount < target && contributors[msg.sender] > 0, "You are not eligible for refund");
        payable(msg.sender).transfer(contributors[msg.sender]);
        contributors[msg.sender] = 0;
    }
```

The `refund` function allows contributors to request a refund if the deadline has passed, the target amount has not been reached, and they have made a contribution. It transfers the contributed amount back to the contributor and sets their contribution balance to zero.

1. Voting for a Request:
    

```solidity
function voteRequest(uint _requestNo) public {
        require(contributors[msg.sender] > 0, "You are not a contributor");
        Request storage thisRequest = requests[_requestNo];
        require(thisRequest.voters[msg.sender] == false, "You have already voted");
        thisRequest.voters[msg.sender] = true;
        thisRequest.noOfVoters++;
    }
```

The `voteRequest` function allows contributors to vote for a specific funding request. It requires that the caller is a contributor and hasn't already voted. The function updates the request's voters mapping and increments the number of voters for that request.

1. Taking Payment for a Request:
    

```solidity
function takePayment(uint _requestNo) public payable {
        require(raisedAmount > target, "The target is not achieved");
        Request storage thisRequest = requests[_requestNo];
        require(thisRequest.completed == false, "The payment has already been claimed");
        require(thisRequest.noOfVoters > noOfContributors / 2, "Your request is not approved by the community");
        thisRequest.recipient.transfer(thisRequest.value);
        thisRequest.completed = true;
        thisRequest.value = 0;
    }
```

The `takePayment` function allows the manager to claim the payment for a specific funding request. It requires that the target amount has been achieved, the request has not been completed, and the request has received approval from more than half of the contributors. The function transfers the payment amount to the recipient address, marks the request as completed, and sets the value of the request to zero.

## Github Link :-

[This is the github link](https://github.com/moayaan1911/smart-contracts/tree/master/4.%20CrowdFunding)