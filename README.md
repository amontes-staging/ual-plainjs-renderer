# UAL Renderer for PlainJS

This library providers a Plain JS renderer around the [Universal Authenticator Library](https://github.com/EOSIO/universal-authenticator-library/).

It uses nothing but standard Javascript and should be supported across desktop and mobile.

![EOSIO Labs](https://img.shields.io/badge/EOSIO-Labs-5cb3ff.svg)

# About EOSIO Labs

EOSIO Labs repositories are experimental.  Developers in the community are encouraged to use EOSIO Labs repositories as the basis for code and concepts to incorporate into their applications. Community members are also welcome to contribute and further develop these repositories. Since these repositories are not supported by Block.one, we may not provide responses to issue reports, pull requests, updates to functionality, or other requests from the community, and we encourage the community to take responsibility for these.

## Getting Started
#### With ``yarn``
```bash
yarn add ual-plainjs-renderer
```
Then, install the authenticators that you wish to use...
```bash
yarn add ual-scatter ual-lynx
```
#### With ``npm``
```bash
npm i ual-plainjs-renderer
```
Then, install the authenticators that you wish to use...
```bash
npm i ual-scatter ual-lynx
```


## Basic Usage
The below code will render a button to the DOM that will launch the Universal Authenticator Library modal.
```javascript
import { UALJs } from 'ual-plainjs-renderer'
import { Scatter } from 'ual-scatter'
import { Lynx } from 'ual-lynx'

const myCallback = arrayOfUsers => {
  // Execute on successful user authentication
}

const myChain = {
  chainId: MY_CHAIN_ID,
  rpcEndpoints: [{
    protocol: MY_CHAIN_PROTOCOL,
    host: MY_CHAIN_HOST,
    port: MY_CHAIN_PORT,
  }]
}

const myAppName = 'My UAL App'

const scatter = new Scatter([myChain], { appName: myAppName })
const lynx = new Lynx([myChain], { appName: myAppName })

const myAppRoot = {
  containerElement: document.getElementById('my-ual-app')
}

const ual = new UALJs(myCallback, [myChain], myAppName, [scatter, lynx], myAppRoot)

ual.init()
```

## Example
An example on how to use the library is provided in the [examples](https://github.com/EOSIO/universal-authenticator-library/tree/develop/examples) folder.

## Environment Set Up
**A one-time environment setup is required prior to development.**  The following commands provides a quick starting point.  Make sure you are in the ``examples/`` directory.
```bash
cd examples
cp default.env .env
```
Now that you have a ``.env`` file, you can set your chain particulars.  Note that this file will not be version-controlled, nor should it be.
The default settings for the file are...
```
CHAIN_ID=12345
RPC_PROTOCOL=https
RPC_HOST=api.example.net
RPC_PORT=443
```
These values are taken from the local chain created by following the [Developer Portal node set up instructions](https://developers.eos.io/eosio-home/docs/getting-the-software). _(Note: if this is your first time following the tutorial you will need to install the eosio binaries [here](https://developers.eos.io/eosio-home/docs/setting-up-your-environment))._  These can be edited according to the requirements of your project if you have a different chain set up.  They will be used as the chain data in the example app.
*See the [Basic Example App for UAL with PlainJS](https://github.com/EOSIO/ual-plainjs-renderer/tree/develop/examples) for more details.*

## Development
After you set up your environment you can begin development.  Make sure you are back in the ``/`` directory of the ``ual-plainjs-renderer`` package.
```bash
yarn
yarn link
yarn build -w
```

In a duplicate terminal tab, enter the following commands:
```bash
cd examples
yarn link ual-plainjs-renderer
yarn
yarn example
```

Open a browser at `localhost:3000` to see a running instance of the example.

*It is recommended to have at least two terminal tabs running so that `yarn build -w` and `yarn example` can run simultaneously creating an environment where changes are immediately reflected in the browser.*

## Contributing

[Contributing Guide](./CONTRIBUTING.md)

[Code of Conduct](./CONTRIBUTING.md#conduct)

## License

[MIT](./LICENSE)

## Important

See LICENSE for copyright and license terms.  Block.one makes its contribution on a voluntary basis as a member of the EOSIO community and is not responsible for ensuring the overall performance of the software or any related applications.  We make no representation, warranty, guarantee or undertaking in respect of the software or any related documentation, whether expressed or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall we be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or documentation or the use or other dealings in the software or documentation. Any test results or performance figures are indicative and will not reflect performance under all conditions.  Any reference to any third party or third-party product, service or other resource is not an endorsement or recommendation by Block.one.  We are not responsible, and disclaim any and all responsibility and liability, for your use of or reliance on any of these resources. Third-party resources may be updated, changed or terminated at any time, so the information here may be out of date or inaccurate.  Any person using or offering this software in connection with providing software, goods or services to third parties shall advise such third parties of these license terms, disclaimers and exclusions of liability.  Block.one, EOSIO, EOSIO Labs, EOS, the heptahedron and associated logos are trademarks of Block.one.

Wallets and related components are complex software that require the highest levels of security.  If incorrectly built or used, they may compromise users’ private keys and digital assets. Wallet applications and related components should undergo thorough security evaluations before being used.  Only experienced developers should work with this software.
