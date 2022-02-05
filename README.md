<h1 align="center">
  <img align="center" src="https://raw.githubusercontent.com/tron-us/tronweb/master/assets/TronWeb-logo.png" width="400"/>
</h1>


## What is TronWeb React Native?

__[Tron Web - Developer Document](https://developers.tron.network/docs/tron-web-intro)__

TronWeb aims to deliver a unified, seamless development experience influenced by Ethereum's [Web3](https://github.com/ethereum/web3.js/) implementation. We have taken the core ideas and expanded upon it to unlock the functionality of TRON's unique feature set along with offering new tools for integrating DApps in the browser, Node.js and IoT devices.



TronWeb is also compatible with frontend frameworks such as:
- React Native

You can also ship TronWeb in a Chrome extension.

## Installation

### Node.js
```bash
npm install tronweb-rn
```
or
```bash
yarn add tronweb-rn
```

## Testnet

Shasta is the official Tron testnet. To use it use the following endpoint:
```
https://api.shasta.trongrid.io
```
Get some Shasta TRX at https://www.trongrid.io/shasta and play with it.
Anything you do should be explorable on https://shasta.tronscan.org

## Your local private network for heavy testing

You can set up your own private network, running Tron Quickstart. To do it you must [install Docker](https://docs.docker.com/install/) and, when ready, run a command like

```bash
docker run -it --rm \
  -p 9090:9090 \
  -e "defaultBalance=100000" \
  -e "showQueryString=true" \
  -e "showBody=true" \
  -e "formatJson=true" \
  --name tron \
  trontools/quickstart
```

[More details about Tron Quickstart on GitHub](https://github.com/tron-us/docker-tron-quickstart)

## Creating an Instance

First off, in your javascript file, define TronWeb:

```js
const TronWeb = require('tronweb-rn')
```

When you instantiate TronWeb you can define

* fullNode
* solidityNode
* eventServer
* privateKey

you can also set a

* fullHost

which works as a jolly. If you do so, though, the more precise specification has priority.
Supposing you are using a server which provides everything, like TronGrid, you can instantiate TronWeb as:

```js
const tronWeb = new TronWeb({
    fullHost: 'https://api.trongrid.io',
    headers: { "TRON-PRO-API-KEY": 'your api key' },
    privateKey: 'your private key'
})
```

For retro-compatibility, though, you can continue to use the old approach, where any parameter is passed separately:
```js
const tronWeb = new TronWeb(fullNode, solidityNode, eventServer, privateKey)
tronWeb.setHeader({ "TRON-PRO-API-KEY": 'your api key' });
```

If you are, for example, using a server as full and solidity node, and another server for the events, you can set it as:

```js
const tronWeb = new TronWeb({
    fullHost: 'https://api.trongrid.io',
    eventServer: 'https://api.someotherevent.io',
    privateKey: 'your private key'
  }
)
```

If you are using different servers for anything, you can do
```js
const tronWeb = new TronWeb({
    fullNode: 'https://some-node.tld',
    solidityNode: 'https://some-other-node.tld',
    eventServer: 'https://some-event-server.tld',
    privateKey: 'your private key'
  }
)
```

## A full example

The better way to understand how to work with TronWeb is go to the demo directory in this repository.

If you'd like to connect with tronlink app and chrome extention and develop a dapp on tron, you could run the demo in path demo/tron-dapp-react-demo.

If you'd like to develop only with tronweb dependency, you could run the demo in path demo/tronweb-demo.

## Contributions

In order to contribute you can

* fork this repo and clone it locally
* install the dependencies — `npm i`
* do your changes to the code
* build the TronWeb dist files — `npm run build`
* run a local private network using Tron Quickstart
* run the tests — `npm test:node`
* push your changes and open a pull request

## Licence

TronWeb is distributed under a MIT licence.

-----

For more historic data, check the original repo at
[https://github.com/tronprotocol/tron-web](https://github.com/tronprotocol/tron-web)

# Warning
I don't guarantee that this package works properly, you may face issues.