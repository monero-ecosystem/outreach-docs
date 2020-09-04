# Triptych: A New Algorithm Protecting Monero Users

**“Monero hides the sender, the receiver, and the amount in a transaction. Triptych (pronounced TRIP-tick) is an upgrade for Monero that is faster, lighter, and more private.” - 1st of September, 2020**

Monero hides the sender, the receiver, and the amount in a transaction, with the details behind this behavior rich and evolving. This article covers Triptych (pronounced TRIP-tick), a new Monero technology that better hides senders, using less space on the Monero blockchain and less time in processing.

### _Ring Signatures_

Hiding senders in Monero takes more than just guarding addresses. All Monero is represented on the blockchain as outputs of transactions, called TXOs. Each TXO is labeled using a unique (one time) ID called the public key (also called a stealth address). By just viewing the Monero blockchain, TXO public keys absolutely cannot be connected to Monero addresses. Yet public keys themselves also need protection. It would be unacceptable for the flow of Monero among public keys to be transparent considering that techniques outside the blockchain could connect those public keys to people.

Monero movement among public keys is kept secret right now using what are called cryptographic ring signatures. With this approach, the public key for an actual TXO is hidden by grouping it with decoys (also called mixins). Looking at a transaction, there is no way to tell if the real TXO is being used or one of the decoys. You can see example input and output TXOs by looking up a transaction in a Monero blockchain explorer, such as [moneroblocks.info](https://moneroblocks.info/) or [xmrchain.net](https://xmrchain.net/).

How TXO decoys are selected from the blockchain has improved over the years. Initially, as a built-in part of the protocol, decoys were optional. Over time the number of decoys was increased and mandated to give the requirement of exactly 10 decoys today. Also, initially in the standard wallet, decoys were randomly sampled uniformly over all transactions. The sampling process improved over time to give the tailored random process, based on picking times from a special gamma distribution, that we have today.

The core ring signature algorithms have also improved. The original CryptoNote whitepaper gave a ring signature scheme different from the current more-efficient implementation based on Multilayered Linkable Spontaneous Anonymous Group (MLSAG) signatures. A widely anticipated enhancement, called Compact Linkable Spontaneous Anonymous Group (CLSAG) signatures, is coming soon and expected to further cut overall transaction size by about a fourth and verification time by a about a tenth (for a two-input, two-output transaction).

All these improvements have given Monero powerful anonymity. Every time Monero is spent, each real TXO source in the form of a TXO public key, already cryptographically disconnected from the sender's Monero address, is hidden among 10 decoy public keys that are chosen to resemble real possibilities. This deeply frustrates surveillance, all while the Monero software runs quickly and smoothly, giving a reasonable blockchain size and speed.

### _Challenges_

But Monero’s sender hiding is not perfect. Ten decoys are not always enough because some random TXOs might be identifiable. They might have previously been spent with public knowledge. The existence of blackball lists both show this as a potential problem and give a workaround to those with the motivation and initiative to add the list to their wallets. And there are other ways to identify decoys, including tying TXOs to pools and exchanges, estimating their validity in other transactions, and using timing probabilities.

Imagine a police lineup with one wrongly accused and 10 decoys. If the decoys were all known to a false witness, it wouldn’t work to protect the accused. The same is true with Monero ring signatures: hiding among decoys only works when the decoys are strangers, and for some adversaries, particularly resourceful adversaries, only 10 random picks might be inadequate. So why not just use more?

Well, for the MLSAG/CLSAG algorithm used by Monero, both the size of the transaction and the time to process it grow linearly (in the Big O computational-complexity sense) with the number of decoys. Using ten decoys balances the need for privacy with the need for a smaller blockchain and faster processing. Increasing the number of decoys would help with privacy, but also inflate the Monero transaction size—already several times larger than for Bitcoin—and bog down wallets doing validation.

### _Triptych_

Addressing this challenge is Triptych, a new algorithm for ring signatures developed by Sarang Noether and Brandon Goodell of the Monero Research Labs (MRL) with outside partner Arthur Blue (RandomRun). With Triptych, the size of the ring signature size grows logarithmically instead of linearly. Logarithmic growth is very slow, the best known growth pattern without having to resort to trusting someone to use then destroy randomness during set up (as was done for Zcash). Verification time still grows linearly with the number of decoys in Triptych, but verification can be batched and evaluated using specialized algorithms, which provides some speedup.

Triptych overcomes several challenges for ring signature application to Monero. It provides linkability. Monero’s ring signature technique must block the reuse of legitimate public keys to prevent spending a TXO more than once (so-called double spending). Triptych does this using linking tags that are similar to today’s key images. Triptych also supports the use of confidential transactions to hide Monero amounts. Special data called commitment keys enable proof that the Monero amounts in a transaction are legitimate without disclosing those amounts. These commitment keys with the signing keys and linking tags are the three components originating the name Triptych, meaning something of three parts.

### _Testing and Alternatives_

Triptych runs fast in practice. One of the creators, Sarang Noether, reported test code giving notable runtime improvement. Roughly, using 63 decoys with Triptych runs 10% faster than using 10 decoys with CLSAG. These results indicate fundamental improvement to Monero that will also be practical to field.

Work remains, though, as rigorous validation is needed for a new algorithm like Triptych to enter the Monero codebase. Though Triptych's algorithm paper has now been peer reviewed (and accepted to the ESORICS CBT 2020 Workshop), Triptych may still benefit from modification to the algorithms and the software implementing those algorithms, and the implementation may be further optimized to reduce validation time. Spending this effort on Triptych takes the place of work on alternatives.

One of those alternatives—a particularly promising one—is an advanced version of Triptych itself called Arcturus, developed by Sarang Noether. Arcturus further shrinks transaction size using a single cryptographic signature data bundle for the whole transaction instead of one for each input TXO. Arcturus and Triptych have comparable verification times. The price of the reduced size is an algorithm in Arcturus that requires mathematical assumptions not necessary for Triptych.

### _Summary_

With Triptych, and its extension Arcturus, Monero has a great new technology with the potential to reduce the size of ring signature data from growing linearly (with the number of decoys used to hide the sender) to growing logarithmically. If adopted, it could allow the number of decoys to increase without increasing blockchain size or CPU use in validation. Triptych’s technology continues Monero’s relentless progress in manifesting the possible and protecting the privacy and liberty of its users.
