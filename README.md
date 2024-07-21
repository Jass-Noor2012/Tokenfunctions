# Tokenfunctions
This Solidity program is a simple "Mint,transfer and burn tokens" program that demonstrates functionality of Create and mint Token and burn and transfer  in Solidity programming language.
## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain.This Contract does three functions that are mint,burn and transfer functions.

## Getting Started
### Installing

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension.Copy and paste the following code into the file:

```javascript

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";


contract _MyTokenJasnoor is ERC20, Ownable {
    constructor(string memory tokenName,string memory symbol)
        ERC20(tokenName, symbol)
        Ownable(msg.sender)
    {}

    function _minttoken (address _sendto, uint256 _amount) public onlyOwner {
        require(_amount > 0, "Amount should be greater than zero");
        _mint(_sendto, _amount);
    }
 
    function burnMyTokens(uint256 _amount) public {
        if (_amount <= 0) {
            revert("Amount to burn should be greater than zero");
        }
        require(balanceOf(msg.sender) >= _amount, "Insufficient balance");
        _burn(msg.sender, _amount);
    }

    function customTransfer(address _to, uint256 _amount) public {
        require(_amount > 0, "Amount should be greater than zero");
        require(balanceOf(msg.sender) >= _amount, "Insufficient balance");

        _transfer(msg.sender, _to, _amount);
    }
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.20" (or another compatible version), and then click on the "Compile create and Myfunction.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "_MyTokenJasnoor" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the _minttoken, _burnthetoken, _Transferthetoken function. Click on the "_MyTokenJasnoor" contract in the left-hand sidebar, and then click on the  _minttoken, _burnthetoken, _Transferthetoken  function. Finally, click on the "transact" button to execute the function and retrieve the message.

## Authors

Jasnoor Kaur @Jass-Noor2012


## License

This project is licensed under the MIT License.
