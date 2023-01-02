# @finney/rpc

A dependency-free TypeScript client for Bitcoin Core's JSON-RPC.

* Targets 100% coverage of the JSON-RPC
* Exports types for each RPC response
* Dependency-free (aside from development dependencies)
* Targets the Bun runtime first

## Usage

Copy `.env.template` to `.env` and replace the values with those for your node. Otherwise, set them in the environment.

Then, import and initialize:

```typescript
import BitcoinRPC from '@finney/rpc';

const bitcoinRPC = new BitcoinRPC();
```

Every procedure is implemented as an `async` function on this imported class, and every function return value is expected to be `Promise<RPCResponse<T>>` and is strongly typed using this generic:

```typescript
const block = await bitcoinRPC.getblock('000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f');
console.log(block.result?.hash);
```

If the procedure failed, you can expect `error` to be present:

```typescript
const block = await bitcoinRPC.getblock('badhash');
console.error(block.result.error);
```

## Coverage
- [x] Blockchain RPCs
  - [x] getbestblockhash
  - [x] getblock
  - [x] getblockchaininfo
  - [x] getblockcount
  - [x] getblockfilter
  - [x] getblockfrompeer
  - [x] getblockhash
  - [x] getblockheader
  - [x] getblockstats
  - [x] getchaintips
  - [x] getchaintxstats
  - [x] getdeploymentinfo
  - [x] getdifficulty
  - [x] getmempoolancestors
  - [x] getmempooldescendants
  - [x] getmempoolentry
  - [x] getmempoolinfo
  - [x] getrawmempool
  - [x] gettxout
  - [x] gettxoutproof
  - [x] gettxoutsetinfo
  - [x] preciousblock
  - [x] pruneblockchain
  - [x] savemempool
  - [x] scantxoutset
  - [x] verifychain
  - [x] verifytxoutproof
- [x] Control RPCs
  - [x] getmemoryinfo
  - [x] getrpcinfo
  - [x] help
  - [x] logging
  - [x] stop
  - [x] uptime
- [x] Mining RPCs
  - [x] getblocktemplate
  - [x] getmininginfo
  - [x] getnetworkhashps
  - [x] prioritisetransaction
  - [x] submitblock
  - [x] submitheader
- [x] Network RPCs
  - [x] addnode
  - [x] clearbanned
  - [x] disconnectnode
  - [x] getaddednodeinfo
  - [x] getconnectioncount
  - [x] getnettotals
  - [x] getnetworkinfo
  - [x] getnodeaddresses
  - [x] getpeerinfo
  - [x] listbanned
  - [x] ping
  - [x] setban
  - [x] setnetworkactive
- [x] Rawtransactions RPCs
  - [x] analyzepsbt
  - [x] combinepsbt
  - [x] combinerawtransaction
  - [x] converttopsbt
  - [x] createpsbt
  - [x] createrawtransaction
  - [x] decodepsbt
  - [x] decoderawtransaction
  - [x] decodescript
  - [x] finalizepsbt
  - [x] fundrawtransaction
  - [x] getrawtransaction
  - [x] joinpsbts
  - [x] sendrawtransaction
  - [x] signrawtransactionwithkey
  - [x] testmempoolaccept
  - [x] utxoupdatepsbt
- [x] Signer RPCs
  - [x] enumeratesigners
- [x] Util RPCs
  - [x] createmultisig
  - [x] deriveaddresses
  - [x] estimatesmartfee
  - [x] getdescriptorinfo
  - [x] getindexinfo
  - [x] signmessagewithprivkey
  - [x] validateaddress
  - [x] verifymessage
- [x] Wallet RPCs
  - [x] abandontransaction
  - [x] abortrescan
  - [x] addmultisigaddress
  - [x] backupwallet
  - [x] bumpfee
  - [x] createwallet
  - [x] dumpprivkey
  - [x] dumpwallet
  - [x] encryptwallet
  - [x] getaddressesbylabel
  - [x] getaddressinfo
  - [x] getbalance
  - [x] getbalances
  - [x] getnewaddress
  - [x] getrawchangeaddress
  - [x] getreceivedbyaddress
  - [x] getreceivedbylabel
  - [x] gettransaction
  - [x] getunconfirmedbalance
  - [x] getwalletinfo
  - [x] importaddress
  - [x] importdescriptors
  - [x] importmulti
  - [x] importprivkey
  - [x] importprunedfunds
  - [x] importpubkey
  - [x] importwallet
  - [x] keypoolrefill
  - [x] listaddressgroupings
  - [x] listdescriptors
  - [x] listlabels
  - [x] listlockunspent
  - [x] listreceivedbyaddress
  - [x] listreceivedbylabel
  - [x] listsinceblock
  - [x] listtransactions
  - [x] listunspent
  - [x] listwalletdir
  - [x] listwallets
  - [x] loadwallet
  - [x] lockunspent
  - [x] migratewallet
  - [x] newkeypool
  - [x] psbtbumpfee
  - [x] removeprunedfunds
  - [x] rescanblockchain
  - [x] restorewallet
  - [x] send
  - [x] sendall
  - [x] sendmany
  - [x] sendtoaddress
  - [x] sethdseed
  - [x] setlabel
  - [x] settxfee
  - [x] setwalletflag
  - [x] signmessage
  - [x] signrawtransactionwithwallet
  - [x] simulaterawtransaction
  - [x] unloadwallet
  - [x] upgradewallet
  - [x] walletcreatefundedpsbt
  - [x] walletdisplayaddress
  - [x] walletlock
  - [x] walletpassphrase
  - [x] walletpassphrasechange
  - [x] walletprocesspsbt
- [x] ZMQ RPCs
  - [x] getzmqnotifications

## Todos
- [ ] Update to 0.24.1
- [ ] Hidden generating RPCs