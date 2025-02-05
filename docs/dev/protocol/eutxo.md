UTXO has many advantages over the account-based model used by Ethereum. It provides superior:

- **Privacy**, as UTXOs are one-time objects making it possible to formalise privacy leaks.
- **Scalability**, as parallel transaction processing is more straightforward in UTXO. UTXOs are also more friendly to known stateless client solutions.
- **Interoperability**, as off-chain and sidechain protocols. One-time objects are more straightforward to work with from an off-chain point of view.
- **Transaction Cost Predictability**, where the only on-chain action is validating the smart contracts. As a result, the transaction cost is significantly lower, and most importantly, the transaction cost is predictable, eliminating the need for ‘gas.’

Extended UTXO systems enable *Turing complete* smart contracts. This is a novel innovation that allows the latest generation of blockchains to reclaim the original model that Bitcoin used, but with a lot more power, adding support for more expressive smart contracts. 

 Ergo has a similar approach to Cardano’s eUTXO with its own Multi-Stage UTXO model that introduces the concept of *UTXO chains* and allows chaining together smart contracts of arbitrary complexity. 

A good introductory article can be found [here](https://dav009.medium.com/learning-ergo-101-blockchain-paradigm-eutxo-c90b0274cf5e) or [DeCo EU Layman Class #1 4-6-22 Basics of eUTxO](https://www.youtube.com/watch?v=SAWeW6wajEw)

## ErgoScript

ErgoScript is built considering Bitcoin’s security and privacy to make all kinds of complex financial contracts accessible. In comparison, Bitcoin’s design doesn’t allow loops or building any complex smart contracts on top of it. ErgoScript allows for self-replication; therefore, we can use it to create Turing-Complete processes in a blockchain.

Ergo extended Bitcoin’s UTXO model by introducing a readable UTXO design. This enables smart contracts to use UTXOs as data inputs without changing them. Therefore nodes are checking transactions rather than balances. In comparison, in Ethereum’s Account model, nodes check all accounts to validate the system.

UTXO allows for parallel computation, and it’s easier to compute atomic swaps in a non-custodial manner. 

Ergo takes the most secure and well-established features of Bitcoin and implements advanced new cryptographic features on its rock-solid foundations. This series explores our choices in creating Ergo, with the first article unpacking the advantages of the UTXO model.

When dealing with financial value, you cannot afford to take chances. Every architecture decision in a cryptocurrency platform has implications. While there are different ways to solve the same problem, some solutions are better tested and reliable.

## Account vs UTXO

### Intro

Like Bitcoin, Ergo uses the ‘UTXO’ (unspent transaction outputs) model rather than the Account model used by platforms like Ethereum. We have made this choice for several reasons, but first, it’s worth explaining how the UTXO or ‘Box’ model works.

Most people think that the balance of an account is a simple number that is updated when you send or receive funds. This is the obvious way to approach the problem; it is effectively how money works in the real world. Your bank account has a balance that is increased or decreased when different transfers are made in and out. The ‘Account’ model operates: transactions to and from the Account alter your balance on the blockchain.

The UTXO model, pioneered by Bitcoin, is quite different. You can think of this a bit like a person holding a series of lumps of bread dough, and their balance is the sum of these lumps or UTXOs. Lumps can be divided or combined before they are sent to a new address, but you always know where they came from. For example:

Alice has 100g of bread dough (100 ERG). She breaks off a lump of 75g and gives it to Bob, keeping 25g of ‘change’ for herself.
Charlie has 250g of dough, and he breaks off 150g and gives it to Bob, keeping 100g of change for himself.
Bob breaks 20g of dough off the 150g lump he received from Charlie and combines the resulting 130g with the 75g he received from Alice. He gives the total of 205g to Dave, keeping the 20g change for himself.

Dave now has 205g of bread dough, which used to belong to Charlie. Before Charlie owned it, 75g used to belong to Alice, while 130g belonged to Bob.

In the UTXO model, ‘lumps’ of coins can be combined and divided, but they aren’t mixed, unlike bread dough. You can follow the history of funds right back to the Coinbase transaction in which those coins were first mined. That’s very different from the Account model, where the balance of each Account is changed. (You can, of course, check the blockchain to make sure the Account says what it should, but that’s not intrinsically necessary like it is with the UTXO approach.)

### Why UTXO?

The UXTO model has several implications. For a start, each object is immutable – lumps of coins cannot be ‘edited’ like an Account balance is edited when a transaction is made. The balance is calculated from the transaction history when those coins first came into existence. 

That makes security much simpler because either a UTXO exists in the form you expect, or it does not exist. With the account model, you need to carefully check that the Account you’re dealing with is in the state it should be (and developers typically don’t do that correctly). This also makes UTXOs more friendly for off-chain protocols, like sidechains and the Lightning Network.

Accounts make storing the ‘state’ easier, but easy doesn’t always mean better. With Ergo’s extended UTXO model, state transitions are more explicit and cleaner – there are no unwanted surprises. It might be a bit more burdensome to deal with, but it’s a lot better and more straightforward security.


## Resources

- [Off-chain logic & eUTXO](https://ergoplatform.org/en/blog/2021-10-04-off-chain-logic-and-eutxo/)
- [The UTXO Alliance Announcement](https://ergoplatform.org/en/blog/2021-09-26-the-utxo-alliance/)
- [Interesting explanation on the eUTXO model and dapps built in it](https://youtu.be/Yt4Sg6rs80Q)
- [The Extended UTXO Model - IOHK Research](https://iohk.io/en/research/library/papers/the-extended-utxo-model/)
- [Understanding the Extended UTXO model - docs.cardano](https://docs.cardano.org/plutus/eutxo-explainer)

