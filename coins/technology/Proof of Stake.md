# Proof of Stake

**Problems of Proof of Work lacks**
- Wasted energy
- Vulnerable to ASICs and centralization
- Lacks 'finality'

**CAP theorem**: A distributed datastore can have 2 of the three guarantees. For cryptoassets, "in the cases that a network partition takes place, you have to choose either consistency or availability, you cannot have both". 

- Consistency: Every read receives the most recent write or an error
- Availability: Every request receives a (non-error) response – without guarantee that it contains the most recent write
- Partition tolerance: The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

There are two kinds of PoS:
1) **Chain based PoS**: the algorithm pseudo-randomly selects a validator during each time slot (eg. every period of 10 seconds might be a time slot), and assigns that validator the right to create a single block, and this block must point to some previous block (normally the block at the end of the previously longest chain), and so over time most blocks converge into a single constantly growing chain.
2) **BFT style PoS**: validators are randomly assigned the right to propose blocks, but agreeing on which block is canonical is done through a multi-round process where every validator sends a "vote" for some specific block during each round, and at the end of the process all (honest and online) validators permanently agree on whether or not any given block is part of the chain. Note that blocks may still be chained together; the key difference is that consensus on a block can come within one block, and does not depend on the length or size of the chain after it.

Proof of work algorithms and chain-based proof of stake algorithms choose availability over consistency, but BFT-style consensus algorithms lean more toward consistency.

**Terms**
**Persistence**: once a transaction goes more than 𝐤 blocks deep into the blockchain of one honest player, then it will be included in every honest player’s blockchain with overwhelming probability.

**Liveness**: all transactions originating from honest account holders will eventually end up at a depth more than 𝐤 blocks in an honest player’s blockchain, and hence the adversary cannot perform a selective denial of service attack against honest account holders.

**Grinding**: Attackers might be able to bias the block creator selection process in their favour by contriving the state of the blockchain. If they can, they could repeatedly re-elect themselves as block creators. If they dominate block creation they can censor transactions, violating liveness.

**Nothing-at-stake**: Since it costs you nothing to create a block you may as well create blocks wherever you can. If an attacker can wield this power effectively, they may be able violate persistence by creating blocks on a competing chain, or bribing/encouraging others to do so. If the chain becomes long enough it will overtake the main chain and so rewrite history.

**PoS Algorithms**
- Tendermint is a BFT-based PoS design
- Peer Coin - Chain-based PoS design
- NeuCoin - Chain-based PoS design
- Ouroboros - Chain-based PoS design
- Ethereum - Casper the Friendly Ghost is a chain-based PoS design 
- Ethereum - Casper the Friendly Finality Gadget is a hybrid of the two
- Tezos ???

## PeerCoin
```
Hash(prev_block, current_time, txout) <= d x number_coins x timeweight(txin)
```
Peercoin satisfies the above formula where d is a difficulty like PoW and timweight is a function where old coins have more weight of winning the new ones. This causes issues where someone can hold few coins for a year and have high weight. With these super coins you can do double spending and other stuff since you can probabilistically guruanntee the next block will be yours. Other issues might be bribing to buy high weight coins.

Coin minting where r = 1
```
reward = number_coins x (days_idle / 365) x r% 
```

This means if you generate a block for 365 days a year or one time a year, you'll get the same reward. This is to avoid rich getting richer however no incentive to generate blocks.

## NeuCoin
```
Hash(prev_block, current_time, txout) <= d x number_coins
```

- Eliminates timeweight
- Faster block generation
- Punishment for malicious forks

Coin minting where r starts from 100 and declines to 6
```
reward = number_coins x (days_idle / 365) x r% 
```

By making dynamic r%, Neucoin solves this problems by generating a rewards like logaritmic function where the reward declines throught the end of the year while generating blocks. This solves the problem of rich not getting richer and having incentive to generate blocks.

## Tendermint

- Tendermint is a BFT-based PoS design. 
- Tendermint requires 100% uptime from a supermajority of its validators because if ⅓ or more are offline or partitioned, the network may halt.
- Tendermint-based blockchain never forks (assuming less than 1/3 are Byzantine)

Tendermint prioritizes safety and finality over liveness. There’s a fairly high likelihood that in the real world, the system will actually halt, and the participants will have to organize outside of the protocol in some sort of software update to restart the system. Tendermint formed the basis of Casper research. 

### Attacks
- Long Range: Every block is finalized so this isn't possible
- Nothing at Stake: When a validator wants to withdraw, they have to wait 3 months. If any bad acting is observed, the validator will get slashed.

### Conclusion

- Provable liveness in partially synchronous network.
- Instant finality: 1–3 seconds depending on number of validators.
- Consistency > Availability.
- Consensus safety.

## Cardano

Cardona uses Chain based PoS. Cardano has two consensus algorithms

**Ouroboros**: Slot leaders are known publicly ahead of time and there is always one slot leader per slot.
**Ouroboros Praos**: Each stakeholder knows which slots they lead ahead of time. Others only find out once they publish a block. There can be multiple slot leaders for a slot or none at all.

Currently Ouroboros is live. Only a handful of authorised stakeholders are currently eligible slot leaders. All stake is essentially assigned to them. At some point in 2018 these training wheels come off, and stake delegation will stakeholders will be able to re-assign their stake. They'll upgrade Ouroboros to Ouroboros Praos sometime. 

### Ouroboros
Ouroboros uses publicly verifiable secret sharing (PVSS) with coin flipping. No one knows the results of the entropy coin flipping does before selection happens. The result of coin flipping results in a stashi address. The stake holder of that satashi address will compute the next n blocks. 


- There can't be forks in Ouroboros.
- Ouroboros will work if 50% + 1 of the network is honest.
- Ouroboros is totally immune to grinding because coin flipping entropy. 
- The number PVSS related messages is proportional to 𝓶² where 𝓶 is the size of the committee.
- Ouroboros uses a synchronous network model to prove its security, meaning that all parties’ messages won’t be delayed longer than a slot. 
- An attacker can identify which parities it would be best to corrupt or hack into ahead of time because the slot leader schedule for the current epoch is public. The model assumes that attackers can’t corrupt other parties instantaneously after seeing the satashi address which means it’s not secure against “fully-adaptive corruption”. 

### Ouroboros Proas

Praos uses a verifiable random function (VRF) as it’s core randomness generating scheme. A psedocode looks like the following for each node. Only a single slot is selected every epoch unlike Ouroboros. 

```
T = calculateMThreshold(myAmountOfStake)
foreach 1..nSlots -> i:
  y, proof = VRF(myPrivateKey, concat(epochNonce, i, nonce))
  if y < T:
    getReadyToGenerateBlockAt(i, y, proof)
```

- There is no reason to have a minimum stake limit to participate in the protocol. Delegation can just be optional for parties who don’t have enough stake to make staking profitable. Having no fixed minimum is a big improvement over Ouroboros.
- Grinding attacks are possible but limited. An Adversery can try all nounces for all forks to get an advantage (can only be used when there is a fork). Grinding attacks are limited by the adversary’s hashing power. They have to hash all possibilities where as an honest node only does lazy hash on single chain. According to the analysis of the paper this advantage doesn’t change the security properties of the protocol.
- When two or more parties are elected in the same slot they will create a fork even if they’re all honest. Most of the time they’ll be very short lived. For a grinding attacker, the more “honest forks” there are at the end of the nonce determining slots the better.
- The paper suggests that in case of a fork, honest parties should choose the chain they got first (see end of page 24). If this is the case when the protocol goes live, I can see it turning into a network relay race. People running staking nodes are going to create systems to propagate their blocks as fast as possible to all the other nodes so everyone chooses theirs first rather than the alternatives (if any).
- Praos’ security proof is done under a semi-synchronous model where an attacker can delay messages for longer than a slot. The intermittent empty slots (where no one is a slot leader) counteracts this ability as it gives parities who are being delayed by an attacker some time to catch up.
- Since slot leaders aren’t publicly known ahead of time, an attacker can’t see who was a slot leader until after they’ve published a block. An attacker can’t know who specifically to attack in order to control a certain slot ahead of time.
- Praos uses a “forward secure” digital signature scheme which means that block creators use a different private key each time they create a block (and delete the old one), while preserving their public key. So, even if an attacker was able to corrupt a party they can’t create blocks in their already published slots. This point and the one above mean that, unlike the original Ouroboros, Praos is secure against fully-adaptive corruption.
- Praos isn’t the only blockchain protocol using a VRF. Algorand, was published before Praos and uses a VRF in a similar way. There’s also Dfinity.
- Is Quantum resistant
- Block times can be shorter and the protocol will run faster in practice compared to Ouroboros.

### Source
- https://www.youtube.com/watch?v=hMgxZOsTlQc&feature=youtu.be 
- https://medium.com/unraveling-the-ouroboros/introduction-to-ouroboros-1c2324912193
- https://iohk.io/research/papers/

## Ethereum

Ethereum has two PoS proposals Casper the Friendly Ghost and Casper the Friendly Finality Gadget. Probably Casper the Friendly Finality Gadget will be implemented.

### Casper the Friendly Finality Gadget

CFFG has PoW and PoS at the same time. The reason behind this is, if they switched to PoS instantly, the miners would hardfork and continue to mine. 

PoS rewards will slowly scale **up**  
PoW rewards will slowly scale **down**

#### Summary

- Layering PoS on to of PoW.
- Validators simply put stakes in a smart contract.
- Validators vote on the canoncial chain, weighted by their deposit.
- Validators can  withdraw deposit  after a quite period where they don't validate. (Quite period is a time frame where other validators check your work and if it looks all fine, it can be can withdraw)
- Validators make money for converging and building a single blockchain
- Validators will lose money for not converging or forming two blockchains

- Every 50 blocks is called an epoch. Each epoch is a checkpoint where every block previous to the checkpoint are finalized. 
- Validators only validate the epoch blocks. Every other block is mined. 
- Need 2/3 vote to make a checkpoint justified.
- Finality is achieved when two consecutive checkpoints receive 2/3 votes

![](https://image.prntscr.com/image/1Q3IXQYuQIy4_HYBWJQxyw.png)
![](https://image.prntscr.com/image/wTT2D1xzRM2APeoT0k4Mqw.png)

##### Slashing Conditions
Burning validator deposits if malicious behavior detected

1) **Nothing at Stake**: Validators must not publish two distinct votes for the same target height
2) **No Surround Vote**: A validator must not vote within the span of its other votes

![](https://image.prntscr.com/image/MfcvNvn9QzWN85Me1Zqhwg.png)

When a validator finds evidance of an evil validator not obeying these rules, the validator will be rewarded and the stakes of the evil validator will be slashed.

##### Long Range Attack
Since the green checkpoints are accepted by everyone as the main chain, an attacker who has more hashing power will not be able to construct a new chain a replace the old one. 

![](https://image.prntscr.com/image/onqio68uS5iqwfOGrY92pQ.png)

##### Economic Incentives

- Why validators volunteer
- How poor performance & attackers are discouraged

If a fork happens between validators, the validators will be penaltizaled less on the chain they voted, more on the chain they did not vote. The validator will be penaltilzed if they did not vote at all (being offline)

![](https://image.prntscr.com/image/om76Run-S1mgY8wa_EaNuQ.png)

Note that in the other chain the penalties are swapped depending on which chain the validators voted.

![](https://image.prntscr.com/image/PiqB77tJRi_l2CzE-DGSow.png)

Onces there is consensus, everyone will be rewarded depending on if they have validated the correct chain or not. 

![](https://image.prntscr.com/image/HKqfPTG_TqGaZU526c5biA.png)

Note: One issue is if this continues to happen for a long time and assuming validators are not aware of each other then effectively there will be two main chains and the system will be hard forked essentially. The reason that happens is the validators who weren't voting will lose their stake and the power to vote on that chain. 

##### Censorship Resistance
Ethereum is trying to get rid of miners having the power and give the power to validators. However since miners are mining the blocks, they can agree and choose which block to mine thus cencor the network. This way validators will be secondary and have no choice but to go along with the miners. To avoid this, Adam Back found a method where miners will encrypt the block data and broadcast. Only after 6 more blocks are revealed the network can see inside of the transaction. This method would take power from miners. 

#### Conclusion

- Resist centralization
- Provide guarantees around finality (every 50 block)
- Consensus safety
- Provable liveness
- Availability > Consistency

#### Source
- https://docs.google.com/presentation/d/1fqnjL-2TqXjhHx8k7HRX7eUYnDK83adnlCLLH8Bk054/edit#slide=id.g29703948a2_0_2965
- https://arxiv.org/pdf/1710.09437.pdf
- https://www.youtube.com/watch?v=MyDocEQfBGA

### Casper the Friendly Ghost

Tendermint needs finalization however CTFG doesn't. Because of this CTFG can be more decentralized regarding validators

#### Conclusion
- Blocks are not finalized (like PoW)
- Available. Casper’s nodes can have their blocks fork until they come to consensus.
- Asynchronously safe.
- Live. Casper’s decisions can be live in partial synchrony, but are not live in asynchrony.
- Cartel-resistant. Casper’s entire premise is built upon resisting an oligopolistic attacker so that no colluding set of validators can overtake the protocol.
- Safety. Depends on each validator’s estimate safety threshold.


