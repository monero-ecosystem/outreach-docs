# Monero Wallet Quickstart
*04/22/19*  
Almutasim  
_**Wallets involve one of the most important security decisions that users make.**_


A Monero software wallet is a program for storing, sending, and receiving Monero. It gives you full control over your Monero with privacy and no middleman. Nobody can know all the details on or change your transactions—unless you choose to share your view keys for auditing—power that is the essence of the Monero experience.

To experience this power, you will need to pick a wallet. The first critical aspect of any wallet is its trustworthiness. Only wallets recommended by the community (and the [getmonero.org](https://getmonero.org/) website) are mentioned in this article. Next, you will want to pick a wallet that runs on your preferred computing device—iPhone, Android Phone, or Laptop/Desktop computer. Finally, you should pick a wallet that matches your privacy needs. This article will guide you on this.

Some wallets operate using their own copy of the Monero blockchain. This is also called running a full node. It gives you control over the timeliness of your transactions. Though you can rely on a remote node without added risk of losing your Monero, you do depend on the remote node’s availability—you can always receive, but you may not be able to send. Another benefit of running your own full node is pride of contribution to the Monero network. Honest full nodes make Monero stronger. Learn more here: [monero.how/how-to-run-monero-node](https://www.monero.how/how-to-run-monero-node).

Benefits of relying, instead, on remote nodes—using what are called light, or sometimes lightweight, wallets—include not needing storage resources for the Monero blockchain. The (unpruned) blockchain is larger than 50 GB and growing. Many wallets that use remote full nodes also use less processing power and network bandwidth. If these resources are limited on your computing device, a light wallet may be preferred. This will almost always be the case for a wallet running on a smartphone.

Light wallets come in two types: view-key-protecting and view-key-sharing. View-key-protecting light wallets keep your view key completely private, and as a consequence have to download the blockchain, or at least the portion of it later than the wallet’s creation date, to calculate the Monero balance in the wallet. View-key-sharing light wallets, on the other hand, share the view key with the server running the remote node to calculate the wallet’s incoming balance on the server. These efficient wallets are sometimes called wallet apps. Their sharing of the view key reduces privacy if the server running the view-key-aware remote node is not trusted because it allows observation of incoming transactions. Note, however, that sometimes wallet holders share the view key for auditing anyway—it does not allow transferring Monero.

For maximum security—security even if your primary device is compromised by malware—specialized hardware wallets can be used. Hardware wallets are small interactive electronic devices that store your private keys and communicate with software on the primary device using only public information. Hardware wallets give extra security for a typical price of $50-150.

So, with all this in mind, consider the following options: If you want to run your own full node, a good choice is the official Monero GUI or CLI wallet. The former provides a graphical user interface, and the latter a textual interface. Both can be configured to either run a full node or connect to a remote node in a privacy enhanced way. These can be downloaded from [getmonero.org/downloads](https://getmonero.org/downloads/). For Android devices, Monerujo, at [monerujo.io](https://www.monerujo.io/), or for iOS, Cake Wallet, at [cakewallet.io](https://cakewallet.io/), are recommended view-key-protecting light wallets. If you would like an view-key-sharing light wallet, browser-based MyMonero, at [mymonero.com](https://mymonero.com/), is recommended. The Edge Wallet, at [edge.app](https://edge.app/), is another solid view-key-sharing light-wallet option for both Android and iOS.

When choosing among these, keep in mind that most have an extra feature in that—the exception being the Edge Wallet—they can be configured to connect to either a third-party remote server or a server you run with a node. This is illustrated in the table.

## Official Wallets

+ [getmonero.org/downloads](https://www.getmonero.org/downloads)
If you want to run a full node, a good choice is the official Monero GUI or CLI wallet. The former provides a graphical user interface, and the latter a textual interface.

## Mobile Wallets

+ [cakewallet.io](https://cakewallet.io/)  
Cake Wallet, a view-key-protecting light wallet, is available for iOS devices.

+ [monerujo.io](https://www.monerujo.io/)  
Monerujo, a view-key-protecting light wallet, is available for Android devices.

+ [edge.app](https://edge.app/)  
Edge Wallet is available for both Android and iOS. It is a view-key-sharing light wallet.

## Web Wallets *(Optimized for Convenience)*

+ [mymonero.com](https://mymonero.com/)  
MyMonero is a light, browser-based wallet. It is also available as an iOS app and a desktop app.

## Hardware Wallets *(Optimized for Security)*

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)  
Ledger is a highly secure device that stores your mnemonic seed.

+ [trezor.io](https://trezor.io/)  
Trezor is an alternative highly secure device that stores your mnemonic seed.

For a hardware wallet that provides extra security in storing and transmitting Monero even if the primary device becomes compromised, both Ledger, [ledger.com](https://shop.ledger.com/?r=92d74dc2847a), and Trezor, [trezor.io](https://trezor.io/), are well regarded. (Note that Ledger works with wallets now, while wallet support for Trezor is in progress.)

Letting your resource and privacy preferences drive your wallet choice will maximize your Monero experience. Monero’s wealth of wallet options—from a quick MyMonero app to an authoritative full-node Monero CLI wallet combined with a Ledger or Trezor—let Monero meet its users’ diverse needs.

To explore further: [medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
