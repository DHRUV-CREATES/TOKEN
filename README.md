# Project: TOKEN
# Simple Overview
This smart contract provides a simple framework for managing a token system where you can create and destroy tokens as needed. The smart contract includes functionalities to mint new tokens, burn existing tokens, and keep track of balances for each address.

# Description

## Public Variables
 - `tokenName`: It is the name of the token.
  - `tokenAbbrv`: It is the abbreviation of the token name.
  - `totalSupply`: It is the total number of tokens in existence.

## Mappings
- `balances`:It tracks that how many tokens each person have.
## Functions
- `mint`: It creates new tokens and Increases the total supply and the balance of a specified address.
- `burn`: It destroy the tokens and Decreases the total supply and the balance of a specified address, ensuring that the balance is sufficient for the burn operation.
## Copy code solidity Contract Code
       
- Copy the following code and paste it into `eth_beg`:
     ```solidity
     // SPDX-License-Identifier: MIT
     pragma solidity 0.8.18;

     /*
            REQUIREMENTS
         1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
         2. Your contract will have a mapping of addresses to balances (address => uint)
         3. You will have a mint function that takes two parameters: an address and a value. 
            The function then increases the total supply by that number and increases the balance 
            of the “sender” address by that amount
         4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
            It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
            and from the balance of the “sender”.
      5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
            to the amount that is supposed to be burned.
     */

    
    contract MyToken {
   // Public variables
     string public tokenName = "Dhruv";
     string public tokenAbbrv = "DRV";
     uint256 public totalSupply;
     
     // Mapping to track balances of addresses
     mapping(address => uint256) public balances;
     
     // Events to log token minting and burning
     event Mint (address indexed to, uint256 amount);
     event Burn (address indexed from, uint256 amount);
     
     // Mint function to create new tokens and increase the total supply and the balance of a specified address
     function mint (address to, uint256 amount) public {
     totalSupply += _amount;
     balances [_to] += __amount;
     emit Mint(_to, _amount);
     
     // Burn function to destroy tokens and decrease the total supply and the balance of a specified address
     function burn (address _from, uint256 amount) public {
     require (balances [_from] >= _amount, "Insufficient balance"); // Check if the balance is sufficient
     totalSupply = _amount;
     balances[_from] -= _amount;
     emit Burn(_from, _amount);
     }

# HOW TO RUN IN REMIX 
1. **Create a New File**
   - In the file explorer panel, click on the "+" icon to create a new file and name it MyToken.sol.

2 **Copy the Contract Code** 
  - Copy the simplified contract code provided earlier and paste it into MyToken.sol.
    
3 **Compile the Contract** 
  - In the Remix sidebar, go to the "Solidity Compiler" tab. 
  - Select the correct version of Solidity (0.8.18 in this case). 
  - Click on "Compile MyToken.sol" to compile the contract.

4 **Deploy the Contract** 
  - Switch to the "Deploy & Run Transactions" tab. 
  - Ensure that the correct contract (MyToken.sol) is selected. 
  - Choose the environment (e.g., JavaScript VM for a quick test). 
  - Click on "Deploy" to deploy the contract.

5 **Interact with the Contract** 
  - Once deployed, you can interact with the contract using the provided functions (mint and burn).

Mint Tokens: Use the mint function to create new tokens. Enter the recipient address and the amount of tokens to mint.
Burn Tokens: Use the burn function to destroy tokens. Enter your address (or any address with tokens) and the amount of tokens to burn.
Check Balances: You can check the balances of different addresses by accessing the balances mapping directly.

**Verify Events** : In the "Console" tab, you can see the emitted events (Mint and Burn) when tokens are minted or burned.

