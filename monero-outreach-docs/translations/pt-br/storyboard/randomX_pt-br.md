# RandomX
*05/06/19*
_**Monero e Arweave para validar o algoritmo de prova de trabalho.**_

Em que ano estamos? Até parece que foi ontem que eles diziam que moedas privadas não poderiam ser melhoradas e que ASICs venceriam no final. Mas aqui estamos...prestes a melhorar e falando do RandomX...usando nossos capacetes espaciais. O RandomX ainda precisa passar pelo processo de ser testado e validado, mas é uma parte empolgante da "pipeline" do Monero. Este guia dará uma visão geral da natureza e dos planos do RandomX e onde você pode aprender mais.

## _O que é o RandomX?_

RandomX é um novo algoritmo de prova de trabalho (do inglês Proof-of-work, PoW) que o Monero está programando para começar a rodar na próxima atualização de rede. O RandomX foi projetado para ser resistente aos ASICs, utilizando um código de execução aleatório e técnicas complexas para memória para prevenir que hardwares especializados em mineração dominem a rede. Como o RandomX é otimizado para CPUs de uso geral, a rede se torna mais decentralizada e igualitária na distribuição de recompensas de bloco.

Howard Chu (hyc) falará sobre o RandomX na [Monero Konferenco](https://monerokon.com/). Até lá, visite o [repositório do RandomX no GitHub](https://github.com/tevador/RandomX) para mais detalhes. À data de elaboração desse artigo, o RandomX estava começando seu processo de auditoria com a [Trail Of Bits](https://www.trailofbits.com/), a [X41](https://www.x41-dsec.de/), o [Quarkslab](https://www.quarkslab.com/en/) e o [Kudelski Group](https://www.nagra.com/). O RandomX está programado para ser ativado na próxima atualização de rede do Monero.

## _O que vai mudar?_

Os ASICs são as principais vítimas do RandomX, mas como ele foi otimizado para CPUs, os GPUs não terão o mesmo aumento na hashrate. Os primeiros [benchmarks da Nvidia (CUDA)](https://github.com/SChernykh/RandomX_CUDA) revelam um aumento no hashrate entre 100% e 150%, e ainda esperam-se aumentos maiores após mais otimizações. Trabalhos para GPUs AMD (OpenCL) estão a caminho.

O RandomX tem dois modos com diferentes requisitos de memória e desempenho. O Modo Rápido requer 2GB de memória compartilhada, mas tem um desempenho de 4 a 6 vezes maior que o Modo Light, que requer 256MB de memória RAM. O Modo Rápido é voltado aos mineradores dedicados. O Modo Light foi desenvolvido para permitir que nós completos validem blocos sem necessitar dos 2GB de memória RAM a mais. Dessa forma, aparelhos pequenos (como computadores ARM de placa única, e.g. Rock64) podem ser utilizados como nós independentes.

| CPU | OS | Threads | RAM | CryptoNight-R (v8) | RandomX Modo Rápido | RandomX Modo Light |
|--|--|--|--|--|--|--|
| AMD Ryzen 7 1700 | Ubuntu 16.04 | 8 | 16 GB DDR4 | 650 H/s | 4100 H/s | 620 H/s |
| Intel Core i7-8550U | Windows 10 | 4 | 16 GB DDR4 | 240 H/s | 1700 H/s | 350 H/s |
| Intel Core i3-3220 | Ubuntu 16.04 | 4 | 4 GB DDR3 | 75 H/s | 510 H/s | 150 H/s |

| GPU | Clockspeed | CryptoNight-R (v8) | RandomX |
|--|--|--|--|
| GTX 1660 Ti | 2070/13760 MHz | 626 H/s (98 W) | 660 H/s (103 W) |
| GTX 1080 Ti | 1930/10010 MHz | 787 H/s (145 W) | 1136 H/s (190 W) |

## _Colaboradores do RandomX_

O RandomX foi desenvolvido para o Monero por tevador, hyc, vielmetti, antanst e SChernykh. Outras organizações já estão interessadas em adotá-lo. O [Arweave](https://www.arweave.org/), um facilitador de armazenamento sem servidor, doou a auditoria da Trail of Bits para a comunidade Monero e implementará o RandomX antes do Monero para um aplicação exclusiva deles. O Arweave oferece um armazenamento de dados de longo prazo, descentralizado e inovador baseado em criptomoedas. Minerar no Arweave se baseia tanto em prova de trabalho como prova de acesso, um conceito novo exclusivo da Arweave. Os mineradores do Arweave são incentivados pela prova de acesso a replicar e ter acesso rápido aos dados armazenados na rede.

O [Wownero](http://wownero.org/) também lançará o RandomX na sua próxima atualização para v0.6 e o chamará de RandomWOW. O código do RandomX será atualizado depois que as auditorias forem concluídas. Portanto, haverá divergência no código no momento do fork do Monero em outubro. Outra diferença é que o RandomWOW tem uma menor scratchpad para hashing, 1MB em vez de 2MB, menor número de iterações de execução VM, e maior execuções em cadeia de VM por hash para elevar o custo de compilação de programa para GPUs.
