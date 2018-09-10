## Creating Smart Contracts with Truffle

### Basic Contract: Modify only allowed by specific account

This page will show you how to:

1. Create a contract with a public string variable
2. Add a public method which will be used to change this variable
3. Add a method to check that the account calling modify is valid
4. Make a change to the variable by correct account
5. Attempt to make a change to variable using different account
6. Test that variable still equal to first change


### Steps

#### 1. Create a new Contract named contracts/Demo.sol

```bash
>contracts/Demo.sol
```

Now edit the file and insert the following code:

#### 2. Edit Contract

```solidity
pragma solidity ^0.4.11;

contract Demo {
	string public name;

	address public owner = msg.sender;


	modifier onlyOwner(){
		require(msg.sender == owner);
		_;
	}

	function changeName(string _name) onlyOwner {
		name=_name;
	}
}
```

### 2. Deploy Smart Contract to TestRPC

To to the root of your new smart contracts folder and (in bash) type:

```bash
truffle migrate
```

### 3. Add chai-as-promised package

```bash
npm install chai-as-promised
```


### 4. Test your smart contract

#### 1. Create and Edit test file

Under the test folder create a new file named 01test.js and edit it. Paste the following text:

```javascript
// Import your smart object ...
var Demo = artifacts.require("Demo");

// Import 'expect' object from Chai package ...
chai = require("chai");
chaiAsPromised = require("chai-as-promised");
chai.use(chaiAsPromised);
expect = chai.expect;

// Tests can be nested in 3 levels: a. the *contract* b. *describe* and c. *it* ...

contract("Test the Demo contract", function(accounts){
	describe("Deploy the Demo smart contract", function(){
		it("Create a new instance of the smart contract", function(){
			return Demo.new().then(function(instance){
				demoContract = instance;
			});
		});
	});

	describe("Check the contract variables", function(){
		it("Change the variable name to Lisa", function(){
			return demoContract.changeName("Lisa").then(function(res){
				expect(res.toString()).to.not.be.an("error");
			});
		});

		it("Check the variable is set to Lisa", function(){
			return demoContract.name().then(function(res){
				expect(res.toString()).to.be.equal("Lisa");
			});
		});

		it("Change the variable name to Des using different account (this should fail)", function(){
			return demoContract.changeName("Des", {"from": accounts[1]}).then(function(res){
				expect(res.toString()).to.be.eventually.rejected;
			});
		});

		it("Check the variable is set to Lisa", function(){
			return demoContract.name().then(function(res){
				expect(res.toString()).to.be.equal("Lisa");
			});
		});
	});
});
```

#### 3. Run the test

```bash
$ truffle test
Using network 'development'.



  Contract: Test the Demo contract
    Deploy the Demo smart contract
      √ Create a new instance of the smart contract (82ms)
    Check the contract variables
      √ The name variable is Des


  2 passing (145ms)
```
