# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
## REGISTER NUMBER: 212224110018

# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


<img width="1907" height="1095" alt="image" src="https://github.com/user-attachments/assets/3906bad7-c5a7-4b63-b059-029b26ac10b3" />

Ownership is transferred at every checkpoint.

<img width="1913" height="1092" alt="image" src="https://github.com/user-attachments/assets/6235c1f6-118f-43ce-9e53-f416e9177bb0" />


Buyers can check the authenticity before purchasing.

<img width="1912" height="1085" alt="image" src="https://github.com/user-attachments/assets/3386d2a2-7885-4b97-bf83-dfd8490d41b5" />


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Hence we implemented code for a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
