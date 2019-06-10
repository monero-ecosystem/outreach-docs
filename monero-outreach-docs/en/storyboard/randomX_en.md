# RandomX
*06/05/19*  
_**Monero and Arweave to Validate the Proof-of-Work Algorithm.**_ 

What year is it? It seems like only yesterday they were saying that a privacy coin couldn’t be pruned and that ASICs will win in the end. But here we are...about to prune and talking about RandomX...wearing our space helmets. RandomX still must go through the process of becoming tried and true, but it’s an exciting part of Monero’s pipeline. This guide gives an overview of its nature and plans, and where you can learn more. 

## _What is RandomX?_ 

RandomX is a new Proof-of-Work (PoW) algorithm that Monero is scheduled to begin using in the next network update. RandomX is designed to be ASIC resistant by using random code execution and memory-hard techniques to prevent specialized mining hardware from dominating the network. Because RandomX is optimized for general-purpose CPUs, the network will become more decentralized and egalitarian in the distribution of block rewards. 

Howard Chu (hyc) will be speaking about RandomX at [Monero Konferenco](https://monerokon.com/), until then, visit the [RandomX GitHub repo](https://github.com/tevador/RandomX) for more details. At the time of writing, RandomX is beginning the auditing process with [Trail Of Bits](https://www.trailofbits.com/), [X41](https://www.x41-dsec.de/), [Quarkslab](https://www.quarkslab.com/en/) and the [Kudelski Group](https://www.nagra.com/). RandomX is scheduled to go live during the next Monero network update. 

## _What Will Change?_

ASICs are the main casualty of RandomX, but since it’s optimized for CPUs, GPUs won’t get the same increase in hashrate. Early [Nvidia (CUDA) benchmarks](https://github.com/SChernykh/RandomX_CUDA) reveal hashrate increases between 100% and 150%, and that’s expected to improve with more optimization. Work for AMD GPUs (OpenCL) is underway. Because RandomX is memory hard, it’s expected that botnets and malware mining will decrease as the memory consumption will be more easily noticed by administrators. An overall decrease in nethash will increase the proportion of the block reward going to legitimate miners whether they are mining with CPUs or GPUs. 

RandomX has two modes with different memory requirements and performance. Fast Mode requires 2GB of shared memory but has 4x-6x the performance of Light Mode which only requires 256MB of RAM. Fast mode is intended for dedicated miners. Light mode is designed to allow fullnodes to validate blocks without requiring the 2+GB of RAM, so that small devices (like ARM single-board computers, e.g. Rock64) can still be used as standalone nodes. 

| CPU | OS | Threads | RAM | CryptoNight-R (v8) | RandomX Fast Mode | RandomX Light Mode |
|--|--|--|--|--|--|--|
| AMD Ryzen 7 1700 | Ubuntu 16.04 | 8 | 16 GB DDR4 | 650 H/s | 4100 H/s | 620 H/s |
| Intel Core i7-8550U | Windows 10 | 4 | 16 GB DDR4 | 240 H/s | 1700 H/s | 350 H/s |
| Intel Core i3-3220 | Ubuntu 16.04 | 4 | 4 GB DDR3 | 75 H/s | 510 H/s | 150 H/s |  

| GPU | Clockspeed | CryptoNight-R (v8) | RandomX |
|--|--|--|--|
| GTX 1660 Ti | 2070/13760 MHz | 626 H/s (98 W) | 660 H/s (103 W) |
| GTX 1080 Ti | 1930/10010 MHz | 787 H/s (145 W) | 1136 H/s (190 W) |  

## _RandomX Collaboration_ 

RandomX was developed for Monero by tevador, hyc, vielmetti, antanst and SChernykh. Already other organizations are interested in adopting it. [Arweave](https://www.arweave.org/), a serverless storage enabler donated the Trail of Bits audit to the Monero community and will be implementing RandomX before Monero for their unique application. Arweave provides an innovative cryptocurrency-based approach to decentralized, long-term data storage. Mining on Arweave relies on both proof of work and—as a new concept unique to Arweave—proof of access. Arweave miners are incentivized through proof of access to replicate and have quick access to data stored in the network. 

[Wownero](http://wownero.org/) is also launching RandomX in their upcoming v0.6 update and will call it RandomWOW. RandomX code will be updated after the audits are complete, so there will be some code divergence by the time Monero forks in October. Another difference is that RandomWOW will have a smaller scratchpad for hashing, 1MB instead of 2MB, smaller number of VM execution iterations, and increased chained VM executions per hash to increase program compilation cost for GPUs. 

