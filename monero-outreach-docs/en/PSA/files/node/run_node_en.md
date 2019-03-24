# Transact Safely, Run a Full Node

**How to run your own full node?**

You can run a full node by using the official Monero CLI and GUI software. The monerod daemon associated with this software is required for running a full node.

The full node run by the Monero CLI wallet is done by the daemon in charge of downloading the blockchain and storing it on your computer. The daemon is the console program that handles the blockchain separately from the account managed by the CLI wallet.

Monerod also runs separately alongside the GUI wallet. However, if specified the daemon can run automatically and the user experience works as if it’s integrated into the wallet and the blockchain synchronization process. Monero.how has provided an easy guide for various systems.

**Mining:** Full nodes are required for mining. With a Monero full node you are able to solo mine, contributing to secure the network (See: [**Mine to Support the Network**](https://www.monerooutreach.org/mine-to-support-the-network.php)). Running a full node helps miners and other nodes know they are on the correct chain, strengthening the blockchain and making attacks harder. In fact, Monero nodes only need to be connected to one honest node to ensure they are on the correct chain.

Pools also run Monero full nodes. Resources from mining pools strengthen security of the Monero network, as well as maintain its decentralization. The more mining pools and solo miners using full nodes on the network, the more secure and decentralized the Monero network will be.

**Remote Nodes:** Remote nodes are full nodes managed by third parties who provide a sharing node service that users can connect to. Users can connect to remote nodes to transact Monero immediately, without the wait associated with synchronizing a full node. Over time, Monero developers have made, and continue to make, substantial improvements for using remote nodes.

While this is a great service and can increase usability and adoption, it also steps over one of the essential building blocks for ultimate privacy on the Monero network. Remote nodes can track your IP address, your “restore height”, and associated block request data. It’s important to be aware of these limitations if you rely on third party nodes.

When you use a remote node you rely on others to check and broadcast your transactions to the network, relinquishing the choice of rules to the remote node operator. Some remote node operators known by the community include, but are not limited to moneroworld, [**monerujo**](https://www.monerujo.io/) (android light-wallet), [**cakewallet**](https://cakewallet.io/) (iOS light-wallet), and [**mymonero**](https://mymonero.com/) (web/desktop light-wallet).

**Conclusion**
Now that you’re informed, be safe out there and strive to use all of the privacy building blocks available to you! For more reading on best practices for staying safe while using Monero, visit: monerooutreach.org/best-practices-for-monero.php
