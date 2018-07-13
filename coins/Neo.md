# Neo

Consensus algorithm is Delegated Byzatium Fault Tolerence (dBFT). It's a type of dPoS where the bookkeepers (validators) vote a single bookkeeper randomly where that bookkeeper will proposes the next block and others validate. If something fishy goes on, they simply change the selected bookkeeper and move on. 2/3 nodes should have consensus for a block to be generated. Meaning 51% attack turns into 67% attack of bookkeepers. Additionally dBFT has finality meaning it can not fork. It is said that this number will be between 1 to 2 dozens.

Neo has two tokens:
1) NEO: NEO token has two use cases. (1) NEO token can be used to select the bookkeepers. (2) GAS is distributed to NEO token holders
2) GAS: This is the real token which has value in transaction and used for smart contract fees. GAS is the revoulationary part of Neo. They have split the voting token and token which will be used. This allows prices to be more predictable.

Neo doesn't aim to solve the transaction problem. Rather it's trying to solve the Smart Contract problem. NEO and GAS are not inflationary. There are 100M  tokens of each. However Neo team has the ability to generate both. 

Neo has:
- NeoVM: Allows any language to be compiled and run on a lightweight VM. Initially C#, Java. Later on  Python, C++, Golang, JavaScript will be supported. 
- NeoFS: DHT for storage
- NeoX: Interchain communication protocol
- NeoQT: Quantum Resistant

NeoX is the most interesting one. Neo not only tries to solve public computation problem, it also tries to solve private chain issue. Another way to think is Neo is b2c. NeoX is b2b. Any private Neo chain can comminicate with other private chains or the original public chain of Neo. 

## Issues

- The current Neo voting system has a flaw where 1 NEO token is 1 vote and voting for self requires min 1000 Neo tokens however each bookkeeper has one vote after selection. Cartels can agree with each and vote each other. They'd hold a lot of bookkeeper seats with not a lot of tokens and it'll be very hard to get rid of them since their # of tokens will only increase. Tl;dr Neo is prune to cartels. 
- Neo claims to solve Byzatium General Problem however they have a special transaction type named "IssueTransaction" which allows a single private key owned by NEO team to generate as many NEO as they want. This means that there is an emperor which can overwrite the generals. They don't solve the deecentralization problem. (Update: I've read some posts that this might not be the case) 
- Since Neo is an Emperor and obligated to Chinese law, Chinese Government may have ultimate power on this blockchain.
- There will only 1 to 2 dozens of bookkeepers. This allows faster blocks since less nodes need to have consensus however it also decreases the decentralization and openness part. 
- Neo team stated they can support 1000tps however the simple ICOs have slowed down the network significantly. 
- Neo only has 27 smart contracts deployed 
- Deploying a smart contract costs 500 Gas which is $1000 for price. This is expensive compared to other Smart Contracts platforms.

## Source
- [Neo has an emperor](https://www.reddit.com/r/Antshares/comments/6nemjr/in_response_to_neo_vs_eth_security_dbft/dk9055i/?utm_content=permalink&utm_medium=front&utm_source=reddit&utm_name=Antshares)
- [Gas price / count](https://www.reddit.com/r/NEO/comments/6ssuit/gas_price_cleared_up_by_da_hongfei/)
- [Bookkeeper count](https://www.reddit.com/r/NEO/comments/76wqeq/how_many_bookkeeping_nodes_will_there_be/)
- [ICOs slow down the network](http://storeofvalueblog.com/posts/neos-secret-scaling-issues/)
- [Deployed Smart Contracts](https://neotracker.io/browse/contract/1)
- [Smart Contract Deployment Fee](http://docs.neo.org/en-us/sc/tutorial.html)
