# Enigma: Decentralized Computation Platform with Guaranteed Privacy
Enigma is a privacy protocol - a blockchain-agnostic, second-layer network for private computations that protects sensitive data.

Intro Video:
https://youtu.be/qeJn8YgDIlw

## Technology
Enigma has 3 parts:
1) Public Ledger: For the storage (Enigma needs an external blockchain to work) 
2) Custom (Secure) Distributed Hash Table (DHT): For off chain storage
3) MPC: For private computation

Enigma provides people to share their personal information with the following 3 attributes to a user/institution.
1) Data Ownership
2) Data Transparency and Auditability
3) Fine-grained Access Control

Enigma API has 4 protocol calls where Blockchains should implement.
1) Generating a compound identity
2) Permissions check against the blockchain
3) Access Control Protocol
4) Storing or Loading Data

### Example Use case
To illustrate, consider the following example: 

A user installs an application that uses Enigma platform for preserving her privacy. As the user signs up for the first time, a new shared (user, service) identity is generated and sent, along with the associated permissions, to the blockchain in a Taccess transaction. Data collected on the phone (e.g., sensor data such as location) is encrypted using a shared encryption key and sent to the blockchain in a Tdata transaction, which subsequently routes it to an off-blockchain key-value store, while retaining only a pointer to the data on the public ledger (the pointer is the SHA-256 hash of the data). 

Both the service and the user can now query the data using a Tdata transaction with the pointer (key) associated to it. The blockchain then verifies that the digital signature belongs to either the user or the service. For the service, its permissions to access the data are checked as well. Finally, the user can change the permissions granted to a service at any time by issuing a Taccess transaction with a new set of permissions, including revoking access to previously stored data.

![](https://image.prntscr.com/image/l4MAFvMeSv2W7jVkAE6OMw.png)

### Secret Contracts
“Secret contracts are like smart contracts, in that they allow executing contracts (i.e., code) with high degree of integrity, which in simple words mean that no one can manipulate the results. However, unlike smart contracts, the underlying input data/state being processed is not visible to anyone, including the nodes in the Enigma network that actually carry out the computation.

Think of a smart contract that lives on the blockchain and tries to find correlations between specific genes and certain diseases. On any blockchain today, this equates to people sharing their genomic data openly for everyone to see. With secret contracts, their data would remain private, because it’s always encrypted.

The way these work under the hood is by one of several means - secure hardware, secure multiparty computation (MPC), or fully homomorphic Encryption (FHE). Enigma employs the first two to enable this with scale (FHE, while theoretically possible, is not likely going to be practical anytime soon).

#### Difference between Etherium zkSnarks
Note that ZKP/zkSnarks (which are an amazing scientific achievement) are a complementary, but not a sufficient, solution to the problem of privacy. ZKP, in general, allow proving the correctness of a computation to others without revealing the underlying data - but the prover still needs full access to the data. This means that with ZKP someone has to see the data - so you can’t, for example accomplish the example above. There was also an exploration of such a system before called Hawk, which had to rely on a trusted manager with the privacy of the data for this exact reason.”

### Economy Model
Enigma has a fixed amount of 150M tokens

The token is used in 3 different ways:
- As a security deposit to ensure that anyone participating in the network is being honest. If they try to tamper with the data they would lose their deposit.
- As payment for any sort of computations or actions done on the network (Gas).
- As payment for fees to store data on the platform.’

A user who wants to join, opens a Enigma Master Node and starts computing and storing data for others in exchange for ENG. 

### Security
Enigma relies on the first-layer network (blockchain) regarding security. If a node is behaving, the check is done by the main chain not Enigma network.

### Unknowns
- I didn't look enough time to digest how Enigma works I don't have enough understanding of [MPC](http://www.wikizero.info/index.php?q=aHR0cHM6Ly9lbi53aWtpcGVkaWEub3JnL3dpa2kvU2VjdXJlX211bHRpLXBhcnR5X2NvbXB1dGF0aW9u) and how it scales. Espicially how it do heavy computations decentrilized and secure.
- Enigma will provide an API to other Blockchains. The other blockchain owners should implement Enigma (with most likely a softfork).

## Competitions
I'm not sure how Enigma can do heavy computations however if it can it has more use cases than Golem since Golem is public. 
It also has more use cases than IPFS because the data stored is private, also, large data can be stored using Enigma.

## Others
- Protocol is not opensourced. It'll be opensourced once it's released (Q1 2018)
- It can be integrated with Tangled. 
- If a node crashes or disconnects while computing something, it'll be penaltilized all will lose all it's deposit

## FAQ
* O kadar privacy'e ihtiyac var mi yoksa zkSnarks ihtiyaclarin %95'ini karsiliyor mu?

zkSnarks ihtiyaclarin cogunlugunu karsiliyor ama herif senin data'ni hic okumasin dersen, ultra encription sagliyor Enigma. 

* Bir contract hem ETH, hem NEO, hem NAS tarafindan calistirilabilir mi? Eger evet ise ENG hepsine katki sagliyor olmali, fakat NASda da bu tarz ozellikler varsa ENG kullanmaya gerek yok, direk NAS kullan. Yani first layer ETH tutarsa buna gerek olabilir, ETH tutmazsa buna gerek olmaz gibi?

Enigma icinde bir contract'i, Enigma'ya baglanan herkes kullanabiliyor. Mesela ben Enigmada Health datami tutuyorum. A blockchain uzeirnden X appina yetki verdim Health datasi icin. B blockchaini uzerinden Y appina da yetki verebilirim. Data Enigma'da duruyor.
