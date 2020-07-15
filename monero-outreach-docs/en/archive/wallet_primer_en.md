# Monero Paper Wallet Primer

**_“All you need to store Monero are primitive tools. A pencil and paper will do, but you can also carve it in stone or mold it in clay, paleolithic style. How is this possible?”_**
_13th of July, 2020_
---

It turns out a software wallet, the common way of storing Monero (XMR), does not actually hold your Monero in the conventional sense of the word wallet. Instead, Monero exists as records on a public ledger, the Monero blockchain, and your wallet holds a special password called the private spend key that allows changing those records. This article will give you background and guidance in how to use a physical copy of a private spend key—called a paper wallet—to store Monero.

### _Technical Background_

It is important to have a mental model of how a Monero paper wallet works to feel confident and use it securely. The private spend key mentioned above, in hex form (using 0-9 and a-f), looks something like this:

_Private Spend Key:_
**09f8225e9f6dd95457a0bca31b66a599 6e6da8be8195025817c36bf490ae0903**

Representing roughly 256 arbitrary bits of information, it has many characters and is so complicated that no one can guess it. You can just write it down and hide it, and then you own the Monero it controls.

Because the raw private spend key is unwieldy and prone to mistakes, mappings have been created to groups of regular words, called mnemonic phrases, that are friendlier. The two most important mappings for Monero are the following:

**Mapping 1 (25 Words):** The official Monero wallet’s built-in mapping uses 25 ordered words chosen from a set of 1626 words. It includes internal constraints so that a random selection of 25 words is usually not valid. This lets software detect errors. The English wordlist can be seen here: [github.com/monero-project/monero/blob/master/src/mnemonics/english.h](https://github.com/monero-project/monero/blob/master/src/mnemonics/english.h). This mapping’s mnemonic phrase for the private spend key shown above is the following: _{moon pram oust mime boil boat nutshell moisture ionic enjoy below ungainly loaded rage etched atom reduce almost glass vexed jaded coils pioneer pyramid nutshell}._

**Mapping 2 (24 Words):** The standard Bitcoin Improvement Proposal 39 (BIP39) mapping is a general-purpose mapping used, for example, by the Ledger hardware wallet. It is composed of 24 ordered words, chosen from a set of 2048. Like Mapping 1, it has internal constraints so that most combinations of words are invalid. The English wordlist can be seen here: [github.com/bitcoin/bips/blob/master/bip-0039/english.txt](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt). An example mnemonic phrase of this type is the following: _{open birth pepper electric nuclear shine stable ritual napkin quarter aunt demand thing cable tuna lucky vehicle taste tourist grape buffalo fitness indoor draft}._

Both of these mappings are standards and widely used. If you save your private spend key using one of them you will be able to calculate the raw form from it and access your XMR 10, 20, or 30 years from now.

The three representations—1) Monero 25-word mapping, 2) BIP39 24-word mapping, and 3) raw form—encode a 32-byte random number that has the sole constraint that it must be below a certain maximum. With this constraint, the private spend key in raw hex form looks random except for the second-to-last digit, which is almost always 0, as in the example shown at the start of this section. (It can be engineered to be a 1, but you will probably never see this at random.) Software can create a private spend key by generating a number with 32 random bytes and taking the remainder after dividing it by the maximum allowed value. The randomness used to make it must be high quality and not predicable because predicting it would enable calculating the private spend key and stealing the Monero it controls.

In modern Monero software, the private spend key is used to create two other important keys: a private view key and a public key (or address). The private view key allows observation of incoming XMR that is sent to the account using the public key. Private view keys are nowadays made from private spend keys using fixed formulas. (Early in Monero’s history, some private view keys were created independently of the paired private spend key. Those of you with these kind of keys probably know who you are.) A private view key corresponding to the example private spend key given earlier, in hex form, looks like this:

_Private View Key:_
**c072ce1678325c1fc09f06ed3f72bdc 290b675747cc01d5255773a63604e8a01**

As with the private spend key, the second-to-last hex digit of the private view key is almost always 0, and very rarely 1.

The public key (also called the address) is longer, and usually shown as a string (rather than in hex). Here is the public key corresponding to the private spend key given earlier:

_Public Key (Address):_
**44XiEedj1ivSCY6A1dFCDCCxZ3nxUQyD aGauuvgYNCAjbKSPzCe3RQ3goiXVvmfX axdYecaBQVNHPGszK9Jmp7Lg3SPAMr1**

(Don’t send Monero to this address! Anyone who knows the private spend key—i.e., anyone who reads this article—can take it.)

The public key is a 95-character string starting with the number 4. It is composed of 58 types of characters that are chosen to be visually clear (you won’t be puzzled by the digit 0 or the capital letter O, for example). It has internal constraints dictating that random characters or errors do not usually form valid addresses.

The process by which these three keys are made with software is shown in the following diagram:

	                   Mnemonic Phrase
			        ↑↓
       Random Data ----> Private Spend Key ----> Private View Key
                                      |
                                      |
				          |    ----> Public Key (Address)

A cryptographic process makes the red arrows in the above diagram irreversible. Knowing the public key and the private view key does not allow calculation of the private spend key.

### _Generating Monero Keys_

You can create keys based on the above process using 1) software wallets, 2) special-purpose websites, or 3) hardware wallets.

**Key Generation Method 1:** Almost any software wallet can be used to generate keys, but you have to trust the software’s competence and honesty. It is safest to use the official Monero wallet or a wallet recommended on the official Monero website, [web.getmonero.org](https://web.getmonero.org/). Monero Outreach has recommendations matching those on the official website in our [Monero Wallet Quickstart](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html).

Steps for using the official wallet to generate keys are the following: The official Monero wallet can be downloaded at [getmonero.org/downloads](https://web.getmonero.org/downloads/). After running the GUI, you can navigate to “Create a new wallet” and get a 25-word mnemonic phrase representing the private spend key using Mapping 1 discussed above. By navigating inside the GUI, you can also get the raw private spend key, private view key, and the public key.

**Key Generation Method 2:** A special-purpose website exists just for generating keys, primarily for paper wallets: [moneroaddress.org](https://moneroaddress.org/). This site, created by esteemed Monero developer moneromoo and widely considered safe by the community, lets you enter custom random text to generate the private spend key—a comforting feature if you like having control over the random input. Steps for using this method are given below.

Go to the website moneroaddress.org in a browser, load the page, then turn off your Internet connection to generate keys. Enter text that is very random (more than 50 unpredictable characters, say) or leave the line blank to use computer-generated randomness, and click GENERATE WALLET. This will give you a private spend key, private view key, and public key (called public address on this website). Alternatively, for increased security, the software for the website can be downloaded as an HTML file and run on a computer offline, or the source can be downloaded from Github github.com/moneromooo-monero/monero-wallet-generator/.

For hardware-wallet-generation, you can use a Ledger or a Trezor. The steps for wallet generation with Ledger are given below.

Download Ledger Live from [shop.ledger.com/ledger-live](https://www.ledger.com/ledger-live/). Then from within Ledger Live, download the app for Monero onto your Ledger, and use it to create a wallet based on your 24-word Ledger mnemonic, based on Mapping 2, using the official Monero wallet. The official Monero wallet has a Ledger option that supports this process. This key generation method has the disadvantage of the private view key being hard to extract, but this disadvantage is moderated by the ability to use the Ledger itself to view incoming transactions.

### _Wallet Generation Safety_

Care must be taken when creating your keys with the above methods. Private cryptocurrency is uniquely stealable, as it is broadly spendable, incorporeal, untraceable, and does not require physical presence to move. Be careful, or someone will take your Monero. Reason must be applied, though. Consider that if you have a little spending cash, you carry it in a billfold, while large business earnings are carried in an armored car. You should view the required security of your Monero paper wallet in the same way, and put effort into security commensurate with your holdings.

For billfold-level security, you can use your smart phone or regular computer. There is debate on which is more secure, but for billfold-level holdings, it is probably OK to use either while taking basic precautions. If you are using a smart phone, don’t use one that is jailbroken. If you are using a computer, run antivirus software and disconnect the computer from the Internet when generating wallets. Don’t use any device of which you are suspicious. With these steps you can apply the techniques from the last section to generate your billfold-level security paper wallet.

For armored-car-level security, you should use a computer that will not ever again be connected to the Internet, and you should wipe its memory after generation of keys (so that someone who gains physical access to your computer cannot re-create them). Almost everybody has an old computer. You can use that, or you can buy a new low-end laptop for a few hundred dollars. If you print your wallet keys for storage, you should use a printer without built-in memory (such as an HP Deskjet 1100). You should check the hash of software loaded onto the wallet computer (taken to it by CD or pen drive, since—again—there is no direct Internet connection). You can see examples of these hashes, for the official Monero wallet, at [getmonero.org/downloads](https://web.getmonero.org/downloads/). When software is signed, you should check the signature.

### _Creating Your Wallet_

With the techniques and precautions from the previous sections, you are now ready with safely generated keys, and all that is left is to store them on a physical wallet. The most common approach is to print the private spend key (in one if its three forms) onto paper. That’s a paper wallet. Save the private view key and public key digitally, anywhere. Then you can hide the paper wallet and send Monero to it at your leisure using the shareable public key. And you can check to make sure funds arrive using the private view key.

You can use non-paper methods, too. The name paper wallet comes from most being on paper, but for this article, the paper wallet definition is extended to include other physical mechanisms of recording. Tools are commercially available to make metal paper wallets compatible with Monero. Some of these slide symbols into place, some engrave them, and some stamp them. Many work with a standard, like BIP39 (Mapping 2, above). To find examples, search on Amazon for “cryptocurrency, steel, wallet” (though some are actually made of copper). A benefit of a metal paper wallet is that it is not as sensitive as paper to water damage and fire—this helps protect the wallet from getting lost, and is probably more relevant to the armored-car-level security discussed above.

You can feel free to be creative in picking a material. The world is transcendently complex, and you can hide in that complexity by choosing a unique method. Thieves would have a hard time figuring out that you wrote your private spend key internally to a table you made as a carpenter, for example, or if the key was notched into barbed wire if you work as a cowboy. Your mnemonic words could be handwritten spread out over pages of a book, if you have a library at home. Find a technique special to you.

### _Secure Your Wallet_

After you have created the wallet, you have to put it where your keys won’t be stolen. How much effort goes into hiding goes back to billfold versus armored-car security considerations. More value merits less accessibility. For billfold-level amounts, you can just put it in an out-of-the-way drawer. For more security, you will want to hide it with effort, perhaps inside your home. You may want to bury it. Or you might want to put it in a bank safe deposit box. Many YouTube videos guide on hiding things inside your home. Watch these, then do something different. Your home and the world are complex—embrace that to hide your wallet.

### _Avoiding Loss_

Also take care to avoid loss. You might forget where you hid your wallet. You may accidentally throw the wallet away. Natural disaster could take it from you. Your death might take it from your family. And if you take steps to protect from loss, how do you keep those steps from making theft more likely? A common approach is to trust one or more people, but with checks on that trust. It is possible to split the private spend key among multiple people. Cryptographic techniques exist to make sure M out of N (where M and N can take any values where M<=N) people have to agree to re-create your private spend key. Simple techniques can also often work. If you have a 24-word phrase, you could give 12 words each to two people (12 words is itself quite secure). Or it might be that you give only enough information to recover your key with a lot of work. You could tell someone, for example, “my Monero paper wallet is buried somewhere in the garden, and it will be worth your trouble to find it if I die.”

Redundancy helps prevent lost keys. If you have two copies and hide them far apart, localized problems like natural disasters will be overcome.

### _Summary_

This article touched on the art and science of using Monero paper wallets. You will need software to generate your keys. Wallet software, moneroaddress.org, or a hardware wallet will do this. If you are in a rush with small amounts, use moneroaddress.org, and if you have more funds and want more protection, use the official Monero wallet on an offline computer that never again goes online. Your paper wallet needs to hold at least the private spend key, either in its raw form or one of its mnemonic forms. You should store this key on a physical medium and hide it in a creative way. You should take care to not lose your paper wallet by having redundant copies and working out a way to trust other people, with limits on that trust, either through clues or using M-of-N responsibility. Using your view key, which you can store and share without risk of losing Monero, you will be able to monitor incoming transactions sent to your paper wallet using the shareable public key, all while the private spend key stays hidden.

### _Learn More_

- [Monero Wallet Quickstart](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html) - A look at wallet types and how to choose what is right for your needs.
- [A Secure Wallet is a Happy Wallet](https://www.monerooutreach.org/monero_best_practices/a-secure-wallet-is-a-happy-wallet.html) - Best practices for your Monero wallet.