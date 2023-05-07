# CryzalisETH

This is a beginner Solidity Smart Contract to demonstrate the basics of Solidity. 

## Description

The contract contains 3 state variables including the Token Name, Token Abbreviation and Token Supply. 

It has a mapping (Adddress => uint) named balances mapping Addresses to their respective balances. 

It also contains 2 functions namely Mint and Burn which work as their name would suggest. Minting increases the total supply as well as the balance of person who runs this function by a certain value passed to the function as a parameter. 

Burn function checks whether the person who run the function has enough tokens and if they do, it reduces that amount of token from that person's balance as well as from the total supply. It utilizes the require keyword which throws an error if the condition is not met.


## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. Go to https://remix.ethereum.org/.

Once you are on the website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Test.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract MyToken {

    // public variables here
    string public tokenName = "Crizalys";
    string public tokenAbbr = "CZ";
    uint public totalSupply = 0;
    // mapping variable here
    mapping (address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply = totalSupply + _value;
        balances[_address] += _value; 
    } 

    function burn(address _address, uint _value) public {

        require(balances[_address] > _value,"balance not sufficient");
        // if(balances[_address] >= _value)
        // {
        totalSupply -= _value;
        balances[_address] -= _value;

        // }
    }

    // burn function

}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Test.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint or burn function. Click on the "MyToken" contract in the left-hand sidebar, and then click on the "mint" function. 

## Help

Make sure to have the compiler option set to 0.8.18 to avoid version depenedency errors. 
```
pragma solidity ^0.8.18
```

## Authors

  
[Dunking](https://twitter.com/dunkjn3022)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
