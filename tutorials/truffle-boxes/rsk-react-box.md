---
layout: rsk
title: Using Truffle box rsk-react-box
tags: tutorial, rsk, truffle, truffle-box, react
description: "How to use the Truffle box rsk-react-box, which comes with everything you need to start using smart contracts from a react app on RSK networks. It includes network configurations for Mainnet, Testnet and the SimpleStorage contract as an example to deploy and run the react app."
render_features: "custom-terminals"
---

In this tutorial, I will show you step-by-step how to use the Truffle box [rsk-react-box](https://github.com/rsksmart/rsk-react-box), 
which comes with everything you need to build a fully decentralized application (DApp), start using smart contracts from a react app on RSK networks. It includes network configurations for Mainnet, Testnet and the SimpleStorage contract as an example to deploy and run the react app.

Check out [RSK Blockchain](https://developers.rsk.co/rsk/) to learn more.

# Overview

Here is a summary of the steps we will take in this tutorial:

1. Setup prerequisites;
2. Install RSK Truffle React Box;
3. Learn how to use the Truffle development console;
4. Do tests;
5. Run a local server;
6. Create a wallet;
7. Configure Truffle to connect to RSK network;
8. Get R-BTC;
9. Deploy a smart contract on RSK network using Truffle;
10. Interact with the smart contract at React app.

If you were redirected from the [Truffle-rsk-react-box](https://github.com/rsksmart/rsk-react-box) page 
and successfully executed all the instructions, you can go ahead and interact with the published smart contract:
- [In the Truffle development console](#interact-with-a-smart-contract-in-development-console).
- [On RSK network](#using-truffle-console-to-connect-to-the-rsk-network).

On the other hand, if you would like to review the steps with more explanatory details and images, you would find this tutorial helpful.

# Setup prerequisites
* POSIX compliant shell
* Curl
* Node.js and NPM (Node Package Manager)
* Code editor: Visual Studio Code (VSCode) or any other editor of your choice
* Truffle

## TO CHOOSE
The [Truffle boxes prerequisites](/truffle-boxes-prerequisites) page covers all the steps with more details, explanations, and images.

OR

The instalation of all of them are explained in detail in the tutorial link below: 
* [Truffle boxes prerequisites](/truffle-boxes-prerequisites)

# Install RSK Truffle React box

The `truffle unbox` command sets up a project based on a known template. 
In this tutorial, we will be using the "RSK react box" Truffle box, 
which includes RSK network configurations, 
the SimpleStorage contract as an example to deploy and a frontend built using react app. 

## Create a new folder 
For example, create the folder `rsk-react`.
Navigate to the folder in the terminal.

```shell
mkdir rsk-react
cd rsk-react
```

```windows-command-prompt
C:\>cd C:\RSK

C:\RSK>mkdir rsk-react

C:\RSK>cd rsk-react

C:\RSK\rsk-react>
```

## Run the unbox command

The truffle unbox command will install all necessary dependencies in the project.

```shell
truffle unbox rsksmart/rsk-react-box
```

```windows-command-prompt
C:\RSK\rsk-react>truffle unbox rsksmart/rsk-react-box

Starting unbox...
=================

√ Preparing to download box
√ Downloading
√ cleaning up temporary files
√ Setting up box

Unbox successful, sweet!

Commands:

  Compile:              truffle compile
  Migrate:              truffle migrate
  Test contracts:       truffle test
  Test dapp:            cd client && npm test
  Run dev server:       cd client && npm run start
  Build for production: cd client && npm run build

C:\RSK\rsk-react>
```

# SimpleStorage.sol

Take a look at the smart contract `SimpleStorage.sol`. You can check it out in folder `contracts`.

```javascript
pragma solidity >=0.4.0 <0.7.0;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

This smart contract has:

* A variable `storedData` to store a number
* A function `get()` to return the number stored at variable `storedData`
* A function `set()` to change the number stored at variable `storedData`

# Truffle development console

Truffle has an interactive console that also spawns a development blockchain. 
This is very useful for compiling, deploying and testing locally.

Run the development console by typing the following command below into the terminal:

```shell
truffle develop
```

```windows-command-prompt
C:\RSK\rsk-react>truffle develop
Truffle Develop started at http://127.0.0.1:8545/

Accounts:
(0) 0x1056f747cf4bc7710e178b2aeed4eb8c8506c728
(1) 0x45a71c00382c2898b5d6fae69a6f7bfe6edab80c
(2) 0x1596384706dc9ac4cca7f50279a4abe591d6c3fe
(3) 0x9576d0a496b645baa64f22aceb2328e7468d4113
(4) 0xd431572eef7d77584d944c1809398a155e89f830
(5) 0x92c111839718fe0800fadccc67068b40b8524a0f
(6) 0x6da22b5a027146619bfe6704957f7f36ff029c48
(7) 0x2c3a82d8c3993f8c80dcaf91025437bd057df867
(8) 0xc43ae7a44f7deb759177b7093f06512a0a9ff5d7
(9) 0xe61bf00cd7dce248449cfe58f23a4ef7d542bc0b

Private Keys:
(0) f32f32839fe27ad906b63eafb326f26fed95c231e3c5e33c7cdd08f62db63167
(1) ebef990088f27f6ef13b5e52a77d5dcc5a76862a701908c586d01b6fe93562b3
(2) 598ccae5e4436fedeb0e798c0d254789c55a63401ebfc3ae8ddde29634ddfcde
(3) 09934b80f391e0024b8cb00cd73790fdf64c4d0509e144766414fee317cd3f4e
(4) ac745b84b6574b5738d364b43e0d471c9d5107504acc709c90f6f091b78c751b
(5) 449654cde095f2349113ef12a93e139b4302bc95adb3619d08adf53dde9b8847
(6) c217f12a89c352fc70b5f1bd5742314b4fb1bb1e35cb779fdb3c2390106355db
(7) 1d4c74dfa4e99e161130c18cc63938bb120a128cefbf1b9188efc678bf5722cb
(8) 0f44e0becf2e090db498a1b747d2a758fcc81fb0241f350d61117a9c6b1fa82e
(9) 85218c5eec657470dafeb09e6f7101f91d21bfe822fbeeecfc9275f798662a63

Mnemonic: virtual valve razor retreat either turn possible student grief engage attract fiber

⚠️  Important ⚠️  : This mnemonic was created for you by Truffle. It is not secure.
Ensure you do not use it on production blockchains, or else you risk losing funds.

truffle(develop)>  
```

> Inside the development console we don't preface commands with `truffle`.

# Compile a smart contract

In the Truffle console, run this command:

```javascript
compile
```

```windows-command-prompt
truffle(develop)> compile

Compiling your contracts...
===========================
> Compiling .\contracts\Migrations.sol
> Compiling .\contracts\SimpleStorage.sol
> Artifacts written to C:\RSK\rsk-react\client\src\contracts
> Compiled successfully using:
   - solc: 0.5.16+commit.9c3226ce.Emscripten.clang

truffle(develop)>
```

# Deploy a smart contract

To deploy a smart contract using Truffle, we need a new migrations file where Truffle will find it. 
This file contains instructions to deploy the smart contract. 

The `migrations` folder has JavaScript files that help you deploy contracts to the network. 
These files are responsible for staging your deployment tasks, and they're written under the assumption that your deployment needs will change over time. 
A history of previously run migrations is recorded on-chain through a special Migrations contract. 
(source: [truffle: running-migrations](https://www.trufflesuite.com/docs/truffle/getting-started/running-migrations))

Take a look in the file `2_deploy_contracts.js` located in the migrations folder. 

## Migrate

In the Truffle console, run this command:

```javascript
migrate
```

```windows-command-prompt
truffle(develop)> migrate

Compiling your contracts...
===========================
> Compiling .\contracts\Migrations.sol
> Compiling .\contracts\SimpleStorage.sol
> Artifacts written to C:\RSK\rsk-react\client\src\contracts
> Compiled successfully using:
   - solc: 0.5.16+commit.9c3226ce.Emscripten.clang

Starting migrations...
======================
> Network name:    'develop'
> Network id:      5777
> Block gas limit: 6721975 (0x6691b7)

1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0xb0c8d61c99d1bd9726ed2157668799729247673714dfa4e6b72b70cfd50972dd
   > Blocks: 0            Seconds: 0
   > contract address:    0xf5c8B230b5281A8813b5153B4bCd815626d098cb
   > block number:        1
   > block timestamp:     1591913834
   > account:             0x1056F747cf4bC7710E178B2aeED4Eb8c8506c728
   > balance:             99.9967165
   > gas used:            164175 (0x2814f)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.0032835 ETH
   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:           0.0032835 ETH

2_deploy_contracts.js
=====================

   Deploying 'SimpleStorage'
   -------------------------
   > transaction hash:    0xd6dc9a9a64e2cfce4f566cccffb650ade4f19b06ca258cc734ec52e25e0ecb2d
   > Blocks: 0            Seconds: 0
   > contract address:    0x73f2aa5D251DbdEd6C950257124eA93bb00c0Ec0
   > block number:        3
   > block timestamp:     1591913834
   > account:             0x1056F747cf4bC7710E178B2aeED4Eb8c8506c728
   > balance:             99.9939459
   > gas used:            96189 (0x177bd)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.00192378 ETH
   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00192378 ETH

Summary
=======
> Total deployments:   2
> Final cost:          0.00520728 ETH

truffle(develop)>
```

# Test the smart contract

Truffle has an automated testing framework to facilitate the testing of contracts.
All test files should be located in the `test` directory.
To learn more, go to the Truffle documentation, in the section [testing your contracts](https://www.trufflesuite.com/docs/truffle/testing/testing-your-contracts).

Our box also comes with the file `TestSimpleStorage.js` for testing the smart contract. 
You can check it out in the `test` folder.

6. Truffle can run tests written in Solidity or JavaScript against your smart contracts. Note the command varies slightly if you're in or outside of the development console.

    ```javascript
    // inside the development console.
    test

    // outside the development console..
    truffle test
    ```

```javascript
test
```

# XXX IMAGEM OU windows-command-prompt
![test](/assets/img/tutorials/rsk-starter-box/image-01.png)

```windows-command-prompt
truffle(develop)> test
Using network 'develop'.

Compiling your contracts...
===========================
> Compiling .\contracts\Migrations.sol
> Compiling .\contracts\SimpleStorage.sol
> Artifacts written to C:\Users\Solange\AppData\Local\Temp\test-202055-3640-nxpnxb.3exj
> Compiled successfully using:
   - solc: 0.5.16+commit.9c3226ce.Emscripten.clang

  Contract: SimpleStorage
    √ should store a value (131ms)

  1 passing (164ms)

truffle(develop)>  
```

# Test the React app

[Jest](https://jestjs.io/) is a JavaScript testing framework and it can be used to test React components. 

Take a look in the file `App.test.js` located in the `client\src\` folder. 

Go to `client` folder to run it.

```shell
cd client
npm test
```

> Compile your contracts before running Jest, or you may receive some `file not found` errors.

```windows-command-prompt
C:\RSK\rsk-react>cd client
C:\RSK\rsk-react\client>npm test

> client@0.1.0 test C:\RSK\rsk-react\client
> react-scripts test
 PASS  src/App.test.js
  √ renders without crashing (13ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        2.761s, estimated 3s
Ran all test suites.

Watch Usage
 › Press f to run only failed tests.
 › Press o to only run tests related to changed files.
 › Press q to quit watch mode.
 › Press p to filter by a filename regex pattern.
 › Press t to filter by a test name regex pattern.
 › Press Enter to trigger a test run.

C:\RSK\rsk-react\client>
```

# Run the developer server

Open a second terminal and go to the `client` folder, inside the folder’s project, to run the React app.

```javascript
// in another terminal (i.e. not in the truffle develop prompt)
cd client
npm run start
```

It will automatically open the default browser at [http://localhost:3000/](http://localhost:3000/)

If it does not open, you can enter the local url manually in the browser.

![2 terminals](/assets/img/tutorials/rsk-react-box/image-01.png)

**Important:**

- Do not close the first terminal, which has the truffle develop prompt, because it is running the development blockchain. 
- If closed, the dApp will not find the deployed smart contract, you can see a message like `Unhandled Rejection (Error): This contract object doesn't have address set yet, please set an address first`.
- If you change something in the smart contract, you need to manually recompile and migrate it.


## RSK

### Setup an account & get R-BTC

- Get an address using [these instructions](https://developers.rsk.co/rsk/architecture/account-based/ "Account Based RSK Addresses - RSK Developers Portal").
- For the RSK Testnet, get tR-BTC from [our faucet](https://faucet.testnet.rsk.co/).
- For the RSK Mainnet, get R-BTC from [an exchange](https://developers.rsk.co/rsk/rbtc/).

### Setup the gas price

**Gas** is the internal pricing for running a transaction or contract. When you send tokens, interact with a contract, send RBTC, or do anything else on the blockchain, you must pay for that computation. That payment is calculated as gas. In RSK, this is paid in **R-BTC**.
The **minimumGasPrice** is written in the block header by miners and establishes the minimum gas price that a transaction should have in order to be included in that block.

To get the **minimumGasPrice** do the following steps:
1. Run this query using cURL:

    **Mainnet**

    ```shell
    curl https://public-node.rsk.co/ \
        -X POST -H "Content-Type: application/json" \
        --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false],"id":1}'
    ```

    **Testnet**

    ```shell
    curl https://public-node.testnet.rsk.co/ \
        -X POST -H "Content-Type: application/json" \
        --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false],"id":1}'
    ```

2. Find in the result the field **_minimumGasPrice_**

For more information about the **Gas** and **minimumGasPrice** please go [here](https://developers.rsk.co/rsk/rbtc/gas/ "Gas - RSK Developers Portal").

### Connect to RSK

1. Copy your mnemonic to `truffle-config.js`

    ```javascript
    // truffle-config.json

    const HDWalletProvider = require('@truffle/hdwallet-provider');

    //Put your mnemonic here, be careful not to deploy your mnemonic into production!
    // NB: you can find the mnemonic in the truffle develop prompt
    const mnemonic = 'A_MNEMONIC';
    ```
    Please be aware that we are using `HDWalletProvider` with RSK Networks derivations path:
    - RSK Mainnet dpath: `m/44’/137’/0’/0`
    - RSK Testnet dpath: `m/44’/37310’/0’/0`

    For more information check [RSKIP57](https://github.com/rsksmart/RSKIPs/blob/master/IPs/RSKIP57.md).

2. Check the gas price of the network, and update `truffle-config.js` if necessary.

3. Run the development console for any RSK network.

    ```shell
    # Console for Mainnet
    truffle console --network mainnet

    # Console for Testnet
    truffle console --network testnet
    ```

4. Compile and migrate the smart contracts. Note that inside the development console, we don't preface commands with truffle.

    ```shell
    compile
    migrate
    ```

**Then continue from step 5 of [installation steps](#installation)**



2. To build the application for production, use the build script. A production build will be in the `client/build` folder.
    ```javascript
    // ensure you are inside the client directory when running this
    npm run build
    ```


  Run dev server:       cd client && npm run start
  Build for production: cd client && npm run build
