---
title: "CrowdFunding Smart Contract"
datePublished: Fri Feb 02 2024 17:52:00 GMT+0000 (Coordinated Universal Time)
cuid: cls4xzxx0000009lb9zhre2x2
slug: crowdfunding-smart-contract
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706896160570/08441506-57de-4230-946c-98eadfc83145.jpeg
tags: javascript, blockchain, crowdfunding, solidity, web3, smart-contracts

---

## **Introduction**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706896167059/fea07839-377e-4e41-bdf3-83946dfdf554.webp align="center")

Crowdfunding has revolutionized the way individuals and organizations raise funds for various projects and causes. However, traditional crowdfunding platforms often suffer from issues of trust, transparency, and efficiency. Blockchain technology, with its decentralized and immutable nature, offers a promising solution to address these challenges.

**In this blog post, we'll delve into the implementation of a CrowdFunding smart contract built on the Ethereum blockchain. We'll explore its code structure, key functions, and the benefits it brings to crowdfunding processes.**

## Smart Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract CrowdFunding {
    struct Campaign {
        uint campaignId;
        string campaignTitle;
        string campaignDescription;
        string campaignImageCID;
        uint targetAmount;
        uint raisedAmount;
        uint startAt;
        uint endAt;
        bool status;
        address payable campaignOwner;
    }

    Campaign[] public campaigns;

    struct Contribution {
        uint campaignId;
        uint contributionId;
        uint amount;
        uint date;
        address payable contributor;
    }

    Contribution[] public contributions;

    uint private campaignId = 0;
    uint private contributionId = 0;

    event CampaignCreated(uint campaignId, uint createdAt);

    function createCampaign(
        string memory _campaignTitle,
        string memory _campaignDescription,
        string memory _campaignImageCID,
        uint _targetAmount,
        uint _duration
    ) public {
        require(_targetAmount > 0, "Target amount should be greater than 0");
        require(_duration > 0, "Duration should be greater than 0");
        campaigns.push(
            Campaign(
                campaignId,
                _campaignTitle,
                _campaignDescription,
                _campaignImageCID,
                _targetAmount,
                0,
                block.timestamp,
                block.timestamp + _duration,
                true,
                payable(msg.sender)
            )
        );
        emit CampaignCreated(campaignId, block.timestamp);
        campaignId++;
    }

    function totalCampaigns() public view returns (uint) {
        return campaigns.length;
    }

    function getParticularCampaign(
        uint _campaignId
    ) public view returns (Campaign memory) {
        return campaigns[_campaignId];
    }

    function getCampaigns() public view returns (Campaign[] memory) {
        return campaigns;
    }

    function getActiveCampaigns() public view returns (Campaign[] memory) {
        uint activeCount = 0;
        for (uint i = 0; i < campaigns.length; i++) {
            if (campaigns[i].status == true) {
                activeCount++;
            }
        }

        Campaign[] memory activeCampaigns = new Campaign[](activeCount);
        uint counter = 0;
        for (uint i = 0; i < campaigns.length; i++) {
            if (campaigns[i].status == true) {
                activeCampaigns[counter] = campaigns[i];
                counter++;
            }
        }
        return activeCampaigns;
    }

    function getInactiveCampaigns() public view returns (Campaign[] memory) {
        uint inactiveCount = 0;
        for (uint i = 0; i < campaigns.length; i++) {
            if (campaigns[i].status == false) {
                inactiveCount++;
            }
        }

        Campaign[] memory inactiveCampaigns = new Campaign[](inactiveCount);
        uint counter = 0;
        for (uint i = 0; i < campaigns.length; i++) {
            if (campaigns[i].status == false) {
                inactiveCampaigns[counter] = campaigns[i];
                counter++;
            }
        }
        return inactiveCampaigns;
    }

    function deleteCampaign(uint _campaignId) public {
        require(
            campaigns[_campaignId].campaignOwner == msg.sender,
            "You are not the owner of this campaign"
        );
        require(
            campaigns[_campaignId].status == true,
            "Campaign is already inactive"
        );
        campaigns[_campaignId].status = false;
    }

    function editCampaign(
        uint _campaignId,
        string memory _campaignTitle,
        string memory _campaignDescription,
        string memory _campaignImageCID
    ) public {
        require(
            campaigns[_campaignId].campaignOwner == msg.sender,
            "You are not the owner of this campaign"
        );
        require(campaigns[_campaignId].status == true, "Campaign is Inactive");
        campaigns[_campaignId].campaignTitle = _campaignTitle;
        campaigns[_campaignId].campaignDescription = _campaignDescription;
        campaigns[_campaignId].campaignImageCID = _campaignImageCID;
    }

    function contribute(uint _campaignID) public payable {
        require(campaigns[_campaignID].status == true, "Campaign is Inactive");
        require(
            campaigns[_campaignID].raisedAmount <=
                campaigns[_campaignID].targetAmount,
            "Target amount reached"
        );
        campaigns[_campaignID].raisedAmount += msg.value;
        contributions.push(
            Contribution(
                _campaignID,
                contributionId,
                msg.value,
                block.timestamp,
                payable(msg.sender)
            )
        );
        contributionId++;
    }

    function getAllContributions() public view returns (Contribution[] memory) {
        return contributions;
    }

    function getAllContributionsForParticularCampaign(
        uint _campaignId
    ) public view returns (Contribution[] memory) {
        uint count = 0;
        for (uint i = 0; i < contributions.length; i++) {
            if (contributions[i].campaignId == _campaignId) {
                count++;
            }
        }

        Contribution[] memory campaignContributions = new Contribution[](count);
        uint counter = 0;
        for (uint i = 0; i < contributions.length; i++) {
            if (contributions[i].campaignId == _campaignId) {
                campaignContributions[counter] = contributions[i];
                counter++;
            }
        }
        return campaignContributions;
    }

    function totalContributions() public view returns (uint) {
        return contributions.length;
    }

    function claimContribution(uint _campaignId) public {
        require(campaigns[_campaignId].status == true, "Campaign is Inactive");
        require(
            campaigns[_campaignId].campaignOwner == msg.sender,
            "You are not the owner of this campaign"
        );
        require(
            campaigns[_campaignId].raisedAmount >=
                campaigns[_campaignId].targetAmount,
            "Target amount not reached"
        );

        campaigns[_campaignId].status = false;
        campaigns[_campaignId].campaignOwner.transfer(
            campaigns[_campaignId].raisedAmount
        );
    }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706896180066/d6fe71e6-e37f-4fc7-a15e-47bec56df6a6.jpeg align="center")

## **Contract Structure**

The CrowdFunding smart contract is written in Solidity and comprises essential components:

**1\. Campaign Structure:**

* **campaignId:** A unique identifier for each campaign.
    
* **campaignTitle:** The title of the campaign.
    
* **campaignDescription:** A brief description of the campaign's goals.
    
* **campaignImageCID:** A link to an image representing the campaign.
    
* **targetAmount:** The funding goal to be reached.
    
* **raisedAmount:** The total amount of funds raised so far.
    
* **startAt:** The timestamp when the campaign starts.
    
* **endAt:** The timestamp when the campaign ends.
    
* **status:** Indicates whether the campaign is active or inactive.
    
* **campaignOwner:** The address of the person who created the campaign.
    

**2\. Contribution Structure:**

* **campaignId:** The ID of the campaign to which the contribution belongs.
    
* **contributionId:** A unique identifier for each contribution.
    
* **amount:** The amount of funds contributed.
    
* **date:** The timestamp when the contribution was made.
    
* **contributor:** The address of the person who made the contribution.
    

**Key Functions:**

**Campaign Management:**

* **createCampaign:** Allows users to create new campaigns.
    
* **getCampaigns:** Retrieves a list of all campaigns.
    
* **getActiveCampaigns:** Retrieves a list of active campaigns.
    
* **getInactiveCampaigns:** Retrieves a list of inactive campaigns.
    
* **getParticularCampaign:** Retrieves information about a specific campaign.
    
* **editCampaign:** Allows campaign owners to edit campaign details.
    
* **deleteCampaign:** Allows campaign owners to delete inactive campaigns.
    

**Contribution Handling:**

* **contribute:** Allows users to contribute funds to a campaign.
    
* **getAllContributions:** Retrieves a list of all contributions.
    
* **getAllContributionsForParticularCampaign:** Retrieves contributions for a specific campaign.
    

**Fund Distribution:**

* **claimContribution:** Allows campaign owners to claim raised funds if the target amount is reached.
    

## **Benefits of Using a Smart Contract:**

* **Trust and Transparency:** The blockchain's transparent and immutable nature ensures that all transactions and campaign data are publicly verifiable, building trust among participants.
    
* **Efficiency:** Smart contracts automate various processes, streamlining campaign management and contribution handling.
    
* **Security:** Funds are held securely on the blockchain, reducing the risk of fraud or misappropriation.
    
* **Reduced Costs:** Smart contracts eliminate the need for intermediaries, potentially lowering administrative fees associated with traditional crowdfunding platforms.
    

## **zkfund Project:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706896197047/73463dd4-23cf-40f6-93a2-d45c65b719c5.png align="center")

The CrowdFunding smart contract discussed in this blog is part of a larger crowdfunding project called zkfund, accessible on GitHub: [https://github.com/moayaan1911/crowdfunding](https://github.com/moayaan1911/crowdfunding)

## **Conclusion**

Blockchain-based crowdfunding platforms offer compelling advantages in terms of trust, transparency, efficiency, and security. As blockchain technology continues to evolve, we can expect to see further innovations in crowdfunding and other financial applications, empowering individuals and organizations to raise funds in a more secure and decentralized manner.