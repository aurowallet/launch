# Submit your BP node to Auro Wallet

1. Update list.json file add BP node info. Don't change the order, The order in which BP nodes are displayed in the wallet is independent of the order in list.json
 
```
{
	"id": "B62qq3TQ8AP7MFYPVtMx5tZGF3kWLJukfwG1A1RGvaBW1jfTPTkDBW6",
	"name": "Auro Wallet",
	"website": "https://www.aurowallet.com",
	"description": "A simple yet powerful Mina Protocol Wallet",
	"Fee": 5
}
```

`id` BP node address  
`name` BP node name  
`website` BP node website  
`description` BP node description  
`fee` BP node fee, 5 mean is 5%

2. Make a folder with BP address, add your logo to  "assets/{bp-node-address}/logo.png"
- Logo resolution should be 128*128
- Logo name should be `logo.png`

3. Make a PR
