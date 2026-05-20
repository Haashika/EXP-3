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
<img width="1128" height="619" alt="Screenshot 2026-05-20 110929" src="https://github.com/user-attachments/assets/dfd8c049-89e3-42af-8a6b-c8712d02503a" />




Ownership is transferred at every checkpoint.
<img width="1128" height="624" alt="Screenshot 2026-05-20 110945" src="https://github.com/user-attachments/assets/9194c01d-9560-4690-8684-4eac7e572b4c" />



Buyers can check the authenticity before purchasing.

<img width="1137" height="614" alt="image" src="https://github.com/user-attachments/assets/80fba0e0-35f5-4426-a15e-80f529115983" />


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Hence we implemented code for a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
