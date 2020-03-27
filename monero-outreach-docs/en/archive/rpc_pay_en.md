# RPC-Pay Up Close

**_“Overlooked and underappreciated so far, RPC-Pay allows instant and private microtransactions and is the new stealthy smallest unit of payment in the Monero universe.”_ - 29th of January, 2020**

Why run a Monero public node? It costs money, but doesn’t make money—at least not directly. A recurring concern has been how to incentivize more of these nodes. RPC-Pay offers this incentivization, and much more. It gives a way to use Monero mining hashes—just the hashes—to pay for Remote Procedure Calls (RPCs) from any RPC-Pay-enabled server, such as a Monero node. Hashes received as payment are used by the server to earn income, and because of Monero’s RandomX the mining hashes can be calculated efficiently using most popular CPUs. Paying with just hashes instead of Monero itself means that RPC-Pay does not burden the Monero network or leave a record. With RPC-Pay, mining hashes become a new stealthy smallest unit of payment in the Monero universe.

### _RPC_

Before studying RPC-Pay, it is helpful to understand the larger concept of RPC. RPC is a process through which one program (a client) requests data and calculations from another program (the server). The server can be on any computer on the Internet. An RPC request is like a subroutine call in a regular program except with RPC the subroutine work is performed on the server. Special intermediary software handles the network communication of both the query and its answer so that the programmer sees it as seamless. Many different types of interface software have been used to implement RPC over the years.

A modern family of RPC interface software uses the language of JavaScript Object Notation (JSON) to form messages. JSON is a standard textual format for exchanging data. It relies on name-value pairs and lists of data to define information in a way that is robust, extendable, and human readable. JSON encoding is the primary method used by Monero’s RPC framework.

For Monero, RPC is already being used in a variety of ways. For example, the standard Monero daemon, containing most of Monero's functionality, is _monerod_. It implements the server side of RPC for a variety of blockchain-related function calls. And the program _monero-wallet-rpc_, delivered with the standard Monero installation, implements the server side of wallet functionality while itself being a client to a _monerod_ server. Monero RPC calls work much like a browser communicating with a web server. Data is sent using the POST method, and returned information is textual, usually JSON. If you are interested in detailed examples of RPC messages, please see [Example #1](https://www.monerooutreach.org/stories/RPC-Pay.html#box1) on using Monero RPC calls.

### _Mining Hashes_

The mining process for Monero's RandomX Proof of Work (PoW) starts by executing a pseuorandom program that is a function of the new transactions, a nonce, a payment address, and data from the previous block. Executing a random program like this is easy for CPUs, but hard for ASICs. The output of the program is then cryptographically hashed into a 256-bit number. If this number is less than a specified threshold, then it counts as mining a new block.

A beauty of this hashing process is that the payment address is specified before the hash is generated, which allows hashes to be created specifically for someone else. This property allows mining pools to function—hashes are made using the pool’s payment address. There are few analogies to a mining hash in the physical world. It is a creation that can have value only for the owner of the destination address, and its value only lasts until the next block is mined. Monero blocks are mined about every two minutes.

For RPC-Pay, the hashes are calculated by the RPC client itself or by a (more powerful) helper to the client, and the hashes are sent to the server as they are calculated. Every hash sent counts as payment. A miniscule percentage of the hashes will actually have value to the server—those that, when represented as a number, mine a block by being small enough. These successful hashes occur at random within the many payment hashes. The server, then, counts all the hashes for credit, but only receives payment itself when it receives and publishes a successful mining hash on the Monero network.

### _RPC-Pay_

RPC-Pay is a new feature added to _monerod_ and wallets that enables payment for RPC calls using mining hashes. This capability is configured through the command line when starting the _monerod_ software. Representative startup parameters are illustrated below in [Example #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2). Similarly, there are commands with the CLI wallet that enable it to create hashes and pay monerod, and these are also presented in [Example #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2).

With the current Monero release, there is a _monerod_ command (of the type that can be typed right into the _monerod_ console) related to RPC, rpc_payments. This command displays information on paying clients and their balances in the console window. Note that a node will forget about credit balances after they are untouched for six months.

RPC-Pay offers many advantages. It supports decentralization because many people will want to run a server that pays for itself, versus the smaller number willing to run one at cost. Payment for RPC also encourages some wallet users to run their own node to avoid having to pay. All this strengthens and decentralizes the network.

RPC-Pay is private. No large credit balances are maintained that require sharing information for backup or security. The mining hashes used for payment are anonymous without a way to trace ownership on the blockchain. A payment ID can be applied to track and maintain balances, but with an operating procedure based on small balances, this ID can be changed regularly or not used at all.

It is important to also consider the disadvantages of the current _monerod_/wallet implementation of RPC-Pay. It can burden low-power clients, such as mobile devices, which must rely on other helper computers for their hashes. Also, the income to the server is random. It comes only when a client provides a hash that can mine a block, while the server’s output must be continuous, matching the regular provision of hashes. Finally, the amount of income a server can make is limited by the Monero mining schedule and will tend to be small.

There is more to RPC-Pay that just Monero programs paying other Monero programs, as any server can use RPC-Pay to earn income. The software in the official Monero node and wallet is open source and can be reused for innovative applications, or other applications can communicate with monerod instances. The core concept is simply that the server gives its Monero address to its clients and the clients use this to create Monero mining hashes that it sends to the server as payment. [Example #3](https://www.monerooutreach.org/stories/RPC-Pay.html#box3) gives an example of RPC-Pay software source code.

### _Primo_

An example new RPC-Pay application is the Primo project ([repo.getmonero.org/selene/primo](https://repo.getmonero.org/selene/primo)). Primo is a protocol and software suite supporting paid website content delivery. It allows undesirable website ads to be replaced with invisible and unobtrusive hash generation. A visitor to a Primo-enabled website who does not want to see ads can opt to calculate Monero mining hashes instead.

Primo has three components. The first is the _primo-apache_ module for use on the web server. The website owner installs this module and configures what content requires payment and how much. The web server communicates with a _monerod_ instance, which handles bookkeeping on payments of hashes and using successful hashes to collect mining revenue. The second component is the _primo-firefox_ extension. A visitor to the website wanting to use RPC-Pay will have this loaded into the Firefox browser. And the third component is the _primo-control-center_ graphical control tool. With this, the Firefox user can configure what websites receive payment.

Primo offers compensation for the website owner and ad-avoidance for visitors, all while strengthening the Monero network. The clients providing hashes and the server using these hashes form a complete mining process. And the more and more diverse miners for Monero, the better. Primo is an excellent example of the possibilities for RPC-Pay.

### _Looking Forward_

RPC-Pay was first released with Monero version 0.15. It is brand new. With time, capabilities will be added, and as RPC-Pay evolves so will its applications. Primo is the first outside application, serving as an example to others. Any server on the Internet providing data or calculations to clients is a potential candidate for using RPC-Pay for funding. With RandomX as Monero’s PoW algorithm, also new with 0.15, any computer can efficiently calculate hashes to make RPC-Pay payments. The time is right for this new feature, and it will produce many exciting developments.

### _Getting Started Guides_

##### _#1: Monero RPC Example_
---

Using the command-line tool curl ([curl.haxx.se](https://curl.haxx.se/)), you can send Monero RPC calls to either your own monerod instance or a public server. For example, if you would like to know how many blocks are in the Monero blockchain, you can use the RPC command get_block_count. To get this information from a public server at Monero World, install curl and on the command line type the following:

```
curl -X POST [uwillrunanodesoon.moneroworld.com:18089/json_rpc](http://uwillrunanodesoon.moneroworld.com:18089/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

You will get a response that looks like this:

```
{ "id": "0", "jsonrpc": "2.0", "result": { "count": 2021560, "status": "OK", "untrusted": false } }
```

The number of blocks in the blockchain when this was generated was 2,021,560.

If you are running your own _monerod_ instance with a standard configuration, you can get the same information with the following, similar, command on that same computer:

```
curl -X POST [127.0.0.1:18081/json_rpc](http://127.0.0.1:18081/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

For more information on the _monerod_ RPC interface, please see [web.getmonero.org/resources/developer-guides/daemon-rpc.html](https://web.getmonero.org/resources/developer-guides/daemon-rpc.html). And for information on the wallet RPC interface, please see [web.getmonero.org/resources/developer-guides/wallet-rpc.html](https://web.getmonero.org/resources/developer-guides/wallet-rpc.html)

##### _#2: Setting up Daemon and Wallet_
---

To test your own local _monerod_ daemon functioning with RPC-Pay, run it with the following options:

```
monerod --restricted-rpc --rpc-payment-address 4xxxxxx --rpc-payment-credits 250 --rpc-payment-difficulty 1000
```

The payment address is a standard Monero payment address that will receive payments whenever a mining hash payment actually mines a new block. The rpc-payment-credits and payment-difficulty values work together so that a client receives the ratio credits/difficulty for each mining hash provided. These examples, which you will want to change to suit your needs, would give 250/1000 = 0.25 credits per hash. You can then run the wallet on the same computer:

```
monero-wallet-cli
```

Once the CLI wallet is initiated, typing start_mining_for_rpc will start the RPC-Pay process. Credits can be monitored using the command rpc_payment_info. The credits-target value is the number of credits the wallet will seek to maintain. After reaching this number of credits, it should stop mining. You can set this target using a command like the following in the CLI wallet:

```
set credits-target 50000
```

The auto-mine-for-rpc-payment-threshold value is the minimum credit rate for which the wallet will mine. If the server provides a lower rate, then the wallet will not send hashes. You can set this threshold using a command like the following in the CLI wallet:

```
set auto-mine-for-rpc-payment-threshold 0.25
```

##### _#3: Coding Example_
---

Code for RPC pay can be written in C (or other languages) using free libraries for network communication. Shown below is an example of how RPC-Pay data in C can be communicated to a monerod instance using curl. This is the same curl family as was used for textual interfacing in Box 1. Curl is both a library and a command-line tool. The code below is a simplified version of the call_monero() function in Primo, which is part of the primo-apache module. You can see the original code at [repo.getmonero.org/selene/primo/blob/master/webserver/apache/mod_primo.c](https://repo.getmonero.org/selene/primo/-/tree/master)

```
/* Note! Simplified, without some initialization, error checks, and memory cleanup. */
static char *call_monero(const char *host, const char *postdata)
{
...

CURL *curl = curl_easy_init();

char url[1024];
snprintf(url, sizeof(url), "%s/json_rpc", host);
curl_easy_setopt(curl, CURLOPT_URL, url);
curl_easy_setopt(curl, CURLOPT_POST, 1);
curl_easy_setopt(curl, CURLOPT_POSTFIELDSIZE, strlen(postdata));
curl_easy_setopt(curl, CURLOPT_POSTFIELDS, postdata);
curl_easy_setopt(curl, CURLOPT_VERBOSE, 1);
curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, &writef);
primo_writer_t writer_data = {calloc(1, 1), 0};
curl_easy_setopt(curl, CURLOPT_WRITEDATA, &writer_data);
struct curl_slist *list = NULL;
list = curl_slist_append(list, "Content-Type: application/json");
curl_easy_setopt(curl, CURLOPT_HTTPHEADER, list);
int res = curl_easy_perform(curl);

return writer_data.data
}
```
