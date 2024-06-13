# MyToken - LUCKCOIN (LKCN)

## Overview

This is a simple smart contract implemented using the solidity language which allows the minting as well as burning of tokens associated with different addresses.
## Features

- **Minting:** Add new tokens to an address's balance.
- **Burning:** Remove tokens from an address's balance.
- **Bonus Minting:** Automatically mint an additional 100 tokens if the balance reaches exactly 100 tokens.
- **Penalty Burning:** Automatically burn an additional 200 tokens if the balance reaches exactly 1000 tokens.

## Public Variables

- `tokenName`: The name of the token. (LUCKCOIN)
- `tokenAbbrv`: The abbreviation of the token. (LKCN)
- `totalSupply`: The total supply of tokens in circulation.
- `balances`: A mapping of addresses to their respective token balances.

## Functions

### `mint`

```solidity
function mint(address _address, uint _value) public
```
### `burn`

```solidity
function burn(address _address, uint _value) public
```

## Getting Started
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., MyToken.sol). Copy and paste the following code into the file:

```solidity
/SPDX-License-Identifier: MIT
pragma solidity 0.8.26;
contract MyToken {

    // public variables here
    string public tokenName = "LUCKCOIN";
    string public tokenAbbrv = "LKCN";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;

        // Check if balance is exactly 100 coins after minting
        if(balances[_address] == 100) {
            totalSupply += 100;
            balances[_address] += 100;
        }
        
    }

    // burn function
    function burn(address _address, uint _value) public {
        if(balances[_address] >= _value){
            totalSupply -= _value;
            balances[_address] -= _value;
        }

        // Check if balance is exactly 1000 coins after burning
        if(balances[_address] == 1000) {
            totalSupply -= 200;
            balances[_address] -= 200;
        }
    }

}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.26" (or another compatible version), and then click on the "Compile MyToken.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the calling the mint function to add tokens for an address and use call the burn function to destroy the tokens for an address.

## Minting Tokens
To mint tokens to an address, call the mint function with the desired address and amount, If the address balance reaches exactly 100 tokens, an additional 100 tokens will be automatically minted.

## Burning Tokens
To burn tokens from an address, call the burn function with the desired address and amount, If the address balance reaches exactly 1000 tokens after burning, an additional 200 tokens will be automatically burned.

## Authors
Rushil Kumar

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
