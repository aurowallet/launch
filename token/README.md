# Submit Your Token Information to Auro Wallet

**1. Add token information by updating the `token.json` file (in the corresponding network). Do not change the order.**

- `mina_mainnet` refers to Mainnet token information.
- `mina_testnet` refers to Devnet/testnet token information.
- You can add the target `networkID` folder as needed.

Example format for the token:

```json
{
  "id": "xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1",
  "address": "B62qmMv99rMLCjnApLERcvof6fP4YD4wqeCXUrFuthHfTNoHbYgmy1i",
  "name": "TEST",
  "symbol": "7UjV6",
  "decimal": "6",
  "description": "Auro test token in Mainnet",
  "website": "https://www.aurowallet.com/"
}
```

**2. Create a folder with the token ID and add your token icon to `{networkID}/assets/{tokenID}/icon.png`.**

- Icon resolution must be 144x144px.
- The icon file name must be `icon.png`.

**3. Send token for testing**

You can use the Mainnet or testnet for this. The purpose is to test whether the token can be send normally before the merge.
Send tokens to the following address for testing:
**B62qpjxUpgdjzwQfd8q2gzxi99wN7SCgmofpvw27MBkfNHfHoY2VH32**

**4. Provide the token contract source code (Optional)**

We currently use the [fungible token contract](https://github.com/MinaFoundation/mina-fungible-token/releases/tag/v1.0.0). If you modify the contract code, it may cause a mismatch between the token contract and the source code. To prevent this, it is recommended to submit the token contract source code in the PR, so it can be integrated into the build service.

- Example location: `token/{networkID}/assets/xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1/source`

**5. Verify Token Ownership**

Add the signature of the `token.json` file submitted or updated in step 1 to the PR comment. This should be signed using the token account.

- Use the `Mina Sign` box in [test-zkApp](https://test-zkapp.aurowallet.com/).
  - In the `Mina Sign` module, fill in `JSON.stringify(submitContent)`, sign with the token account, and submit the signed result as a comment.
- Alternatively, use `client.signMessage` from [mina-signer](https://www.npmjs.com/package/mina-signer) with the following code:

```js
const submitContent = {
  id: "xLpobAxWSYZeyKuiEb4kzHHYQKn6X1vKmFR4Dmz9TCADLrYTD1",
  address: "B62qmMv99rMLCjnApLERcvof6fP4YD4wqeCXUrFuthHfTNoHbYgmy1i",
  name: "TEST",
  symbol: "7UjV6",
  decimal: "6",
  description: "Auro test token in Mainnet",
};

const unsignedMessage = JSON.stringify(submitContent);
const client = new Client({ network: "mainnet" });
const signedMessage = client.signMessage(unsignedMessage, tokenPrivateKey);

// After signed, submit the result in the comment
// Example: {"field":"10082789485841188200651752083435401189651661935760768844006925598425995295018","scalar":"13559698666955008071097956591497128241909562564253145138590504826423557135826"}
```

**6. Create a Pull Request (PR)**

Once all steps are completed, create a PR for review.
