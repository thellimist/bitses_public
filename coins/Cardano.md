# Cardano

- Cardano uses PoS and DPoS at the same time. 
- They will create a [debit card](https://www.cardanohub.org/en/shop-with-cardano/)
- It has a Treasury
  - ADA currently doesn't have fees, so users can send and receive ADA for free. Ultimately, transacting ADA will have a nominal fee that will be collected by a central treasury,

## Consensus Algorithm

https://medium.com/@thellimist/how-proof-of-stake-work-in-different-blockchains-518da229f486

## Treasury 

Currently it's not decided enitrely. The general outline and security proprosals are handled. All votes are essentially putting stakes. The treasury should be used for projects that'll improve Cardano. 

Getting money to treasury
1) Mint
2) Tax
3) Donation

There are 4 types users:
1) Voter: Can vote or give the votes (stakes) to expert.
2) Expert: Can vote or give the votes (stakes) to another expert. 
3) Commitee: Randomly selected nodes. They count the decsion, finilize the decision making process, trigger the distribution of the decision.
4) Project proposers: They propose the project so people can vote and give grant from the treasury.

All votes are done using NIZK for privacy. 

If the cost is too high for calculating the results of the ballot, the commitee can randomly take percentage of the ballot, calculate that and execute.

If most of the Commitee members are evil
1) They can read the results before anyone else
2) They can avoid the ballot to conclude
3) They can **not** change the election result.
