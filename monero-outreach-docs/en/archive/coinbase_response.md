# A Response to Coinbase

**Conflicting views on PoW security. - 13th of November, 2019**

On November 8, 2019, Coinbase blogged an article authored by employee Mark Nesbitt covering its views on Proof of Work (PoW), [blog.coinbase.com/how-coinbase-views-proof-of-work-security-f4ba1a139da0](https://blog.coinbase.com/how-coinbase-views-proof-of-work-security-f4ba1a139da0). This article included a good description of PoW and made some cogent arguments for the benefits of using Application-Specific Integrated Circuits (ASICs) for PoW. But it also made a number of incorrect points and reached an arguably inappropriate conclusion. This response corrects the errors and argues in favor of the ASIC-resistance path taken by Monero’s developers. Corrections include pointing out that the article’s description of Monero’s efforts to prevent the use of ASICs is old and outdated, and include countering technical and philosophical arguments made regarding the benefits of ASICs.

### _Issues_

The Coinbase article presents a case study on Monero that focuses on a six-month hard fork cycle changing Monero’s PoW algorithm to stymie ASIC application. Its criticisms regarding the risk and downsides of the cycle were correct and insightful. However, the cycle is historical, not current, as it was changed last March. Its issues were addressed with the release of Monero software version v0.15.0.0, called Carbon Chamaeleon. With this release, starting near the end of November a new PoW algorithm called RandomX will begin to be used. By creating random programs, RandomX enables the Central Processing Units (CPUs) found in everyday computers to be competitive for PoW calculations. RandomX is anticipated to give many years of ASIC resistance without requiring hard forks, a future opposite the scenario of the case study.

“the goal was to use hardware that is already ubiquitous, so that getting access wasn’t an issue, as it’s been with Bitmain.”
Howard Chu

The core case made in the Coinbase article is that cryptocurrencies are better served by PoW algorithms that encourage ASIC use. It touches on the benefits of ASIC-resistance as to “make sure the network isn’t controlled by a small number of people,” but then it dismisses this as doing more harm than good. In fact, preventing adverse control of the network by hardware manufacturers is critical. Historically, control asserted by ASIC manufacturing has adversely affected cryptocurrencies. It contributed to Bitcoin infighting, for example. And control by a small number of people making hardware undermines Monero’s model of decentralization and invites significant risk. The benefits of maintaining independence from hardware manufacturers outweighs the costs of maintaining it—this is Monero’s PoW premise.

Beyond avoiding power consolidation, there are numerous other benefits of running on commodity CPUs. Commodity hardware, owned by almost everyone, gives small miners an opportunity to participate financially, and a reason to stay interested in and use Monero. CPU PoW enables novel applications for Monero, including making money from dormant and intermittent everyday computers. It gives access to Monero to those globally who find themselves banned from traditional exchanges. And it adds beneficial obscurity to the origin of new Monero, which with personal mining can be spent directly without passing through an exchange.

The opinion stated in the article that simple PoW algorithms will lead to commoditized ASICs made competitively and equitably ignores the reality of ASIC design and manufacturing, with its intrinsic complexity and economies of scale. Even for a hypothetical PoW algorithm having only one way to build it, a large manufacturer will still dominate small challengers through economies of scale. And not even the hashing algoirthm SHA-256 is that rudimentary—researchers are still publishing new optimization techniques for it, 18 years after its development. ASIC energy efficiency has grown exponentially over recent years. There is no simple, egalitarian model for ASIC PoW dominance.

The article asked sardonically if “the industry is going to be secured by hobbyists running old laptops in their homes.” This is misleading. Cryptocurrency mining, the process of executing a PoW algorithm to secure transactions, follows a power law with a smaller section of all miners possessing the majority of computational power. Professional mining farms will exist for all choices of PoW algorithm. ASIC resistance ensures hobbyists can still participate in mining, which only positively contributes to the strength and decentralization of the network.

As Howard Chu, Founder and CTO of Symas Corp. and Chief Architect of the OpenLDAP Project, notes regarding RandomX, “the goal was to use hardware that is already ubiquitous, so that getting access wasn’t an issue, as it’s been with Bitmain. General purpose CPUs, as found in desktops, laptops, and smartphones, are the most ubiquitous and easily accessible computing devices out there.“ Howard has been one of the most actively involved in the development and roll out of Monero’s new RandomX PoW algorithm.

Further, Monero is driven by grass-roots open-source development and ideology. This supports decentralization, distribution of funds, and innovation in privacy and security that would be hard to impossible to find in a project developed, say, by a large corporation or government. Distributed and egalitarian PoW mining contributes to this ethos.

### _Monero’s Dynamism_

It is still early for crypto, early for Monero. Any argument for technical change must consider the evolving nature of cryptocurrency, and the fact that decisions are not forever. Monero’s developers have formally discussed—public logs are available—possible paths forward for a future after RandomX. These include using SHA-3 (or similar), a hashing algorithm for PoW that can be run easily on ASICs. The choice to use RandomX over coming years capitalizes on this flexibility. The Monero community has a track record of incorporating new technology, observations, and developments, and can be expected to do the same going forward, taking full advantage of whatever is learned about ASICs and ASIC resistance.

RandomX was developed transparently on a public Github repository and subsequently audited by four independent audit teams, verifying its potential as a secure and innovative PoW algorithm. We will soon see its effectiveness at maintaining security and decentralization in the Monero network.

### _Summary_

Coinbase’s blog article gives a good overview of PoW and makes several valid points regarding the use of ASICs that are important to consider. Its presentation of Monero, though, is outdated, and some of its arguments and opinions are flawed. In an environment of new technology and uncertainty, the Monero community has taken a forward-looking approach to protect against control from hardware manufacturers. By using RandomX, Monero stands out as uniquely innovative and proactive, qualities that will carry it forward into its bright future.

### _Further Reading_

- Discussion of the future of the PoW algorithm
[github.com/monero-project/meta/issues/316](https://github.com/monero-project/meta/issues/316)
- Discussion of the future of the PoW algorithm #2
[github.com/monero-project/meta/issues/321](https://github.com/monero-project/meta/issues/321)
- dev meeting logs from 2019-03-24
[repo.getmonero.org/monero-project/monero-site/blob/b87354501b6343f9146f331805ddadc45696f728/_posts/2019-03-24-logs-for-the-dev-meeting-held-on-2019-03-24.md](https://repo.getmonero.org/monero-project/monero-site/blob/b87354501b6343f9146f331805ddadc45696f728/_posts/2019-03-24-logs-for-the-dev-meeting-held-on-2019-03-24.md)
- Monero and Arweave to Validate RandomX, a new Proof-of-Work Algorithm
[monerooutreach.org/stories/RandomX.php](https://www.monerooutreach.org/stories/RandomX.php)
