# Submit your token info to Auro Wallet

**1. Add token info by update `token.json` file (in the corresponding network). Don't change the order.**

- `mina_mainnet` is mainnet token info
- `mina_testnet` is testnet token info
- `Add target networkID folder is ok`.

```
    {
        "id": "xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1",
        "owner": "B62qmMv99rMLCjnApLERcvof6fP4YD4wqeCXUrFuthHfTNoHbYgmy1i",
        "name": "TEST",
        "symbol": "7UjV6",
        "decimal": "6",
        "sourceUrl": "https://github.com/MinaFoundation/mina-fungible-token/blob/main/FungibleToken.ts",
        "description": "Auro test token in mainnet",
        "weisite":"https://www.aurowallet.com/"
    }

```

**2. Make a folder with tokenID, add your token icon to "{networkID}/assets/{tokenID}/icon.png"**

- Icon resolution should be 128\*128px
- Icon name should be `icon.png`

**3. Provide less test token to this address B62qpjxUpgdjzwQfd8q2gzxi99wN7SCgmofpvw27MBkfNHfHoY2VH32**

- Both mainnet and testnet are OK, as long as the token contract is the same. This is mainly to test whether it can be send normally before merging.
  source code folder is `"{networkID}/assets/{tokenID}/source"`

- demo path in `token/mina_mainnet/assets/xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1/source`

**4. Provide token contract source code (Optional)**
Currently we are using the [fungible token contract](https://github.com/MinaFoundation/mina-fungible-token/releases/tag/v1.0.0). If you change the contract code, there will be a mismatch between the token contract and the source code. In this case, it is recommended to submit the token contract source code in the PR so that it can be written into the build service.

**5. Verify Token Ownership**

- Add the signature of the token.json submitted or updated in step 1 to the comment. (use token account)

- use `Mina Sign` box in [test-zkApp](https://test-zkapp.aurowallet.com/)
  - In the module of `Mina Sign`, fill in JSON.stringify(submitContent). Sign with the token account and submit signed result to comment
- use `client.signMessage` of [mina-signer](https://www.npmjs.com/package/mina-signer)
  This is the usage scheme using mina-signer

```js
const submitContent = {
  id: "xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1",
  owner: "B62qmMv99rMLCjnApLERcvof6fP4YD4wqeCXUrFuthHfTNoHbYgmy1i",
  name: "TEST",
  symbol: "7UjV6",
  decimal: "6",
  description: "Auro test token in mainnet",
};
const unSignMessage = JSON.stringify(submitContent);
const client = new Client({ network: "mainnet" });
const signedMessage = client.signMessage(unSignMessage, tokenPrivateKey);

// after signed, submit result to comment
// {"field":"10082789485841188200651752083435401189651661935760768844006925598425995295018","scalar":"13559698666955008071097956591497128241909562564253145138590504826423557135826"}
```

**6. Make a PR**
