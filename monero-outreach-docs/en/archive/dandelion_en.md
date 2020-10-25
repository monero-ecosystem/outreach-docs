# Dandelion++ for Monero

**“Dandelion++ stops bad actors from linking your IP address to your Monero transactions.” - 2nd of March, 2020**

Monero stands on its Peer To Peer (P2P) communication network. The network’s blockchain-aware computers—called nodes—share the information that powers Monero, such as node addresses, historical blockchain data, blocks as they are mined, and new transactions to be added to blocks. The nodes are identified using Internet Protocol (IP) addresses, though, exposing risk that observers can connect IP addresses to transactions, deanonymizing the data they contain. Dandelion++ is a method for hiding this connection that is planned for an upcoming Monero software release. This article describes how Dandelion++ works and what it will do for users of Monero.  

### Monero’s P2P Network

Monero has two conceptual parts: 1) a P2P network and 2) applications that run on this network. Applications deal with addresses and keys and transactions, while the network organizes and ensures the flow of information. For understanding Dandelion++, it is important to consider both the P2P network’s structure and the way wallets use it to communicate transactions.  

Its structure comprises thousands of nodes across the globe—tens of thousands if passive nodes are included—each one connected over the Internet to usually only a small group of other nodes called peers [1]. Nodes communicate with their peers using the same Transmission Control Protocol (TCP) protocol used by Web browsers and Web servers. A node’s peers appear random and need not be close geographically. A common number of peers is eight, but some nodes have hundreds, with each node finding its peers by first asking special master nodes for their peers, then asking those for new peers, and so forth. The result is a network of many computers, each communicating through TCP with only a scattered, usually limited, collection of the others.  

A Monero wallet must communicate with one of these nodes as a gateway to the P2P network. Some wallets, like the official GUI wallet, can run their own node, while others, like MyMonero on a smart phone, always use a remote node. Wallets spend Monero by creating and broadcasting a transaction via its gateway node, with the goal that the transaction eventually find its way to a miner’s node for inclusion in a mined block. Each transaction holds information that is limited but contains some meaningful data, including a set of possible sources of spent funds.  

Right now, the Monero node starting the broadcast of a new transaction uses a process called flooding. It communicates the transaction to all its peers, who in turn communicate to all their peers, and so forth, with some checks to prevent redundant communication. The information travels in all directions over the network like a wave. Some cryptocurrencies, like Bitcoin, randomize the timing of this broadcast, but Monero does not.  

### The Problem

Your IP address can tell a lot about you. (For a sample of what is known about your IP address, you can visit an IP information site like [whatismyipaddress.com](https://whatismyipaddress.com/).) With information from your Internet Service Provider (ISP) or Virtual Private Network (VPN) provider, as the case may be, it might identify you by name. Any connection between your IP address and the transactions you create leaks information—even the mere act of making Monero transactions is probably not something you want strangers to know. The problem is that the flooding of transactions over the Monero P2P network lets others make just this transaction-to-IP-address connection [2].  

Connecting an IP address to a transaction isn’t easy or flawless. It takes many observers and lots of work. But using a botnet, for example, connected to the Monero P2P network allows calculation of a likely transaction origin through analysis of timing and comparison with information known about peers. When there is a loud noise, you know which way to look because your brain extracts the direction from the timing and distortion of the sound in each ear. Analysis on flooded cryptocurrency packets received at different locations lets a spying adversary do the same. Transaction creation is like a loud noise for botnet nodes that are like ears.  

### Dandelion

To address this problem, esteemed researchers at the University of Illinois first developed a set of techniques they called Dandelion [2]. The initial focus was on Bitcoin, but it applies to Monero as well. The idea with Dandelion is to first route transactions to a remote node in a special undetectable way before initiating the flooding.  

The Dandelion authors delved into the theory and practice of using botnets to find sources of cryptocurrency transactions. This included the creation of mathematical models for anonymity (please see [2] for detailed information) that were used to analyze three propagation techniques: 1) basic flooding (Monero’s method), 2) randomized flooding called diffusion (Bitcoin’s method), and 3) diffusion by proxy. The last technique first forwards a transaction to a random node, which then broadcasts it using diffusion. All three techniques were found to be inadequate using the authors’ mathematical models.  

To address this inadequacy, the authors proposed Dandelion. Dandelion defines a process for finding a proxy node to broadcast, called the anonymity (or stem) phase. And it establishes another process for broadcast, called the spreading (or fluff) phase. In general, the two phases use different sets of peer connections with the important difference that the anonymity phase connection set changes with time. The descriptive name Dandelion comes from the process of first seeking out a proxy node along a special linear search path, then from this proxy node spreading the information rapidly and symmetrically—the shape of information flow resembles a dandelion.  

Dandelion, analyzed using the authors’ mathematical models, when used by all nodes proves to resist spying by a team of nodes that are passive observers. With Dandelion, a botnet participating honestly in the P2P network cannot reliably link transactions with IP addresses.  

### Dandelion++

However, an adversary seeking to link transactions with IP addresses may not be passive, and may not follow the rules of the network. Some honest nodes may not run Dandelion. Motivated by the growing market for wide-area cryptocurrency analysis, such as by Chainalysis [4], the authors revisited the assumptions from their earlier work and, with collaborators, a year later developed Dandelion++ [3]. Dandelion++ tweaks Dandelion to resist large-scale rule-breaking deanonymization attacks.  

The creators of Dandelion++ modeled an adversary as a botnet with spy nodes distributed throughout the network, forming some significant fraction of the overall network. In their model, these nodes need not follow the rules. They can generate any number of outbound connections to any honest or adversarial nodes. They use all available information, including timing and the addresses of senders. It is in this very hostile environment that Dandelion++ succeeds in protecting anonymity.  

Dandelion++, like Dandelion, has a stem and fluff phase. In the new stem phase, to implement dynamic connectivity, it proceeds in discreet intervals, called epochs. Each node switches epoch independently, typically every few minutes. With each new epoch, a node picks two new relay connections at random from its outbound connections. Then whenever the node creates its own transaction it sends it over one of these two relays, always making the same choice for a given epoch. And whenever it gets a transaction from another node for forwarding during stem phase, if it is a relayer (more on this below), it sends it out randomly over one of the two relays.  

The fluff phase in Dandelion++ uses diffusion, the flooding process where the timing of the communications are random to make it harder for spy nodes to locate the source. Once a transaction has started the diffusion process it continues to propagate using diffusion, never going back to the stem phase. Diffusion starts, though, in special way with Dandelion++. For each epoch, a node classifies itself as either a relayer or a diffuser. The mode is determined at random at the start of the epoch. If a node is a diffuser, whenever it is given a transaction to relay as stem phase, it instead broadcasts it using diffusion, thereby starting the fluff phase.  

There is an additional, complementary piece to Dandelion++ called the fail-safe mechanism. Each node that relays a transaction during stem phase starts a timer for that transaction. If a time threshold passes without the node receiving the same transaction back during a fluff phase, it starts its own fluff phase. This serves two purposes: It frustrates attempts at deanonymization using timing, and it defeats so-called black-hole attacks where adversarial nodes discard transactions during the stem phase rather than relaying them.  

With these techniques in place, Dandelion++ gives formal guarantees of resistance to deanonymization. It achieves this using local techniques, unlike the Tor network, which requires global reasoning. Each elegant Dandelion++ node makes its own decisions about its behavior. The result is a fast and efficient, yet effective, technique for preventing even sophisticated adversaries from connecting IP addresses to transactions.  

### Integration with Monero

Though Dandelion++ was explicitly developed for Bitcoin, it was recently applied to Monero by developer Lee Clagett (vtnerd), with testing and review by developer moneromooo. Discussions and file changes made by these preeminent Monero developers can be seen as part of the source control pull request [5]. A pull request is part of the formal process by which new code enters the Monero code base. Though the Dandelion++ pull request was approved by moneromooo, at the time of this writing it has not yet completed all review and has not been merged into the Monero codebase.  

When released, Dandelion++ will be used by default, though it will be possible to turn it off by defining the probability of entering fluff mode probability to 100% in the C++ code file cryptonote_config.h and recompiling. Importantly, even in this case of targeted recompilation, the new release will use diffusion, with its random delays, rather than basic flooding. The date for its formal release is not set. The addition of Dandelion++ does not require a hard fork.  

There are some minor downsides and limitations. Dandelion++ adds delay to the propagation of transactions. This comes from multiple sources, which are discussed by the Dandelion++ authors [3]. First, the existence of the stem phase adds delay, possibly a few seconds, based on the authors’ analysis and experimental evaluations. Diffusion adds random delays during the fluff phase, typically less than a second. And should the network be subject to a black-hole attack, the confirming wait by the initiator could delay transmission by minutes. These delays are not expected to materially affect the network. Also, Dandelion++ does not encrypt the P2P packets, and does not protect against ISP/VPN-level spying—for this, you can use Tor.

[1] Exploring the Monero Peer-to-Peer Network, T. Cao, J. Yu, J. Decouchant, X Luo, and P. Verissimo, [eprint.iacr.org/2019/411.pdf](https://eprint.iacr.org/2019/411.pdf).  
[2] Dandelion: Redesigning the Bitcoin Network for Anonymity, S.B. Venkatakrishan, G. Fanti, and P. Viswanath, SIGMETRICS ’17, June 5-9, 2017, Urbana-Champaign, [publish.illinois.edu/science-of-security-lablet/files/2016/07/Dandelion-Redesigning-BitCoin-Networking-for-Anonymity.pdf](http://publish.illinois.edu/science-of-security-lablet/files/2016/07/Dandelion-Redesigning-BitCoin-Networking-for-Anonymity.pdf)  
[3] Dandelion++: Lightweight Cryptocurrency Networking with Formal Anonymity Guarantees, G. Fanti, S.B. Venkatakrishnan, S. Bakshi, B. Denby, S. Bhargava, A. Miller, and P. Viswanath, arXiv:1805.11060v1, May 28, 2018, [arxiv.org/pdf/1805.11060.pdf](https://arxiv.org/pdf/1805.11060.pdf)  
[4] Chainalysis, [chainalysis.com](https://www.chainalysis.com/).  
[5] Adding Dandelion++ support to public networks: #6314, [github.com/monero-project/monero/pull/6314](https://github.com/monero-project/monero/pull/6314).  

### Summary

A powerful deanonymization-prevention method is coming to Monero, Dandelion++. This method, developed originally for Bitcoin, and applied to Monero by developer Lee Clagett, prevents adversaries from connecting IP addresses to Monero transactions even in large-scale sophisticated attacks. It focuses particularly on resistance to botnets. Dandelion++ uses stem and fluff phases that make the flow of information take the shape of a dandelion, hence the name. Through this, it makes it hard for observers to locate the source of a transaction. This beautiful new feature will enhance Monero’s already excellent privacy features and carry Monero forward on its path of continual improvement.  

### Learn More

- Lee Clagett at Monero Konferenco: [Dandelion Onions: Protecting Transaction Privacy in Monero](https://www.monerooutreach.org/monero-konferenco/lee-clagett.html)
