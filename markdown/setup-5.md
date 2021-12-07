
# Deploying on the Public/Global Ropsten Network 

Now let's do the same with the online Ropsten Testnet because we actually want to have this app distributed! It is supposed to be a DApp after all! 

### Get Some Fake Ether on the Testnet 

The very first thing you need to do is get some ETH in your account. For this you need to use a `faucet`. These are available for free and can be found by searching for `"ropsten faucet"`. At the moment, the following faucets work:  

* https://faucet.ropsten.be/
* https://faucet.metamask.io/
* https://faucet.dimensions.network/

Request ETH on all the faucets. You'll need it for testing and it sometimes takes time to receive it. Make sure you give it an address that you created yourself. Hardhat accounts are publicly known and people will steal your (fake) ether from the testnet and you won't be able to test out your contracts. 

### Get Endpoints 

Next, let's create a project in Infura. This will give us an endpoint through which we can actually push our contract. Think of this as the equivalent of the `node` that we created locally. For the internet, you need some node to act on your behalf. We'll use infura but you can also use Alchemy. 

Go to `infura.io` and create a new Ethereum project. You need the `Project ID`. Also select Ropsten from the Endpoints dropdown and get the endpoint URL. Save both of these somewhere. 

Also in the security tab, enter your public key (not the private key!) for the account `recly-test0x` account. This is because we have some test ETH in this account and we'll need that to deploy our contracts. 

Stop the hardhat node and let's configure it to use the Ropsten Testnet. 

Edit the `hardhat.config.js` file and add the configs for Ropsten. 

```javascript 
networks: {                   // and this ...
  hardhat: {
    chainId: 1337,
  },
  ropsten: {
    url: "https://ropsten.infura.io/v3/e5143812e60d4048a480d4fde5??????",  // Ropsten endpoint 
    accounts: [
      "0x261e20914b939aec2aa0529c115c8970dfa949e021bb6b0f3bef40faad??????" // private key with ETH
    ]
  }
}
```

```bash 
npx hardhat run scripts/deploy.js --network ropsten 
```

This will use up your ETH, which you can verify through MetaMask. Go to dots menu for `recly-test0x` account and click on `View on Etherscan`. 

You can now go ahead and import the REC token which is now on the Ropsten Testnet but is an actual DApp! 

Congrats! 

## Deploying on Mainnet 

Deploying on mainnet is exactly the same as with Ropsten. You can get an endpoint for mainnet from Infura. The difference is only that you will need real ETH to deploy your DApp on mainnet and it would take gas to write transactions to the block. 

So, test well on the testnets and only move to mainnet when you are sure everything is fine. 

Good luck! 
