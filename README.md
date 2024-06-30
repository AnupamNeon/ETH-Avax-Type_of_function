
# ERC20 token
This Solidity program is an ERC-20 token contract named "myTokens". It demonstrates the basic functionality of the ERC-20 token standard, including minting, transferring, and burning tokens. This program is designed for those who are new to Solidity and ERC-20 token development on the Ethereum blockchain.

## Getting Started

### Executing Program
1. Open Remix IDE or your preferred development environment.
2. Copy the MyToken contract code into a new Solidity file (e.g., MyToken.sol).
3. Compile the contract using Solidity version 0.8.24.
4. Deploy the contract to a local blockchain or any Ethereum testnet/mainnet.


```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.24;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract myTokens is ERC20, Ownable {
    // Constructor
    constructor() ERC20("Anupam", "Akm") Ownable(msg.sender) {}

    // Mint new coins
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Burn coins
    function burn(uint256 amount) public {
        require(amount > 0, "Transfer amount must be greater than 0");
        require(balanceOf(msg.sender) >= amount, "Not enough coins to burn"); 
        _burn(msg.sender, amount);
    }

    // Transfer coins
    function transferTokens(address receiver, uint256 amount) external {
        require(amount > 0, "Transfer amount must be greater than 0");
        require(balanceOf(msg.sender) >= amount, "Not enough coins to transfer"); 
        approve(msg.sender, amount);
        transferFrom(msg.sender, receiver, amount);
    }
}
```

## Authors

Anupam Kumar
- [@AnupamNeon](https://github.com/AnupamNeon)


## License

This project is licensed under the MIT License - see the LICENSE file for details.

