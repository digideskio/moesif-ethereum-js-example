
# Moesif For Dapp Example

Purpose of this repo is to illustrate an example how a DAPP can integrate Moesif
for API analytics.

### Background on Dapps

When you create your own Dapp, the key dependency is the `web3.js` official library from Ethereum org.
[Web3js](https://github.com/ethereum/web3.js/) allows your Dapp to interact with the ethereum network (and the smart contracts deployed on it) using JSON-RPC. In our example, we use Truffle framework, which is set of tools for streamline some of the process and generate boilerplate code.

## Background on Moesif

Moesif is the leading API analytics and monitoring platform, for Restful APIs, GraphQL, and now JSON-RPC/Ethereum.

For Dapps (distributed Apps) that are built on top of Ethereum, it is impossible to
monitor the servers, as there is no more servers.  To understand how the Dapp APIs
are used, where the errors are, it becomes even more difficult.

Moesif is the perfect solution for giving you insight for the Dapp that you could get in traditional server based applications.

## How we created this example

This repo is based on the [Truffle Framework](http://truffleframework.com/), and one of the standard starting kit [Truffle React Box](http://truffleframework.com/boxes/react). Although the Moesif integration itself do not
depend on react.

We followed these steps to create this example:

- `npm install -g truffle`
- `truffle unbox react`
- Created a basic Dapp, something more interactive than the one out of the box.
  - We added a form and a button to set the storage value using the minimalistic "storage" smart contract included in the depot.
  - This additional code is in `src/App.js`.
- Install Moesif using standard Browser integration.
  - leverages the [moesif-browser-js](https://www.moesif.com/docs/client-integration/browser-js/) library.
  - In `index.html` under `/public`, we added the following code snippet, between the `head` tags.

```
    <script src="//unpkg.com/moesif-browser-js@1.2.0/moesif.min.js"></script>
    <script type="text/javascript">
    var options = {
      applicationId: 'Your application id'
      // add other option here.
    };

    // for options see below.
    moesif.init(options);

    // this starts the capturing of the data.
    moesif.start();
    </script>
```

### To run this example

- Fork or download this repo.
- Get a [Moesif account by sign up](https://www.moesif.com), and obtain an Application Id.
- Edit the `index.html` file in `/public`, and replace `Your application id` with your actual application id.
- If you haven't already, install truffle by: `npm install -g truffle`
- install dependencies for this repo: `npm install`
- start the truffle development environment: `truffle develop`
- compile the smart contracts: type in `compile` in the truffle develop prompt.
- deploy the smart contracts: type in `migrate` in the truffle develop prompt
- Start the Dapp: in another terminal, run `npm run start`;

Now, you can type go to: http://localhost:3000/, and interact with the Dapp.
As you interact with the Dapp, all the JSON-RPC calls will be captured in your
Moesif account.


### Summary

Basically for any Dapp build on top of Ethereum and JSON-RPC using web3.js, it is very simple
to install Moesif API analytics. Basically the process is the same as for any normal browser based app.
Moesif automatically detects they are JSON-RPC calls and apply same level of intelligent monitoring and deep insights that we already do for other APIs such as REST or GraphQl.