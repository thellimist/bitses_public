# OmiseGO

OmiseGO is a blockchain using [Tendermint PoS](https://github.com/demiculus/bpc_general/blob/master/level4sum/technology/Proof%20of%20Stake.md#tendermint).

The core principle of OmiseGO is to have a blockchain which connection all blockchain and digital fiat assets in a light manner. They'll create a DEX on top of OmiseGO chain. There are two sets of tokens which are mentioned in the whitepaper.  

1) BTC tokens: Lightning network which are using BTC like tokens (LTC etc..) can connect to OmiseGO.
2) ETH tokens: ETH, ETC20 and other ether based tokens can connect to OmiseGO using smart contacts.

There are Clearing Housees which are validators for OmiseGO PoS chain. These validators put stake on Ethereum smart contracts. If they behave bad, their stakes will be slashed. These validators are responsible for transfering funds from BTC to ETH inside OmiseGO network. OmiseGO assumes Clearing Houses will have huge amounts of tokens. They'll operate as a decentrazied exchange with orderbooks etc. 

- OmiseGO will use Plasma (and might use Raiden Network) to scale. 
- OMG is the token for OmiseGO network and will be used to give fees to Clearing Houses

## Limitations

- When someone in the OmiseGO network tries to do something malicious, every transaction will need to be published to mainchains. However currently Plasma Cash update from Vitalik solves this problem where each individual should monitor their own transaction. Alternatively they pay a 3rd party to monitor their transactinos.
- OmiseGO focuses on speed rather than security. They will not implement Zero Knowledge Proofs cause it's too slow. Basically transactions will be sudo anonymous like BTC.
- It assume Ethereum will have finality (PoS)

## Additional info
Lots of partnerships -> https://www.reddit.com/r/ethtrader/comments/6nldxs/why_i_have_decided_to_invest_in_omisego_omg_now/

## Unknowns

- Tendermint can halt. Does OmiseGO have a solution for this?
