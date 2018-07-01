# EOS
- DPoS
- 21 block producers
- new block every 3 seconds

## Accounts
The EOS.IO software permits all accounts to be referenced by a unique human readable name of 2 to 32 characters in length. A user has to pay to get an account. Account names also support namespaces such that the owner of account @domain is the only one who can create the account @user.domain.

A single private key can create multiple permissions. You can share keys with permissions you've created with other people such as friends or apps. 

A good example can be seen [here](https://github.com/EOSIO/eos/wiki/Accounts%20%26%20Permissions#42-multi-sig-account--custom-permissions)

## Community Benefit Application

Users can elect 3 community benefit applications also known as smart contracts. These 3 applications will receive tokens of up to a configured percent of the token supply per annum minus the tokens that have been paid to block producers. These smart contracts will receive tokens proportional to the votes each application has received from token holders. The elected applications or smart contracts can be replaced by newly elected applications or smart contracts by token holders.

## Account Recovery 

Only stolen keys can be recovered. Forgotten keys are forgotten. 

1) Owner and a 3rd party company already has a multi-sig operation locked. 
2) Private Key is stolen (it can be any account with any access level)
3) Owner shares his key with the partner and unlocks the multi-sig operation.
4) The operation changes the private key for that account and provides it to the user.

This method can also be used for allowing some operations to have delays such that, if a user does 100+ EOS operation, send email and sms to the user. If the user does not provide the the multi-sig operation then the action is invalid. It's basically a multi-sig operation built-in the protocol (I guess). Users can subscribe to other operations for their account. Account Recovery is just one app.

## Programming

Block producers publish their available capacity for bandwidth, computation, and state. The EOS.IO software allows each account to consume a percentage of the available capacity proportional to the amount of tokens held in a 3-day staking contract. For example, if a blockchain based on the EOS.IO software is launched and if an account holds 1% of the total tokens distributable pursuant to that blockchain, then that account has the potential to utilize 1% of the state storage capacity.

- Every block producers can calculate the amount of computation a message took. If it's higher than allowed, it can discard the operation. Even if one block producers says it's within their power, the computation will happen.
- Uses EVM and WASP as a language. C, C++, Python, Solidity and Rust can be used too. (Probably other languages can be used as well since they're using WASM which is llvm based. 

## Others
- Max  5% inflation, all given to block prodcers. Zero fee transactions. 
- A transaction can be split to multiple accounts (used for apps such as paying bill in a restaraunt). It's relatively slow. 
- Since the inflation is given to the block producers, the value of EOS that can be earned will be the minimum limit for the computational and storage power block producers will use. 
- Block producers vote 17/21 to freeze an account. Bad actors can be voted out (or not...)
- There is a proper [way](https://github.com/EOSIO/Documentation/blob/84f3da2b7fac118618f1806a1aaca0410b9d29b7/TechnicalWhitePaper.md#upgrading-the-protocol--constitution) to upgrade protocol which takes 2-3 months.
- EOS network vulnerable, as the nothing-at-stake problem remains unsolved.

## Open Questions
0) No idea how [this](https://github.com/EOSIO/Documentation/blob/84f3da2b7fac118618f1806a1aaca0410b9d29b7/TechnicalWhitePaper.md#deterministic-parallel-execution-of-applications) works.

1) How does smart contracts work?

2) In the wiki it is stated that the technical limit for a transaction is 1ms. This means only really basic operations are possible with EOS. Is it possible to run high computation required contracts on EOS?

3) I remember when the founder of EOS was working on Steem, he mentioned about using sidechains for smart contracts. I couldn't see anything related with applications running on sidechain. Does EOS use sidechains for computations?

4) How does updating a smart contract work? (Please explain technically how the data os shared and how the old smart contract users point to the new one on an immutable block)

5) There are 21 block producers. How and where does EOS store the data of multiple applications (where some may be CDN like file storage services)
