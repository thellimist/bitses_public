# Stellar

Stellar and Ripple had the same consensus algorithm. Later on there was a fork because the algorithm had a flaw prefering speed over safety. The team added a centralized verifier to disallow isolated nodes however that was not scalable. Then they had arguments with Ripple team on how to distribute tokens and the algorithm and decided to re-do the algorithm from scratch the new algorithm is called SCP.

## Stellar Consensus Protocol (SCP)
![](https://www.stellar.org/wp-content/uploads/2015/04/properties-no-margin1.png)

Stellar has sets of nodes called quorums. Each node can select their own quorums which are called quorum slices. Quorums do Paxos like algorithm to agree on a consensus. There are 2 ways quorum slices can group
1) Isolated Quorums
2) Intersecting Quorums

![](https://cdn-images-1.medium.com/max/1600/0*msL7MVVEy4p2VzhP.)

If the quorums are isolated, the quorums might agree upon a value which might result in double spending. The way SCP handles this is called Federated Byzantium Agreement (FBA).

FBA gives tiers to certain nodes just like how the internet works today (tiered DNS servers). There are 3 tiers of nodes.  
Tier 3: 4 to 12 nodes which are highly reputable services like Stellar or Bank Of America   
Tier 2: N nodes which are like national ISPs (per country or geography)    
Tier 1: M nodes which can be anyone.    

![](https://cdn-images-1.medium.com/max/1600/1*ljU_3U-YV7sa_0-JbRYjTw.png)

The image shows the necessary votes a quorum would need from other tiers to get in consensus. Tier 3 quorums needs 3/4 votes from Tier 3s where as Tier 2 quorums need 2/4 votes from Tier 3 and rest from Tier 2. Tier 1 nodes require 2/4 votes from Tier 2 and rest from Tier 1. 

This federated system disallows any 2 quorum to be isolated and have double spent attacks. Stellar is open membership meaning everyone can open a node, set their own quorums and validate. In theory a malicious person can create isolated quorums but it won't be useful since it's not connected to the real ledger where everyone hangsout.

This system does not need PoS or PoW. It does basic validation resulting in 100k+ tps.

I'll be skipping how Ballot Protocol works which allows SCP to get out of states where a decision couldn't be made.

## Minting
Unlike other Blockchains with PoS/PoW, SCP can't mint coins meaning Stellar Foundation needs to distribute the coins initially. 

## Inflation
There is 1% inflation yearly. This is a incentive for people to use Stellar as a payment method rather than holding. More info on https://lumenaut.net/

## Anchor Nodes 
Stellar can transfer any currency or asset by providing an IOU via a trusted party worldwide. Watch this video: https://www.youtube.com/watch?v=EA53r43vGCA

### ICOs
Stellar can do ICO's the same way issuing an asset without the need of smartcontracts https://www.stellar.org/blog/using-stellar-for-ico/

## Smart (Simple) Contracts
Stellar only has simple smart contracts with “built-in token capabilities”. Stellar strives to ensure safety and stability of their system and has hence opted to limit their smart contract functionality.

tl;dr Stellar has built-in functinalities which can act like a contract allowing people to do future sells or sell bonds, do ICOs etc.

## Resources 
Stellar has great resources everywhere around it's webiste. This might be a good start.
https://www.stellar.org/blog/stellar-consensus-protocol-proof-code/
