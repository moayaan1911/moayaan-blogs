# WEB3 and Social Media

In recent years, social media has become a ubiquitous aspect of our daily lives, affecting the way we communicate, share information and interact with each other. However, despite its widespread use and impact, social media platforms have faced numerous criticisms, particularly in terms of privacy, security, and ownership of data. This is where blockchain technology, Web3, and Ethereum come into the picture.

## What is Blockchain?

Blockchain, at its core, is a decentralized, secure and transparent ledger that records transactions across a network of computers. This technology enables individuals to have control over their data, as it is not stored in a centralized location, making it difficult for third parties to access and manipulate the information. Additionally, transactions on the blockchain are recorded on multiple nodes, making it nearly impossible to alter the data.

## Ethereum

Web3 and Ethereum are two terms that are closely related to blockchain technology. Web3 refers to a decentralized web where users can interact with each other directly, without intermediaries. Ethereum, on the other hand, is an open-source blockchain platform that enables developers to build decentralized applications (dapps) and smart contracts.

## Benefits of a "WEB3" Social Media

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675971206253/c02b5ce7-bdcd-4797-9e3c-66d8d2237d7e.jpeg align="center")

1. ### Decentralized Ownership of Data:
    
    With blockchain, users have complete control over their data and information. They can choose to share it or keep it private, without fear of it being misused or exploited by third parties.
    
2. ### Improved Privacy and Security:
    
    Blockchain technology provides a secure and tamper-proof environment for users to interact with each other. Transactions and data stored on the blockchain cannot be altered or deleted, making it an ideal solution for sensitive information.
    
3. ### Increased User Rewards:
    
    Currently, social media platforms profit from the user data they collect, which is then sold to advertisers. With blockchain, users can be rewarded for their contributions, such as creating and sharing content, participating in surveys, and more.
    
4. ### Decentralized Social Networks:
    
    Decentralized social networks can be built on the blockchain, enabling users to connect and interact with each other directly. This eliminates the need for intermediaries, such as Facebook or Twitter, to control user data.
    
5. ### Transparent Advertising:
    
    With blockchain and smart contracts, advertisers can be assured that their advertisements reach their target audience, while users can control the types of advertisements they receive.
    

## Companies Working on DeSoMe (Decentralized Social Media)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675971346090/7867e14d-54cc-438c-9cfb-48843a0be158.jpeg align="center")

1. ### Minds:
    
    Minds is a decentralized social network that aims to provide a more open and transparent environment for its users. The platform is built on the Ethereum blockchain and rewards users for their contributions, such as creating and sharing content. Additionally, Minds aims to provide a secure and private environment for its users, giving them complete control over their data.
    
2. ### Steemit:
    
    Steemit is a decentralized social media platform that rewards its users for creating and curating content. The platform operates on the Steem blockchain, which enables users to earn rewards in the form of Steem cryptocurrency for their contributions. Additionally, Steemit aims to provide a more equitable and democratic environment for its users, as the rewards are distributed based on the popularity of the content.
    
3. ### Flixxo:
    
    Flixxo is a decentralized social network for video content. The platform operates on the Ethereum blockchain and enables users to create, share, and monetize their video content. Additionally, Flixxo aims to provide a more secure and transparent environment for its users, as all transactions on the platform are recorded on the blockchain.
    
4. ### Voice:
    
    Voice is a decentralized social media platform that aims to provide a more authentic and transparent environment for its users. The platform operates on the EOS blockchain and rewards users for their contributions, such as creating and sharing content. Additionally, Voice aims to provide a more secure and private environment for its users, giving them complete control over their data.
    
5. ### Lens Protocol:
    
    Lens is a decentralized social media platform built on the Ethereum blockchain. It aims to provide a secure, transparent, and equitable environment for its users, where they can interact with each other directly without intermediaries. The platform enables users to monetize their content and data, giving them complete control over their information. Additionally, Lens provides a user-friendly interface that enables users to easily create and share content, as well as discover and explore new content created by others. The platform leverages the power of blockchain technology to create a more democratic and equitable social media experience, where users are rewarded for their contributions. The Lens protocol is designed to provide a decentralized alternative to existing centralized social media platforms, giving users more control over their data and information.
    

## Example Smart Contract of social media

```solidity
pragma solidity ^0.8.0;

contract SocialMedia {
    // mapping to store user profile data
    mapping (address => User) public users;

    // structure to represent user profile
    struct User {
        string username;
        string bio;
        bytes32 profilePicHash;
    }

    // function to update user profile
    function updateProfile(string memory _username, string memory _bio, bytes32 _profilePicHash) public {
        users[msg.sender].username = _username;
        users[msg.sender].bio = _bio;
        users[msg.sender].profilePicHash = _profilePicHash;
    }

    // function to retrieve user profile data
    function getProfile(address _user) public view returns (string memory, string memory, bytes32) {
        return (users[_user].username, users[_user].bio, users[_user].profilePicHash);
    }
}
```

This smart contract allows users to update their profile information, including their username, bio, and profile picture. The profile picture is stored as a hash on the blockchain, and the actual image can be stored off-chain, for example, on IPFS. The `updateProfile` function enables users to update their profile information, and the `getProfile` function allows other users to retrieve the profile information of any user on the platform.

*Note that this is just a basic example, and a more complex smart contract could include additional features such as content creation, voting, and monetization. Additionally, security measures such as access control and error handling could also be added to ensure the integrity and reliability of the platform.*

## Conclusion

In conclusion, blockchain, Web3, and Ethereum have the potential to revolutionize the way we interact on social media. By providing users with control over their data, improved privacy and security, and rewards for their contributions, social media can become a more equitable and user-friendly environment. As the technology continues to evolve and mature, we can expect to see more and more innovative applications that leverage the power of the blockchain to change the way we interact with each other online.