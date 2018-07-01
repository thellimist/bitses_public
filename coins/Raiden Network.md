# Raiden Network

The Raiden Network is an off-chain transfer network for Ethereum ERC20 tokens. It provides a fast, scalable, and cheap alternative to on-chain token transfers. At the same time, the Raiden Network transfers provide users with guarantees of finality, security, and decentralization similar to those known from blockchains.

tl;dr Raiden Network is Lightning Network on ETH. The difference is Raiden network allows ERC20 tokens + ETH to be transferred. 

**Key features**  
- Scalable: Scales linearly with the number of participants  
- Fast: Transfers are confirmed and final within a fraction of a second  
- Confidential: Single transfers don’t show up in the global shared ledger  
- Interoperable: Works with any token that follows Ethereum’s standardized token API  
- Low fees: Transactions can be 7 orders of magnitude lower than on the blockchain  
- Micro-payments: Low transaction fees allow tiny values to be efficiently transferred.  

**Limitations**
- Not suitable for large value transfers due to extra cost of channel lifetime management  

## Fees
There are two kinds of fees in the Raiden Network.

- Protocol level fees are necessary to keep the payment channel network balanced. Nodes will use fees to prevent their channels from being depleted over time. These fees will be comparatively small and be denominated in the token that is transferred in the channel.
- Peripheral fees will be payable to services in the network that, for example, assist with finding a path with sufficient capacity or services that provide channel monitoring services for offline users. Users running these services themselves will not need to pay these fees but can earn them instead.

Over 95% of all nodes are expected to be light-clients willing to pay small fees for the convenience of not having to run a full stack of services. As most users will not run a full node, they will need to pay RDN to participate in the Raiden
network. 

## Issues
- Large transactions are not possible
- Natural wealth distribution will cause a centralized network. 
- Nodes needs to be online. If they are offline during transaction, their fund can be stolen without retrieving the product. DDoS'ing a node is also possible to make them offline. However uses shouldn't transfer large amounts thus the attack is kind of useless. It's more of a connectivity problem.
- Raiden Token value comes from only fees. The tokens will keep curculating. HODLing doesn't work in this case. I can't see a reason for the price to jump significantly.
- The project has been delayed for a while (original MVP launch date was March 2017).

## Others
- RaidEx: Dex on Raiden. Will be useful.
- Trustlines Network: Useless project...
- HydraChain: Permissioned Distributed Ledger based on Ethereum.
