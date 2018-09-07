## Creating Smart Contracts with Truffle

### Intro

This page should be used if you wish to begin [Truffle](https://truffleframework.com/) based development/test of Smart Contracts.

### 1. Install NODE-JS

#### Windows

Click [here](https://www.wikihow.com/Install-Node.Js-on-Windows) for installation steps in windows.


### 2. Install Truffle

```bash
npm install truffle
```

### 3. Install TestRPC

```bash
npm install ethereumjs-testrpc
```

### 4. Create and test your ne Truffle project

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


