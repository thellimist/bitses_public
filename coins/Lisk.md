# Lisk

- Blockchain written in JS .
- Has sidechains (details will be below)
- Uses DPoS as consensus algorithm. Only 101 Delegates can be selected. Block time is 10 seconds with 25 transactions per block (2.5tps). It is said that it can scale to thousands of tps in the future (like Ripple, Stellar)

## Side Chains

![](https://cdn-images-1.medium.com/max/2000/1*Hpm8pdFndHGcj8iQbyCfgQ.jpeg)

Like Skycoin, Lisk allows people to create a sidechain, write a new chain with different block limits, frequency, custom logic, different consensus algorith etc. People can write their own sidechain and use blockchain as their database. Sidechains have multiple benefits

Pros:

1) Security: A compromised sidechain will only lose whatever is there. Other applications won't be effected.
2) Speed: Sidechain can adjust itself to scale as it wants. It is not depended on the mainchain.
3) Tokenization: Sidechains can create their own tokens rather than using mainchain token LSK allowing custom market dynamics

Cons:

1) Trust: People need to trust the sidechain owner. The reason is, sending LSK to a sidechain is basically sending LSK to the sidechain owners mainchain wallet. Then the sidechain wallet of the user will have a tx from the sidechain owners wallet with the amount of LSK they have sent. If the sidechain owner wants to run away with the LSK they can. There might be extra logic that can make it a bit safer however I haven't seen it in their roadmap.
2) Decentralization: Sidechains have 2 options, first is to have nodes which would run the sidechain, second, pay mainchain delegates to run the sidechain and pay fees. 

Sidechains are generally a much better way than how Etherium is handling custom logic. Side chains do not run smartcontract. They are a different blockchain with custom backend. However if someone implements smartcontracts, they may have the ability to run those (if needed). Another benefit of sidechains is there might be 100s of sidechains one for login system, other for file storage etc. The comminication would be much easier than separate blockchains because they are all implementing LISK Protocol Interface. 

## Fees
Currently Lisk has constant fees (0.1 LSK) for each transaction which is really expensive compared to the market. They do plan to add dynamic fees in Lisk 1.0.0
