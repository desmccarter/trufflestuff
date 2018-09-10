## Creating Smart Contracts with Truffle

### Basic Contract: Simple Contact with static string

This page will show you how to:

1. Create a contract with a public string variable
2. Create a test to check the string variable

### Steps

#### 1. Create a new Contract named contracts/Demo.sol

```bash
>contracts/Demo.sol
```

Now edit the file and insert the following code:

#### 2. Edit Contract

Add *pragma* and the contract itself ...

```solidity
pragma solidity ^0.4.11;

contract Demo {
	string public name = "des";
}
```

### Deploy your new Smart Contract

#### 1. Edit JS file in migrations folder inserting deploy steps

```javascript
var Demo = artifacts.require("Demo");

module.exports = function(deployer){
	deployer.deploy(Demo);
};

```

#### 2. Deploy new Smart Contract to TestRPC

To to the root of your new smart contracts folder and (in bash) type:

```bash
truffle migrate
```


### Test your smart contract

#### 1. Install chai (adds BDD type context to your tests)

```bash
npm install chai
```

#### 2. Create and Edit test file

Under the test folder create a new file named 01test.js and edit it. Paste the following text:

```javascript
// Import your smart object ...
var Demo = artifacts.require("Demo");

// Import 'expect' object from Chai package ...
expect = require("chai").expect;

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
		it("The name variable is Des", function(){
			return demoContract.name().then(function(res){
				expect(res.toString()).to.be.equal("des");
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
