# Storj

Storj is a a Peer-to-Peer Cloud Storage Network

Storj uses a custom DHT just like IPFS. It has added 
1) Security
2) Auditing
3) Communitcation 
4) Bridges
modules. 

Storj has added a system called Bridge. This is the most important part of the system. Storj is a protocol and a company. The protocol has all the features implemented in it. The user has a single point of contact called the Bridge. Bridge software they made which allows additional logic to run on top of the protocol such as paying monthly bills, converting fiat to tokens, some extra smart logic on top of the protocol which will fit the companies use case better. Companies can have their own Bridge and even have connection with other Bridges. However Bridge makes the system centralized. Storj markets as 99.99999% availability however that's the data's availibility. The bottle neck is the Bridge where when the Bridge fails, user will not be able upload new data. However old users can still fetch data since that is p2p. 

App developers can easly use Storj using it's API and select which Bridge they'd like to use. The Bridge owner should implement the market needs. 

They have a reputation system in the protocol however
1) I'm not sure if it works as expected. Seems really buggy. (like most software)
2) Is prune to reputation attack. (They are aware of this but no one has a solution. They're hoping that there won't be Reputation Sybil attacks. 

# Comments
- The network is slow atm. They need a few years to be competitive.
- The supply for storage is a lot more than the demand. This means the storage owners will earn little amount of money for their work. 
- A user needs good connection and good availability. Normal people can't use this.
- Promise is 2x cheaper than Cloud Storage and %50 faster not 100x. 
- Roadmap includes public and private data storage. They would want to be a storage CDN as well.
