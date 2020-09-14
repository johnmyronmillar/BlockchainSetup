# out-of-the-box-blockchain
Instructions to setup new blockchain

## Create Folder with Blockchain-Tools

> D:\Blockchain-Tools

## Run puppeth on GitBash

Open GitBash

set location to folder with Blockchain-Tools
$ cd D:\Blockchain-Tools

Run puppeth
$ ./puppeth

Set network name
> znet

## Configure zneth

Select new genesis
2. Configure new gensis
> 2
> Enter

Select create from scratch
1. Create new genesis from scratch
> 1
> Enter

Select proof-of-authority
2. Clique - proof-of-authority
> 2
> Enter

Leave time for blocks at 15
>
> Enter

## Set accounts allowed to seal

### Addresses
> 0x60DfEeC1f6a281c58C298649c4BAEc2Aa00aad2E
> Enter
> 0x22Dc13a88804F0ae840eCD123966E27afbb8850c
> Enter

Should the precompile-addresses be pre-funded
> yes
> Enter

Sprcify your chain/network ID if you want...
>
> Enter

## Manage esisting genesis options
2. Manage existing genesis
> 2
> Enter

### Setup Images

![GitBash_Blockchain1.png](images/GitBash_Blockchain1.png)

![GitBash_Blockchain2.png](images/GitBash_Blockchain2.png)



Crib5:
0x75ed7F5045A47b68D25474398f66BB7c18812578

Crib1:
Address = 0xCe969D0cfE8166fe8E0CAA5dDc1Dd337Bec63aF1
Private Key = 0xe862100c9458933a565c7763bbae2daef84061fa36fc9eb153777aa70b651127

Node1:
./geth account new --datadir node1

Result:
Public address of the key:   0x5a1655007E7B8AB4954A17533d5f80082B1a6fa5
Path of the secret key file: node1\keystore\UTC--2020-09-11T04-07-59.162324700Z--5a1655007e7b8ab4954a17533d5f80082b1a6fa5

Initialize (pupnet):
./geth init pupnet.json --datadir node1


Node2:
./geth account new --datadir node2

Result:
Public address of the key:   0xfacaCcD00dD03955845a01bB9868bffb7aa31531
Path of the secret key file: node2\keystore\UTC--2020-09-11T04-13-06.290598700Z--facaccd00dd03955845a01bb9868bffb7aa31531

Initialize (pupnet):
./geth init pupnet.json --datadir node2

Start Node 1:
./geth --datadir node1 --mine --minerthreads 1

result:
enode://d9cc1e93be93ff5f4ec52e81cedfee680aad13d5e3acf3a731bf66538b635812147ba3b965b08e798a43520f7f0164a2887a280b1aaeabd14b8901e239a1bb98@127.0.0.1:30303

Start Node 2:
./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://d9cc1e93be93ff5f4ec52e81cedfee680aad13d5e3acf3a731bf66538b635812147ba3b965b08e798a43520f7f0164a2887a280b1aaeabd14b8901e239a1bb98@127.0.0.1:30303" --ipcdisable

enode:
d9cc1e93be93ff5f4ec52e81cedfee680aad13d5e3acf3a731bf66538b635812147ba3b965b08e798a43520f7f0164a2887a280b1aaeabd14b8901e239a1bb98@127.0.0.1:30303

Hints:
If you ever encounter strange errors, or need to start over without destroying the accounts, run the following command to clear the chain data (this will reset the enode addresses as well):

rm -Rf node1/geth node2/geth

The --rpc flag enables us to talk to our second node, which will allow us to use MyCrypto or Metamask to transact on our chain.

Since the first node's sync port already took up 30303, we need to change this one to 30304 using --port.

The --bootnodes flag allows you to pass the network info needed to find other nodes in the blockchain. This will allow us to connect both of our nodes.

In Microsoft Windows, we need to add the flag --ipcdisable due to the way Windows spawns new IPC/Unix sockets doesn't allow for having multiple sockets running from geth at once. Since we are only using RCP we can safely disable the IPC sockets.
