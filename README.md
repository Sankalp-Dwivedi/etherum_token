# Holocoin Smart Contract

## Overview

Holocoin is an ERC-20 compliant token built on the Ethereum blockchain. This smart contract defines a custom token named "SANKCOIN" with the abbreviation "SANK." The contract includes functionalities for minting and burning tokens, as well as keeping track of token balances for each address.

## Features

1. **Public Variables:**
   - `name`: Stores the name of the token ("SANKCOIN").
   - `abbrv`: Stores the abbreviation of the token ("SANK").
   - `supply`: Stores the total supply of the token.

2. **Mapping:**
   - `balances`: Maps each address to its token balance.

3. **Mint Function:**
   - The `mint` function allows new tokens to be created and assigned to a specified address. It takes two parameters:
     - `_address`: The address to which the new tokens will be added.
     - `_value`: The amount of new tokens to be created.

4. **Burn Function:**
   - The `burn` function allows tokens to be destroyed from a specified address. It takes two parameters:
     - `_address`: The address from which the tokens will be deducted.
     - `_value`: The amount of tokens to be burned.
   - The function includes a check to ensure the address has enough tokens to burn the specified amount.

## Smart Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract Holocoin {

    // Public variables
    string public name = "SANKCOIN";
    string public abbrv = "SANK";
    uint public supply = 0;

    // Mapping variable
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        supply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) {
            supply -= _value;
            balances[_address] -= _value;
        }
    }
}
```

## Functions

### Mint Function

```solidity
function mint(address _address, uint _value) public {
    supply += _value;
    balances[_address] += _value;
}
```

- **Description:** Creates new tokens and assigns them to the specified address.
- **Parameters:**
  - `_address`: The address receiving the new tokens.
  - `_value`: The number of tokens to mint.

### Burn Function

```solidity
function burn(address _address, uint _value) public {
    if (balances[_address] >= _value) {
        supply -= _value;
        balances[_address] -= _value;
    }
}
```

- **Description:** Destroys tokens from the specified address, reducing the total supply.
- **Parameters:**
  - `_address`: The address from which tokens will be burned.
  - `_value`: The number of tokens to burn.
- **Condition:** Ensures that the address has enough tokens to burn.

## Deployment

To deploy the Holocoin smart contract, follow these steps:

1. Install a development environment like Remix IDE or Truffle.
2. Copy the contract code into a new Solidity file (e.g., `Holocoin.sol`).
3. Compile the contract using the Solidity compiler.
4. Deploy the contract to the Ethereum network using your preferred method (Remix, Truffle, or other deployment tools).

---
