# How to Accept Monero

If you are able to install an app, you’ll be able setup your business to accept Monero (XMR). This guide explains the most common ways merchants accept Monero and how to get started painlessly and build on that as you grow.

First there isn’t a special kind of Monero merchant account—you just need a regular wallet and an address to start. It’s recommended that you create a separate address for business transaction for the same reasons that having seperate business and personal checking accounts is suggested. You can use the same wallet software, but having dedicated address for business will help keep accounts organized.

If you don’t already have a Monero wallet/address then you’ll want to create that first. The official Monero GUI/CLI wallets from [getmonero.org/downloads](https://www.getmonero.org/downloads/) are always recommended. Also, this guide will reference mobile wallets and you can find information about those on our [Monero Wallet Setup](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html) page.

### _The Anatomy of a Monero Transaction_

Monero transactions go through the following steps. It’s not necessary to understand the technical aspects of this, but as a merchant, you do need to have a basic knowledge of the steps to be able to decide what tradeoffs are right for you.

1. **Purchase** - After adding up the customers purchase in local fiat and applying sales tax if needed, you simply need to calculate the corresponding amount in XMR.
2. **Payment** - The customer scans your QR code to pay you in XMR. The Monero transaction fee is paid by the sender and calculated as the time of transaction.
3. **Transaction Pool** - Within a second, the transaction is announced to the Monero network and placed in the transaction pool, also called the mempool. You can check for the existence of your transaction in the mempool, an example mempool can be seen here: xmrchain.net/txpool.
4. **Confirmation** - Within 4 minutes, the transaction will usually be in a block on the blockchain and you can have confidence that it is valid. The payment will now appear in your wallet as locked funds. Your transaction will be confirmed by 9 more blocks before being unlocked and virtually impossible to reverse.

There may be a lag in how quickly your wallet checks for new transactions, often 90 seconds. So depending on when your wallet checks for new transactions and how quickly your transaction gets into mined block, the actual expected time before it shows up in your wallet is 4-12 minutes. For a more in-depth look at the Monero transaction process and average duration, visit [monero.how/how-long-do-monero-transactions-take](https://www.monero.how/how-long-do-monero-transactions-take).

If a 4-12 minute wait is impossible for your business, you can do a zero confirmation transaction in one second. Instead of waiting for first confirmation, you look into the transaction pool to check that the transaction exists. There’s a risk because the transaction hasn’t been confirmed, but a double-spend attack is unlikely if the person is standing in front of you. For smaller scale retail transactions, the benefit of completing the transaction in one second is usually worth a minor risk and if something isn’t feeling right to you, you can always choose to wait for first confirmation on a case-by-case basis.

### _Identifying Transactions_

One thing that becomes obvious when you start accepting Monero is that you don’t automatically know the senders address because transactions are private. Depending on your business linking the transaction and the payment might not be a big deal, or it might be a really big deal. That will be up to you, the good news is that there are several simple techniques to help you positively indentify your XMR payments.

The first is simple, make a note. If you’re dealing with a fairly low volume of transactions you can just add your invoice or transaction number as at note in your wallet when you receive funds. Alternately, you could note the Monero transaction ID in your Point Of Sale (POS) system or accounting software.

But when you absolutely, positively need to link a customers payment with a transaction, using Monero’s subaddresses is the answer. A subaddress is a single-use address, and since they’re free and you can make as many as you would like, you can give a unique subaddress to each customer to be able to track each payment. This feature is also useful if you’d like to keep your main address private.

### _Multisig Transactions_

Multisig transactions require signing from multiple parties before it can be announced to the network. For example, you could arrange a transaction so that the funds aren’t released until both the buyer and seller agree. We won’t go deeper into multisig with this article, but visit [getmonero.org/resources/user-guides/multisig-messaging-system.html](https://www.getmonero.org/resources/user-guides/multisig-messaging-system.html) to learn more.

### _LeMonero Enterprises, LLC_

With that overview of how a Monero transaction works, let’s apply it to some real world examples using our fictional company LeMonero Enterprises, LLC. It’s a rags to riches story of Monero adoption and integration where we’re going to sell lemonade and our customers are going to pay in Monero three different ways as we grow.

In all of these examples, let’s say that we’re selling our lemonde, priced in local fiat, for $1. Our accounting and our tax-burden is also in fiat. Your conditions will depend on where you live and how your type of business is regulated.

### _LeMonero Stand_

In our lemonade stand we’ve got a simple cash box and notebook to record each sale, as is common at farmer’s markets, festivals, pop-up retail events and community craft sales where setup is limited. The good news is that accepting Monero for this kind of simple transaction only needs a smartphone.

For payments in Monero, the transaction starts out the same as for fiat. You prepare the lemonade, figure out the total and record the transaction in your notebook according to your accounting needs.

A $1.00 total is converted into XMR right before payment. The exchange rate is constantly changing. At the time of writing, 1 XMR cost $61.40 USD, so a $1.00 lemonade would cost 0.0162 XMR.

The customer needs to get your address into their phone to pay you 0.0162 XMR. Copy-and-pasting text sometimes works, but usually Monero addresses are exchanged with QR codes. The QR code contains your Monero address in a form that the customer’s wallet can scan. Your wallet generates this for you when you click ‘receive,’ and you can turn your wallet screen for the customer to scan it. Alternatively, you can have a QR code printed and posted, then just use your wallet to confirm the transaction.

As soon as the customer sends you the XMR, the transaction is broadcast to the Monero network. Funds will appear in your wallet in 4-12 minutes after the first confirmation.

We rarely have to make a customer wait, though, as trust can be extended to lemonade customers, especially regulars. For someone sketchy with a big order, we might just explain that it’ll take a few minutes.

### _LeMonero Cafe_

With hard work, our little lemonade stand has grown into a lemonade cafe. We’re an independent brick-and-mortar retailer now. In addition to cash and Monero like before, the cafe accepts credit/debit cards and has POS system to record transactions and manage inventory instead of a notebook.

LeMonero has higher overhead, and we can’t afford to just hold the XMR payments—we need to convert some XMR into fiat to pay the bills though we choose to settle into fiat manually when it’s most advantageous. We still need a payment processor, though, so customer check-outs are quick and easy.

Most business owners are familiar with credit/debit payment processors, third-parties that rent you the terminal, who put you on their network and charge you fees by the transaction and by the month. A Monero payment processor can work like this, or you can be your own payment processor with a little bit of software and not pay any transaction fees at all.

Because Monero software is open-source you can scratch-build your own payment gateway (how cool is that), but Monero Integrations has already done the work for you and crafted libraries and plugins that do all the heavy lifting at [github.com/monero-integrations](https://github.com/monero-integrations).

Alternatively, a third-party Monero payment processor will have packaged software and apps and interfaces that make setup simple. They will also have interfaces and tools for you to manage your account, and customer/technical support. See our Monero Payment Processor Guide for help deciding which setup is right for you.

### _LeMonero.com_

Our lemonade cafe is driving people wild and we’ve expanded into online sales and more storefronts. The good news is that we don’t need to change our payment processor, we just need to use it more.

Shopping cart integration is easy compared to physical, real-time transactions. Whether you’re using an open-source payment processor or a third-party service, plugins for WooCommerce, Shopify, etc. are available and easy to install.

We now can have automatic settlement in fiat. As a lemonade stand, we held our XMR payments; when we were a cafe, we liquidated some when the exchange was favorable. But our cash-flow needs have intensified. We need a predictable XMR to fiat exchange even if it means additional fees or unfavorable timing.

Most third-party payment processors will provide automatic fiat conversion with their partner exchanges for a fee. There may be additional tranaction or withdrawl fees depending on the providers, but the convenience may be worth it.

With an open-source payment processor you’re free to develop you own solution using the API of your preferred exchange with monero-wallet-rpc calls. This is beyond the scope of this tutorial, but you can find out more a [getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/resources/developer-guides/wallet-rpc.html).

### _Learn More_

- How to accept Monero with the official Monero wallets: [getmonero.org/get-started/accepting](https://www.getmonero.org/get-started/accepting/)
- [Monero Merchant FAQs](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
- Monero Multisignatures Explained: [hackernoon.com/monero-multisignatures-explained...](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
- Potential Risks of Accepting Zero Confirmation Transactions: [reddit.com/r/Monero/.../potential_risks_of_accepting_zero_confirmation](https://www.reddit.com/r/Monero/comments/7s937y/potential_risks_of_accepting_zero_confirmation/)

Illustrations By: