# pocket-node
A Pocket Network client for Pocket Nodes, which are the actors within the Pocket Network that execute the Relays.

## Node registration
To register your node in the Pocket Network you can go to [https://dashboard.pokt.network](https://dashboard.pokt.network) and register your node, there you will be assigned a Node Nonce which you will use for configuration in a later step.

## Installation
You can install using `npm`:

`npm install -g pocket-node`

## Node setup
The first thing you need to do is configure your Node, by using the following command:

`pocket-node setup`

For an example of how to configure your node in the Rinkeby Testnet, you can use the following configuration:

* `Ethereum Node` You can use a GETH instance you're running locally (http://localhost:8545).
* `Ethereum Network ID` For Rinkeby you must use **4**
* `EpochRegistryAPI address` The address of the contract which records the transactions your node will relay into the blockchain. For Rinkeby this address is: `0x4cdaf013049eebf5891b389b0fc638386253d9aa`
* `Ethereum account address` The Ethereum account you used to register your node in the previous step.
* `Node Nonce` The Nonce for your Node, you can get it from [https://dashboard.pokt.network](https://dashboard.pokt.network)

## Running the server
To start the server, just run:

`pocket-node start -p [port number]`

But before you can start relaying transactions, read below on how to install the different plugins which will allow your Node to connect to the different blockchains (ETH, BTC, LTC, etc.).

## What is a Pocket Node Plugin?
The Pocket Node Plugin System allows the Pocket Node app to support any decentralized network as a Relay Node in the Pocket Network.

Each plugin can be created independently and supported individually as a NPM package, and each node can pick and choose whichever plugins they wanna use to support on their network.

For example, if you wanted to add Ethereum support for your node, you can use our [Pocket Node Ethereum Plugin](https://github.com/pokt-network/pnp-eth)

## Installing a Pocket Node Plugin
To install a plugin from NPM just run the following command:

`pocket-node install <npm package name>`

As simple as that and your Pocket Node will support the network described by this plugin.

***Note***: Please note that if you install multiple plugins for the same network, only the latest one you installed will be used, the older ones will be uninstalled.

## Listing your Pocket Node Plugins
To see which plugins you have installed just run the following command:

`pocket-node list`

## Configuring your Pocket Node Plugins
Each Plugin requires a configuration file which is a JSON object with all the pre-determined configurations.

`pocket-node configure <network token ID (ETH, BTC, etc.)> /path/to/configuration.json`

## Removing a Pocket Node Plugin
To remove a specific plugin just run the following command:

`pocket-node remove <network token ID (ETH, BTC, etc.)>`

***Note***: In case you have multiple plugins with the same name, all will be removed.
