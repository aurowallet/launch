# Submit your token info to Auro Wallet

**1. Add token info by update `token.json` file (in the corresponding network). Don't change the order.**

- `mina_mainnet` is mainnet token info 
- `mina_testnet` is testnet token info 
- `Add target networkID folder is ok`.

```
    {
        "id": "xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1",
        "name": "TEST",
        "symbol": "7UjV6",
        "decimal": "6",
        "description":"Auro test token in mainnet"
    }

```

**2. Make a folder with tokenID, add your token icon to  "{networkID}/assets/{tokenID}/icon.png"**
- Icon resolution should be 128*128px
- Icon name should be `icon.png`

**3. Provide less test token to this address B62qpjxUpgdjzwQfd8q2gzxi99wN7SCgmofpvw27MBkfNHfHoY2VH32**
- Both mainnet and testnet are OK, as long as the token contract is the same. This is mainly to test whether it can be send normally before merging.
source code folder is `"{networkID}/assets/{tokenID}/source"`

- demo path in `token/mina_mainnet/assets/xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1/source`


**4. Provide token contract source code (Optional)**
Currently we are using the [standard token contract](https://github.com/MinaFoundation/mina-fungible-token/releases/tag/v1.0.0). If you change the contract code, there will be a mismatch between the token contract and the source code. In this case, it is recommended to submit the token contract source code in the PR so that it can be written into the build service.

**5. Make a PR**