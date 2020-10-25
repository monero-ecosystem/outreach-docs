# Aram Jivanyan

Aram is a cryptographer at Zcoin and the founding CEO of Skycryptor, Techstars company pioneering the development of proxy re-encryption algorithms. At Zcoin Aram has invented the Lelantus protocol and now is working on scaling it to the next level. Before founding Skycryptor Aram was a senior cryptography researcher and development team lead at the American University of Armenia where the scientific group conducted cryptography research for big industrial partners.

https://youtu.be/gb53Fe2iuqg

_**Abstract**_
---

We propose Lelantus, a new anonymous payment system which ensures both transactional confidentiality and high anonymity with small proof sizes, short verification times and without requiring a trusted setup. We show how to support efficient aggregation of the transaction proofs, so that the proof verification, while asymptotically linear, is very efficient in practice. Lelantus builds on the techniques of Con fidential Transactions, Zerocoin, and 1-out-of-Many proofs and its efficiency is particularly well-suited for enabling private blockchain transactions with minimal trust required while employing well-studied cryptographic assumptions.

_**Transcription**_
---

Hello everybody! So, my name is Aram Jivanyan. I'm a cryptographer at [Zcoin](https://zcoin.io/) which is a privacy cryptocurrency, and happy to be here today talking to you about [Lelantus](https://lelantus.io/), our new privacy protocol for anonymous and confidential transactions. But before continuing my talk, I would like to thank you Brandon and Sarang for inviting me and especially Sarang for the great job he did in making pierce implementation of Lelantus and its analysis and also the great feedback he provided me continuously during the last few months, thanks. 

So as a brief outline of my talk, let me start by describing [Zerocoin](http://zerocoin.org/) - the protocol which is currently empowering the Zcoin network - which discusses limitations sure why we want to move on beyond it. Next, I will provide high-level characteristics of Lelantus and then we go deeper into its cryptographic details and then briefly compare with existing privacy techniques. And I will finish my presentation by identifying few open problems and also promising research directions, which could help to improve Lelantus farther, okay. 

So Zerocoin is one of the first technologies which enabled highest anonymity of transactions. It enables the user to burn coins and then spend them to bring new coins. And during the spend, the zero-knowledge proove us, provided, that the spent coins was one of the previously minted coins without revealing its origin. And although it provides high-level of anonymity, it absolutely lacks confidentiality. Moreover, Zerocoin can work only with fixed denominated coins which results to a poor user experience. And the proof size in a Zerocoin we're huge, about 25 kilobyte and the verification time is also quite high, about 300 milliseconds. 

Zerocoin is using [RSA](https://blockonomi.com/rsa-cryptography/) [accumulators](https://en.wikipedia.org/wiki/Accumulator_(cryptography)), which means that it also requires some type of trusted setup to generate these accumulator parameters. Although, Zcoin, we avoided of this trusted setup, by using RSA challenge parameters generated in 1992. And last but not least, now this protocol is absolutely broken. It's not secure at all, so we created Lelantus to address this functional and the performance limitations of Zerocoin. 

It's a new brand-new design inspired by Zerocoin and confidential transaction concepts which leverage one out of many proof constructions and bullet proofs and it doesn't require trusted setup. Proof sizes are relatively small, they're about 1.5 kilobyte per input spent, it enables efficient verification of transaction in pages by supporting large anonymity sets as of up to 50-65 thousands or even 100k. Lelantus enables to works with coins of arbitrary amounts and also enables direct anonymous payments in some extent.

So, let's see how it works. It provides two basic type of transaction. First one: mint transaction, enables the users to mint its base coin into cheated coins of arbitrary values and provides a balance proof that the output coin values sum of the base coin-- minted based coin amount. And it allows to do joint split transaction which mean you can merge, split, and redeem coins without revealing the input coin origins and also preserving the confidentiality of both input and output coin amounts.

It uses new cryptography constructions called one out of n proofs to hide the origin of inputs, but also to generate a balance proof. Let's see how it works. So one out of n proofs, is a sigma protocol for knowledge of one out of n commitments, C0, C1, Cn minus 1, being a commitment to 0. To be clear, we are working with [Pedersen Commitments](https://www.getmonero.org/resources/moneropedia/pedersen-commitment.html).

So the idea behind this protocol is saying that one out of n commitments contains 0, is equivalent saying that there exists an index l so that the product of Ci to the delta il, will be a commitment to 0. Delta i,l here is the [Kronecker delta](https://en.wikipedia.org/wiki/Kronecker_delta), it equals to 1 only when the index i is equal to l and 0 otherwise. And assuming that the number N is a power of 2, we can write these indexes i and l in binary, and we can reformulate what we want to prove as the product of Ci to the product of delta ij,lj being a commitment to 0. Does this make sense? Okay.

So the prover starts by making commitment to his index l to making commitment Cl1, Cl2, Cln to the bit values. And next it engaged in two n parallel Sigma protocols to demonstrate the knowledge of opening of these commitments to be bit binary values to lj equal to either 0 or 1, and during these proofs n elements are revealed of the following form, f1, f2, f to n where fj equal to lj times x plus aj. So, let's make the following denotions, let's say denote fj,1 to be equal as fj and we can see that it's equivalent to b, it's equal to delta 1,lj times x plus aj because it's simple if the bit lj is 1, then delta 1,lj is also 1 and 0 otherwise,

The same way let's denote fj,0 as x minus fj which will be equal to delta 0,lj x minus aj. And for each index i we can construct polynomials pi,l x as a product of these values fj,ij. You see it will and easy to see that the polynomial pi,l x will be the only one polynomial of degree n amongst all this p0, p1, pn minus 1 because only delta l l will be equal to 1 and it will be 0 otherwise for all other indexes. 

So the prover can compute the product of Ci to the product of these polynomials and in its initial message, the prover can also construct special ciphertext which will be able to cancel out this low order polynomials in this equation. Ups, sorry. Because the generation of these coefficients doesn't require the advanced knowledge of the value x so it can be constructed by prover at the proof generation time. So we will end up by proving that the product of commitments Ci to the power of product fj,ij multiplied with the product of these magic commitments will be commitment to 0. 

Hope this gave just some high-level insight about how one out of n proof works. We cannot go deep into the rabbit hole here, but this is the whole protocol, this is the initial construction of [inaudible]. You see, it's relatively simple, the proof and verification just fit in one page. That's it. And the one important thing to observe here is this proof transcript contains also this value. Which is the encoding of the commitment randomness r. This is important because this will be used for generating the balance proof. 

Let's see how straightforward is to build a Zerocoin like scheme having this one out of n construction. A scheme which enables the user to mint coin of some fixed value and then spend it anonymously without revealing its origin. So for minting a coin the user just generates a random coin serial number S and then commits to the serial number by using some randomness r. This will be the users coin which will be published to blockchain. And then, the user wants to spend it, he just reveals the coins serial number S - and revealing serial number is important also for preventing double spending attacks - and when the serial number is revealed, both prover and verifiers can homomorphicaly subtract the serial number from all commitments, like if we have the previously minted commitments or previously minted coins. You can subtract this coin specific serial number from all commitments and result to a new set of commitments where one of them will already be commitment to zero and you just prove that you know which one is the commitment to zero. 

Lelantus is following to the same approach for ensuring anonymous spends of input coins. But as we want to support coins of arbitrary amounts here, let's encode also the coin value into the commitment.

So in Lelantus construction coins are commitment to coin serial number by using a random value R and also the coin values. So we are using three independent generators and we'll have to refer to this construction as double blinded commitment. And it's worth noting that the serial number is not generated randomly, but it's generated by hashing of some public key, first generated public key, which corresponding witness, referred also as spending key, will be used to send a transaction when this coin is spent.

So this diagram shows the one out of n construction scheme used in Lelantus. It's a modified version of more optimized protocol, not on the original cross protocol but an optimized version of it and also contains some our own modifications which are done to support double blinded commitments and also the balance per generation process. Now important thing to observe here is that this proof transcripts contains, publishes these two values zV and zR which are the encodings correspondingly of the coin value V and coin randomness R.

So assuming that the [inaudible] transaction outputs n new coins, and it consumes n old coins, the transaction transcript will contain this output coins and also n old one out of many proofs for each spent input and all verifiers can independently do the following computations. They can compute the value A, which is a product of output coins to the power xm, which, based on the homomorphic properties of the an online commitment scheme, will be commitment to the sum of all output coins. Yeah. And verifiers can also compute a value B as a commitment of the sum of this value zV and the sum of the values zR multiplied with the product of some auxiliary data - which was also contained in the proof transcript - and the result will be a commitment to the sum of all input coins.

So without revealing these input values or without even revealing which coins have been spent, we will end up having commitment to the sum of all input coins. And if the transaction balance is preserved is already simple, the prover, it's enough for the prover, to provide a proof of representation of the value A over B with respect to the generators g and h2.  

Okay, this is about how we make anonymous spents and how we provide balance proof so now let's see how we enable page verification of this proofs. A verification of one out n proofs is linear from the number of n and it boils down to this big multi-exponentiation. Yeah, this, here, the generators, are all transaction specific because as you remember as we described in the Zerocoin scheme this generators are computed by taking this commitment Ci and dividing to j to the power St, where St is the coin serial number spent doing the transaction.

The good thing in our set up is that during the spend, these serial numbers are explicitly revealed. So we can leverage the fact that the serial numbers St are published on the blockchain and incorporate that into the verification operation, and reformulate the verification operation with the alternative equation where the generators will be transaction agnostic because the C and the St are already on this right side of the equation. This enables to perform verification of many proofs in batches and helps to save n exponentiation per each extra proof when we work within the same anonymity sets. This results to huge savings.

As you can see from this table the average cost of one proof verification between these anonymity set of size 16,000 can be as low as 12 milliseconds, and within the anonymity set of size 65,000 it can be as low as 35 milliseconds.

Last, let's discuss how we enable direct anonymous payments when the outputted coins can be spent only by dedicated recipients. In our structure in order to spend this coin - which has the following structure, it's a commitment to the coin serial number S - the user should possess all the secret values, the coin value, randomness, and also the witness or spending key which was used to generate the serial number. And we can use some [Diffie-Hellman](https://wiki.openssl.org/index.php/Diffie_Hellman) like exchange process to make this witness accessible only to the recipient. Like in very simple setup, the receiver can generate new public address and the sender can generate the random y and create a public key which witness is accessible only to the receiver, of course, this can work also with two alt key based [stealth addresses](https://www.mycryptopedia.com/everything-need-know-stealth-addresses/) protocol.

Okay, I'm sorry if you will find some inaccuracies in this number, but just to highlight that, just to briefly compare Lelantus with other privacy techniques, we see that the proof sizes and verification times are quite comparable with existing Monero's performance while ensuring larger anonymity sets. We should make this construction more immune against different types of attacks including flooding attacks or transaction graph analysis attacks.

Of course, it's hard to beat Zerocash performance but unlike Zerocash we don't require trusted setup, we rely only on standard cryptography asumption and which is more important, in my opinion, we don't use complex arithmetic circuits. So it uses a simple cryptography construction which is easy to implement, easy to test, easy to crypto analyze, easy to implement on any platform. 

So just as a conclusion, this is a new protocol and there is a lot that can be done to improve it further. Of course. We would love to see an alternative approach for direct anonymous payments which results to untraceable coins, but the research problem which takes me busy this moment, full-time, is how to scale one out of n proofs. I believe it's possible, so, and now we have some progress on building two layers one out of n proofs which promised to significantly reduce the proof time. And also, I think it's possible to design, I'm sorry, to design more efficient M out of N schemes. If you can design efficient amount M out of N schemes, this will optimize transaction size with multiple inputs. And also, it will be interesting to see how we can support multi asset transfer or also enable auditability of transactions for enterprise use cases.

Thank you, happy to answer questions.

Does anybody have any questions for Aram?

Thank you for your talk, I think Lelantus is very very cool. My question is, so when you're working with Zcoin and moving away from the Zerocoin protocol, there is an intermediate protocol you guys are working on, is there kind of a timeline for when and if, Zcoin intends to deploy Lelantus? Would it be in its current form or is the intent to wait until you get some of these kind of efficiency issues taken care of like you were talking about?

Yeah, sure, so that our current release which we call Sigma, which is basically Zerocoin construction pasted on one out of n schemes - which I've described already - is already on our test net and it will go to main net very soon. And we plan to have Lelantus on testnet in early 2020 next year.

Thank you.

Is there anybody else have any questions? All right, let's give it up for, oh, we got one more from [inaudible].

Yeah, thank you so much for your talk, can you describe some of the privacy concerns in regards to a recipient of funds maybe needing to churn their funds before in order to help protect their privacy with Lelantus?

Maybe I can go back, oh, no is not possible already. So if I answer the question right, when the sender sent a coin to recipient, it generates a serial number and in order to spend the coin the serial number should be published on the blockchain. Which means that the sender can track this, can identify the serial number and you see can identify the spend of this coin. This is why it's advised the recipient to self spend the coin immediately after receiving it.

All right well let's give it up for Aram.

[applause]

Thank you

