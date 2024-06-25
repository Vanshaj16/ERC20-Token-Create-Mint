# Project: Create and Mint Token
This repository is used to create and mint the ERC20 token using the solidity. The contract includes functionality for minting, burning, and transferring tokens. The contract owner can mint new tokens to a specified address, and any user can burn and transfer their own tokens.

## Description
### Features
1. Standard ERC20 token functionality
2. Ownership management using OpenZeppelin's Ownable contract
3. Owner-only minting function
4. Public burning and transfer function for token holders
### ERC20 standard interface has following functions and events:
1. Total Supply: The total number of tokens that will ever be issued
2. Balance Of: The account balance of a token owner's account
3. Transfer: Automatically executes transfers of a specified number of tokens to a specified address for transactions using the token
4. Transfer From: Automatically executes transfers of a specified number of tokens from a specified address using the token
5. Approve: Allows a spender to withdraw a set number of tokens from a specified account, up to a specific amount
6. Allowance: Returns a set number of tokens from a spender to the owner
7. Transfer: An event triggered when a transfer is successful (an event)
8. Approval: A log of an approved event (an event)
### ERC20Token contract has following functions and events:
1. Mint Function: Allows the owner to mint new tokens to a specified address.
2. Burn Function: Allows any token holder to burn their tokens.
3. Renounce Ownership: The renounceOwnership function from Ownable is overridden to allow the owner to renounce their ownership.
### Prerequisites
1. MetaMask: A browser extension for interacting with the Ethereum network.
2. Remix IDE: An online IDE for Solidity smart contract development.

## Getting Started
### Executing program
1. Go to Remix IDE.
2. Create a New Solidity File: In the "File Explorer" pane on the left, click the "+" button to create a new file.
3. Name your file ERC20Token.sol
   
Copy and paste the following code into ERC20Token.sol:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract ERC20Token is ERC20, Ownable(msg.sender){
constructor() ERC20("Jimmy Coin", "JC") {
    _mint(msg.sender, 1_000_001* 10 ** 18);
}
    
    function mint(address to, uint amount) public{
        _mint(to, amount);
    }

    function burn(uint amount) public {
        _burn(msg.sender, amount);
    }
    
     // Transfer function is already provided by the ERC20 standard. 
     // But we can call this function by redefining it using the super keyword.
    function transfer(address recipient, uint256 amount) public override returns (bool) {
        return super.transfer(recipient, amount);
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.20" (or another compatible version), and then click on the "Compile ERC20Token.sol" button.

Once the code is compiled, in the "Deploy & run transaction" change the environment to "Injected Provider-MetaMask" then select the ERC20Token contract and click on the deploy button.
Test the contract by input the value in the status bar.

## Authors

Vanshaj

vanshajsen16@gmail.com
