# ETH Proof Beginner EVM Course Project
This Solidity program contract provides basic functionalities to mint new tokens and burn existing ones, 
following the specified requirements.

## Description
This repository contains a Solidity smart contract for creating custom tokens on the Ethereum blockchain. The program was
created and compiled on Remix, an online Solidity IDE. https://remix.ethereum.org/.


### REQUIREMENTS
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
## Getting Started
### Executing program
Once you are on the Remix IDE, create a new file by clicking on the "+" icon in the left-hand sidebar.
Save the file with a .sol extension (e.g., myToken.sol).
Copy and paste the following code into the file:

```

// SPDX-License-Identifier: MIT
pragma solidity 0.8.26;

contract EtherAss {
    // public variables
    string public tkName="Hello";
    string public tkAbbrv ="META";
    uint public totalSupply=0;

    // mapping variable
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option 
is set to "0.8.26" (or another compatible version), and then click on the "Compile EthAss.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand
sidebar. Select the "EthAss.sol" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the tkName, tkAbbrv, totalSupply in order to check the 
Token Name, Abbreviation and total supply of the tokens. You can also use the mint function in order to add tokens to an address 
while burn function to destroy tokens of an address. Speaking of addresses, you can use a default address provided by the IDE,
to do this look for a label "ACCOUNT" there you can see all the sample account provided by the IDE. Now, copy the address by clicking
the "Copy account to clipboard" symbol. After copying the desired account you can now paste it on the address field of the balances, 
burn and mint functions then just put a value you want to mint or burn for that address. Lastly, after the fields are now populated
you can now click "transact" in order to call the burn and mint functions.

## Authors
Siddhartha Chaurasia
@siddh8a

## License
This project is licensed under the MIT License.
