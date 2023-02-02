# Cryptography in Blockchain

Cryptography is an essential component of blockchain technology and is used to ensure the security of transactions and the confidentiality of sensitive information stored on the blockchain. Cryptography uses mathematical algorithms to encode and decode data, making it unreadable to anyone except those who have the proper decryption key. This helps to prevent unauthorized access and manipulation of the data stored on the blockchain.

## Types of Cryptography

There are several different types of cryptographic algorithms that are used in blockchain technology, including symmetric-key cryptography, asymmetric-key cryptography, and hash functions.

### Symmetric-key cryptography

Symmetric-key cryptography, also known as secret key cryptography, uses the same key for both encryption and decryption. An example of a symmetric-key algorithm is the Advanced Encryption Standard (AES), which is widely used to secure sensitive information.

### Asymmetric-key cryptography

Asymmetric-key cryptography, also known as public key cryptography, uses two different keys for encryption and decryption. The encryption key is made publicly available, while the decryption key is kept private. This allows users to encrypt messages that can only be decrypted by the intended recipient. An example of an asymmetric-key algorithm is the RSA algorithm, which is commonly used for secure communication and digital signatures.

## Cryptography in Blockchain

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675340808542/0ca871df-65e8-477d-8177-75c8bb3523db.png align="center")

In the blockchain, the most widely used cryptographic techniques are asymmetric-key cryptography and hash functions. Asymmetric-key cryptography is used to generate digital signatures, which are used to prove the authenticity of transactions. Hash functions are used to ensure the integrity of the data stored on the blockchain and to secure the hashes that link blocks together in the blockchain.

In the world of blockchain, some of the most commonly used cryptographic algorithms include SHA-256, Ethash, and Elliptic Curve Digital Signature Algorithm (ECDSA). SHA-256 is used for hashing and verifying data, while Ethash is used as the mining algorithm in the Ethereum blockchain. ECDSA, on the other hand, is used for digital signatures to secure transactions and provide proof of ownership. Additionally, Advanced Encryption Standard (AES) is also frequently used for encryption and decryption of data in blockchain. The most widely used cryptography algorithm in blockchain is dependent on the specific implementation and requirements of each individual blockchain network.

## SHA-256

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675340814884/fa8f4030-067a-4204-a70b-4b2b70dbdb04.jpeg align="center")

SHA-256, also known as Secure Hash Algorithm 256-bit, is a widely used cryptography algorithm in the blockchain technology. It is a hash function that takes in any input of any length and produces a fixed-length output of 256 bits. This algorithm is used for various purposes in blockchain, including verifying the integrity of data, secure digital signatures, and validating transactions.

SHA-256 is a one-way function, meaning that it is computationally infeasible to reverse the process of the hash function and obtain the original input from the hashed output. This makes SHA-256 an important tool for maintaining the security and privacy of data in blockchain. Additionally, any change to the input data will result in a completely different hash value, making it easy to detect any tampering or changes to the original data.

Another important feature of SHA-256 is its collision resistance. A hash collision occurs when two different inputs produce the same hash value. In blockchain, this can lead to significant security vulnerabilities, as it could allow an attacker to alter the original data in such a way that it still generates the same hash value. The SHA-256 algorithm has been designed to be collision-resistant, making it a secure option for use in blockchain applications.

## Ethash

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675340824869/1a025fab-e52b-4bab-947a-2efb222d725c.jpeg align="center")

Ethash is a Proof of Work (PoW) mining algorithm used in the Ethereum blockchain network. It is designed to be ASIC-resistant, meaning that it is intended to be more democratic in the sense that it can be mined with a regular computer or graphics card, as opposed to specialized mining equipment. This helps to distribute the mining rewards more evenly among the network participants and prevent centralization.

One of the key features of Ethash is its use of a DAG (Directed Acyclic Graph) which is generated for each epoch (30,000 blocks) and serves as the basis for mining. The DAG is stored in memory and used as input for the mining process, which involves finding a nonce (a random number) that, when combined with the block header, results in a hash value that meets the required difficulty target. The miner who finds the solution first is rewarded with Ether, the cryptocurrency used in the Ethereum network.

The use of a DAG in Ethash helps to make the mining process more memory-hard, which increases the difficulty of developing specialized hardware (ASICs) to mine Ethereum. This helps to maintain the decentralization of the network and prevent the concentration of mining power in the hands of a few individuals or organizations. Additionally, Ethash also provides a degree of randomness in the mining process, making it more difficult for miners to predict the outcome and optimize their mining operations.

## Elliptic Curve Digital Signature Algorithm

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675340834184/5cb0760e-94f2-4744-a4de-87d95313296d.png align="center")

Elliptic Curve Digital Signature Algorithm (ECDSA) is a widely used public-key cryptography algorithm in the blockchain technology. It provides a secure way of verifying the authenticity of digital signatures, which are used to prove the ownership of assets in the blockchain. In the ECDSA, the private key is used to sign the data, while the public key is used to verify the signature.

ECDSA is based on the mathematics of elliptic curve cryptography, which provides a highly secure method of encryption. The use of elliptic curves in cryptography was first introduced by mathematicians in the mid-1980s and has since become a widely adopted method of securing data in various fields, including blockchain. In ECDSA, the private key is used to generate a digital signature, which is then verified using the public key. This ensures that the signature can only be produced by the owner of the private key and provides a secure way of verifying the authenticity of the signature.

The security of ECDSA is based on the mathematical properties of elliptic curves, which make it computationally infeasible to find the private key from the public key. This helps to protect the privacy of the private key and ensure the security of the digital signature. Additionally, ECDSA also provides a degree of non-repudiation, meaning that the owner of the private key cannot deny having signed the data. This helps to ensure the integrity of the data and provide a secure way of validating transactions in the blockchain.

## Advanced Encryption Standard

Advanced Encryption Standard (AES) is a widely used symmetric-key encryption algorithm in the field of cryptography. It is a block cipher, meaning that it encrypts data in fixed-size blocks, and it uses a fixed-length key for both encryption and decryption. AES was first adopted by the U.S. government in 2001 and has since become a widely used encryption standard in various industries, including blockchain.

AES is considered to be a highly secure encryption algorithm, as it has been rigorously tested and reviewed by cryptography experts. It uses a substitution-permutation network (SPN) structure, which provides a high level of security by performing multiple rounds of substitution and permutation operations on the data. The length of the key used in AES determines the number of rounds performed, with longer keys providing a higher level of security.

One of the key advantages of AES is its high speed, which makes it well-suited for use in real-time applications. Additionally, AES is flexible and can be easily integrated into various hardware and software systems, making it a popular choice for encryption in the blockchain. AES can also be used in various modes of operation, such as ECB (Electronic Code Book), CBC (Cipher Block Chaining), and CTR (Counter), each of which provides a different level of security and is suited for different use cases.

## Implementation of SHA-256

```python
import hashlib

def sha256(data):
    sha = hashlib.sha256()
    sha.update(data.encode())
    return sha.hexdigest()

message = "This is a message to be hashed using SHA-256"
hashed_message = sha256(message)

print("Original Message: ", message)
print("Hashed Message: ", hashed_message)
```

In this program, the `sha256` function takes in a string `data` as input, creates a SHA-256 hash object using the `hashlib.sha256()` function, and updates the hash object with the encoded version of the input data using the `update` method. Finally, the hexadecimal representation of the hash is returned using the `hexdigest` method.

The message to be hashed is assigned to the variable `message`, and the hashed message is obtained by calling the `sha256` function with `message` as its argument. The original message and the hashed message are then printed to the console.

## Conclusion

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675340843020/989c22e7-29b1-4af0-8899-5b24196157ec.jpeg align="center")

In conclusion, cryptography plays a crucial role in the security and privacy of the blockchain technology. By using various cryptographic algorithms, blockchain systems are able to protect the confidentiality of data and verify the authenticity of transactions. Different algorithms have different strengths and weaknesses, and the choice of which to use depends on the specific needs of the application.

SHA256 and Ethash are two of the most widely used cryptographic algorithms in the blockchain. SHA256 is used for proof-of-work in many blockchain systems, while Ethash is used in the Ethereum blockchain. AES, ECDSA, and Elliptic Curve Digital Signature Algorithm are also widely used in the blockchain, each providing a different level of security and efficiency. Additionally, these algorithms have undergone extensive testing and review, ensuring their security and making them well-suited for use in the blockchain.