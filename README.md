# Blockchains-and-Crypto
Notes for CS 5970 University of Oklahoma


Decentralization:
Distributed Consensus:
```
There are “n” nodes, each have an input value. Some nodes are faulty or malicious. 
```

A distributed consensus protocol has the following two properties:
```
1.The protocol terminates and all honest nodes are in agreement on the same value
2.This value must have been proposed by some honest node
Ex: When Alice wants to pay Bob she broadcasts the transaction to all Bitcoin nodes 
```

Why consensus is hard (esp. in the Bitcoin context)?
```
Nodes may crash
Nodes may be malicious
Peer-to-peer network is imperfect
•Not all pairs of nodes connected (and may participate)
•Faults in network
•Latency

Byzantine generals problem: Consensus impossible to achieve if 1/3 or more generals are traitors
 
•Fischer-Lynch-Paterson (deterministic nodes): consensus impossible with a single faulty node (under certain conditions)
```

Mining incentives:
```
Block Reward:
Creator of block gets to
• include special coin-creation transaction in the block
• choose recipient address of this transaction
Value is fixed: currently 6.25 BTC, halves every 210,000 blocks created (or 
every 4 years at the current rate of block creation)
• We are now in the fourth period – first period block reward was 50 BTC
Block creator gets to “collect” the reward only if the block ends up on long-
term consensus branch!
• Subtle but powerful trick: Incentivizes nodes to behave in way that will get other 
nodes to extend their block

Transaction Fees
•Creator of transaction can choose to make output 
value less than input value
•Remainder is a transaction fee and goes to block 
creator (that first puts that transaction into that 
block)
•Purely voluntary, like a tip
• But system will evolve, and will become mandatory, as Block 
```

Bitcoins implied consensus:

```
Protection against invalid transactions is cryptographic, 
enforced by consensus
• Protection against double-spending is by consensus
• You’re never 100% sure a transaction is in consensus branch. 
Guarantee is probabilistic
```
Key Ideas of implied consensus:
```
1. In each round (corresponds to a different block in the 
block chain), random node is picked
2. This node proposes the next block in the chain
•  No consensus or voting done by this node!
3. Other nodes implicitly accept/reject this block• by either extending it 
• or ignoring it and extending chain from earlier block
4. Every block contains hash of the block it extends
```

Consensus algorithm (simplified)
```
1. New transactions are broadcast to all nodes
2. Each node collects new transactions into a block
3. In each round a random node gets to broadcast its block
4. Other nodes accept the block only if all transactions in it 
are valid (unspent, valid signatures)
5. Nodes express their acceptance of the block by including 
its hash in the next block they create
```

Essentially:
Distributed Consensus:
```
Which transactions were broadcast on the network
● Order in which these transactions occurred
-> Result of the consensus protocol: Single, global transaction 
ledger for the system
```
Incentives to miners:
Mining reward (block reward + tx fees) > mining cost(hardware & electricity) = PROFIT
```Complications:
• Fixed (hardware) vs. variable (electricity) costs
• Reward depends on rate at which miners propose blocks (ratio of their 
hash rate to the global hash rate)
• Cost in dollars, but reward in BTC -> profit depends on exchange rate
Solving more than 1013 hashes to obtain 6.25 BTC at current 
exchange rate is profitable!
```
***PoW(proof of work):***
```
To approximate selecting a random node: select nodes in 
proportion to a resource that no one can monopolize (we 
hope)
• In proportion to computing power: proof-of-work 
(Used in Bitcoins)
• In proportion to ownership of the currency: proof-of-
stake (Not used in Bitcoins – but a legitimate model used in 
other cryptocurrencies)
```
**3 Properties**:

```
difficult to compute:
• As of today: difficulty level is over 10^13 (little under 16 trillion) hashes/block
• i.e., size of target space <= 1/10^13 size of hash’s output space
• Such a computation not possible with commodity laptops
• Technically anyone can mine -> however mining power is concentrated in 
a mining ecosystem

parameterizable cost:
Nodes automatically re-calculate the target (size of target space 
as a fraction of the output space) every two weeks
GOAL: AVERAGE 10 MINS
(Alice wins next block) = 
fraction of global hash power she controls

trivial to verify:
Nonce must be published as part of block
Other miners simply verify that
Any node or miner can 
verify that the block was correctly mined
```
51% attacker:
**CAN**:
```*Suppress transactions from blockchain
*Destroy confidence in Bitcoin```
**CANT:**
```*Steal coins from existing address
*suppress transactions from P2P network
* change the block reward
```
