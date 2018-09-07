## Creating Smart Contracts with Truffle

### Intro

This page should be used if you wish to begin [Truffle](https://truffleframework.com/) based development/test of Smart Contracts.

### Setup steps

#### 1. Install NODE-JS

##### Windows

Click [here](https://www.wikihow.com/Install-Node.Js-on-Windows) for installation steps in windows.


#### 2. Install Truffle

```bash
npm install truffle
```

#### 3. Install TestRPC

```bash
npm install ethereumjs-testrpc
```

#### 4. Create and test your new Truffle project

A **Truffle Project** contains:

1. Files representing the smart contracts
2. Configuration files for smart object deployment
3. Test files which are used to test the smart object deployment

#### a. Create a folder which will contain you files. This will be your project folder.

```bash
mkdir ~/projects/mysmartcontracts
```

#### b. Initialise your project with truffle

```bash
truffle init
```
#### c. Launch TestRPC from ANOTHER bash terminal

```bash
# from another bash terminal type ...
testrpc
```
#### d. Test your new environment: truffle test

```bash
# from another bash terminal type ...
truffle test
```

Output should be similar to the following:

```bash
Compiling .\contracts\Migrations.sol...


  0 passing (0ms)


Des.McCarter@LPT2903 MINGW64 ~/projects/mysmartcontracts
```

### Create and Test a simple smart contract


#### 1. Create a new file named contracts/Demo.sol

```bash
>contracts/demo.sol
```

Now edit the file and insert the following code:

#### 2. Add Solidy Pragma

```solidity
pragma solidity ^0.4.11;
```

#### 3. Add your contact

```solidity
pragma solidity ^0.4.11;

contract Demo {

}
```

#### 4. Add a variable to your contact

```solidity
pragma solidity ^0.4.11;

contract Demo {
	string public name = "des";
}
```


