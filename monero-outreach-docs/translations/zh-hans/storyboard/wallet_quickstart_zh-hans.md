# Monero Wallet Quickstart
# 门罗币钱包快速入门

*04/22/19*  
*2019年4月22日*  

Almutasim  

_**Wallets involve one of the most important security decisions that users make.**_  
_**钱包对于用户决策的安全性事关重大。**_  

A Monero software wallet is a program for storing, sending, and receiving Monero. It gives you full control over your Monero with privacy and no middleman. Nobody can know all the details on or change your transactions—unless you choose to share your view keys for auditing—power that is the essence of the Monero experience.

门罗币钱包软件是一个用于存储、发送和接收门罗币的程序。它让您可以完全控制您的门罗币，保证匿名性的同时没有任何中介参与。没有人能够知道或者更改您的交易及其所有细节—除非您公开了查阅私钥—这种保护隐私的力量就是门罗币的本质所在。

To experience this power, you will need to pick a wallet. The first critical aspect of any wallet is its trustworthiness. Only wallets recommended by the community (and the [getmonero.org](https://getmonero.org/) website) are mentioned in this article. Next, you will want to pick a wallet that runs on your preferred computing device—iPhone, Android Phone, or Laptop/Desktop computer. Finally, you should pick a wallet that matches your privacy needs. This article will guide you on this.

要体验这种力量，你需要选择一个钱包。选择任何钱包都要关注其可信度。本文只提及社区以及[getmonero.org/zh-cn](https://www.getmonero.org/zh-cn/)网站推荐的钱包。接下来，您需要选择一个能够在您的苹果手机、安卓手机或者笔记本电脑、台式机上运行的钱包。最后，你应该选择一个符合你隐私需求的钱包。本文将为您提供相关的指导。

Some wallets operate using their own copy of the Monero blockchain. This is also called running a full node. It gives you control over the timeliness of your transactions. Though you can rely on a remote node without added risk of losing your Monero, you do depend on the remote node’s availability—you can always receive, but you may not be able to send. Another benefit of running your own full node is pride of contribution to the Monero network. Honest full nodes make Monero stronger. Learn more here: [monero.how/how-to-run-monero-node](https://www.monero.how/how-to-run-monero-node).

一些钱包使用他们自己的门罗币区块链备份。这也称为运行完整节点。它使您能够知晓交易的时效性。虽然您可以依赖远程节点，且不会增加丢失门罗币的风险，但是您需要依赖于远程节点的可用性—您仍然可以收款，但是可能因为没有可用的远程节点而导致无法支付。运行您自己的完整节点的另一个好处是为门罗币网络做贡献。诚实完整的节点使门罗币更强大。更多信息参见[monero.how/how-run-monero -node](https://www.monero.how/how-run-monero -node)。

Benefits of relying, instead, on remote nodes—using what are called light, or sometimes lightweight, wallets—include not needing storage resources for the Monero blockchain. The (unpruned) blockchain is larger than 50 GB and growing. Many wallets that use remote full nodes also use less processing power and network bandwidth. If these resources are limited on your computing device, a light wallet may be preferred. This will almost always be the case for a wallet running on a smartphone.

然而，依赖远程节点的好处就是不需要为门罗币区块链存储数据，而是使用所谓的轻钱包，有时候也称为轻量钱包。全部的区块链数据大于50G，并且这个数字还在增长。使用远程节点运行的钱包会占用更少的电脑资源和带宽。如果您的设备存储空间不足，轻钱包是您的首选。手机钱包几乎都是轻钱包。

Light wallets come in two types: view-key-protecting and view-key-sharing. View-key-protecting light wallets keep your view key completely private, and as a consequence have to download the blockchain, or at least the portion of it later than the wallet’s creation date, to calculate the Monero balance in the wallet. View-key-sharing light wallets, on the other hand, share the view key with the server running the remote node to calculate the wallet’s incoming balance on the server. These efficient wallets are sometimes called wallet apps. Their sharing of the view key reduces privacy if the server running the view-key-aware remote node is not trusted because it allows observation of incoming transactions. Note, however, that sometimes wallet holders share the view key for auditing anyway—it does not allow transferring Monero.

需要注意的是门罗币有两种密钥：一种是查阅密钥，用于查看转账过程，但查阅密钥不能用于交易及提币；另一种是支付密钥，拥有了支付密钥您就拥有了这一笔门罗币，您可以对这笔门罗币进行提币及交易。

轻钱包也有两种类型:查阅密钥保护型和查阅密钥分享型。查阅密钥保护型轻钱包会保持您的查阅密钥完全私有，因此必须下载区块链，或至少下载在钱包创建日期之后的部分，以计算钱包中的门罗币的余额。另一方面，查阅密钥分享型轻钱包与运行远程节点的服务器共享查阅密钥，以计算服务器上钱包的结算情况。这些高效钱包有时被称为钱包应用程序。如果由于允许查阅交易的过程，而导致运行拥有查阅密钥的远程节点的服务器不受信任，那么查阅密钥的分享就会导致隐私性的降低。不过，请注意，有时钱包持有人共享用于审计的查阅密钥——它不允许进行门罗币转账。

For maximum security—security even if your primary device is compromised by malware—specialized hardware wallets can be used. Hardware wallets are small interactive electronic devices that store your private keys and communicate with software on the primary device using only public information. Hardware wallets give extra security for a typical price of $50-150.

最大限度地保证安全性---即便您的设备受到恶意软件的攻击，专业的硬件钱包也是安全的。硬件钱包是一种小型的交互式电子设备，它存储您的私钥，并仅使用公开的信息与主设备上的软件通信。硬件钱包提供更安全的保障，一般的价格约为50-150美元。

So, with all this in mind, consider the following options: If you want to run your own full node, a good choice is the official Monero GUI or CLI wallet. The former provides a graphical user interface, and the latter a textual interface. Both can be configured to either run a full node or connect to a remote node in a privacy enhanced way. These can be downloaded from [getmonero.org/downloads](https://getmonero.org/downloads/). For Android devices, Monerujo, at [monerujo.io](https://www.monerujo.io/), or for iOS, Cake Wallet, at [cakewallet.io](https://cakewallet.io/), are recommended view-key-protecting light wallets. If you would like an view-key-sharing light wallet, browser-based MyMonero, at [mymonero.com](https://mymonero.com/), is recommended. The Edge Wallet, at [edge.app](https://edge.app/), is another solid view-key-sharing light-wallet option for both Android and iOS.

综上所述，您可以考虑以下选项:

如果您想运行自己的完整节点，最好选择门罗币官方GUI钱包或者CLI钱包。前者提供图形化界面，后者提供文本界面。两者都可以设置为运行完整的节点或以增强隐私的方式连接到远程节点。这些都可以从这里下载[getmonero.org/zh-cn/downloads](https://www.getmonero.org/zh-cn/downloads/)。对于安卓设备，推荐使用Monerujo，网址是[monerujo.io](https://www.monerujo.io/)对于苹果系统，推荐使用Cake Wallet，网址是[cakewallet.io](https://cakewallet.io/)。如果您想要一个查阅私钥共享型轻钱包，推荐使用基于浏览器的MyMonero，网址是[mymonero.com](https://mymonero.com/)。Edge钱包，网址是[edge.app](https://edge.app/)，是另一个可供选择的针对安卓系统和苹果系统的可靠的查阅私钥共享型轻钱包。

When choosing among these, keep in mind that most have an extra feature in that—the exception being the Edge Wallet—they can be configured to connect to either a third-party remote server or a server you run with a node. This is illustrated in the table.

在选择这些钱包时，请记住，他们大多数都有一个额外的特性(Edge 钱包除外)他们都可以设置为连接到第三方远程服务器或者连接到一个您运行节点的服务器。如表所示。

## Official Wallets
## 官方钱包

+ [getmonero.org/downloads](https://www.getmonero.org/downloads)  
If you want to run a full node, a good choice is the official Monero GUI or CLI wallet. The former provides a graphical user interface, and the latter a textual interface.

+ [getmonero.org/zh-cn/downloads](https://www.getmonero.org/zh-cn/downloads/)  
如果您想运行一个完整的节点，建议选择门罗币官方的GUI钱包或者CLI钱包。前者提供图形化界面，后者提供文本界面。


## Mobile Wallets
## 手机钱包

+ [cakewallet.io](https://cakewallet.io/)  
Cake Wallet, a view-key-protecting light wallet, is available for iOS devices.  
Cake钱包是一款用于苹果设备的查阅私钥保护型的轻钱包。  


+ [monerujo.io](https://www.monerujo.io/)  
Monerujo, a view-key-protecting light wallet, is available for Android devices.  
Monerujo, 是一款用于安卓设备的查阅私钥保护型轻钱包。  


+ [edge.app](https://edge.app/)  
Edge Wallet is available for both Android and iOS. It is a view-key-sharing light wallet.  
Edge钱包同时适用于安卓和苹果系统。是一个查阅私钥共享型轻钱包。  


## Web Wallets *(Optimized for Convenience)*
## Web钱包 (为便利性而优化)

+ [mymonero.com](https://mymonero.com/)  
MyMonero is a light, browser-based wallet. It is also available as an iOS app and a desktop app.  
MyMonero 是一个轻量级的基于浏览器的钱包。它还可以作为iOS应用程序和桌面应用程序使用。  

## Hardware Wallets *(Optimized for Security)*
## 硬件钱包 （为安全性而优化）

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)  
Ledger is a highly secure device that stores your mnemonic seed.  
Ledger 是一个用于存储您的助记词的高度安全的设备。

Not Applicable
不可用  

+ [trezor.io](https://trezor.io/)  
Trezor is an alternative highly secure device that stores your mnemonic seed.  
Trezor 是一个用于存储您的助记词的高度安全的设备。  

For a hardware wallet that provides extra security in storing and transmitting Monero even if the primary device becomes compromised, both Ledger, [ledger.com](https://shop.ledger.com/?r=92d74dc2847a), and Trezor, [trezor.io](https://trezor.io/), are well regarded. (Note that Ledger works with wallets now, while wallet support for Trezor is in progress.)

如果您需要一个即使主要设备受到破坏，在存储和传输门罗币时也能提供额外安全性的硬件钱包，推荐使用Ledger([ledger.com](https://shop.ledger.com/?r=92d74dc2847a)和Trezor 钱包([trezor.io](https://trezor.io/)。(请注意，Ledger现在与钱包已良好兼容，而Trezor的钱包支持尚需完善。)

Letting your resource and privacy preferences drive your wallet choice will maximize your Monero experience. Monero’s wealth of wallet options—from a quick MyMonero app to an authoritative full-node Monero CLI wallet combined with a Ledger or Trezor—let Monero meet its users’ diverse needs.

根据您的自身情况和隐私偏好来选择钱包，将优化您的门罗币使用体验。门罗币丰富的钱包选项——从快速的MyMonero应用程序到权威的全节点门罗币 CLI钱包，再加上Ledger或者trezor——门罗币可以满足用户的多样化需求。

To explore further:  
更多信息  

[medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
