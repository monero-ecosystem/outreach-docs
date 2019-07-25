# RandomX
*06/05/19*  
_**Monero et Arweave pour valider l'algorithme de preuve du travail.**_ 

En quelle année sommes-nous ? Il semble qu'hier encore, ils disaient qu'une monnaie numérique orientée sur le respect de la vie privée ne pouvait être "élaguée" et que les ASIC finiraient par l'emporter. Mais nous voilà... sur le point de le réaliser et de parler de RandomX... et de porter nos casques d'astronautes. RandomX doit encore faire ses preuves, mais c'est une étape passionnante du développement de Monero. Ce guide vous présente un aperçu de sa nature et de ses plans, et vous indique où vous pouvez en apprendre davantage. 

## _Qu'est-ce que RandomX ?_ 

RandomX est un nouvel algorithme de preuve du travail (PoW) que Monero commencera à expérimenter lors de la prochaine mise à jour du réseau. RandomX est conçu pour résister aux l'ASIC en se servant de l'exécution de code aléatoire et de techniques difficiles à mémoriser pour empêcher le matériel minier spécialisé de dominer le réseau. Comme RandomX est optimisé pour les processeurs généraux, le réseau deviendra plus décentralisé et plus égalitaire dans la distribution des récompenses par blocs. 

Howard Chu (hyc) parlera de RandomX à la prochaine [Monero Konferenco](https://monerokon.com/), d'ici là, visitez le dépôt [RandomX GitHub repo](https://github.com/tevador/RandomX) pour plus de détails. Pour le moment, RandomX commence son processus d'audit avec [Trail Of Bits](https://www.trailofbits.com/), [X41](https://www.x41-dsec.de/), [Quarkslab](https://www.quarkslab.com/en/) et le [Groupe Kudelski](https://www.nagra.com/). RandomX devrait être mis en ligne lors de la prochaine mise à jour du réseau Monero.

## _Qu'est-ce qui va changer ?_

Les ASIC sont les premières victimes de RandomX, comme il est optimisé pour les CPU, les GPU n'auront pas la même proportion de hashrate. 
Début [Nvidia (CUDA) benchmarks](https://github.com/SChernykh/RandomX_CUDA) révèle des augmentations de hashrate entre 100% et 150%, et cela devrait continuellement s'améliorer. Les travaux relatifs aux GPU AMD (OpenCL) sont en cours. Parce que RandomX est difficilement mémorisable, on s'attend à ce que les botnets et les malwares diminuent à mesure que la consommation de la mémoire sera plus facilement remarquée par les administrateurs. Une diminution globale du nethash augmentera la proportion de la prime globale versée aux mineurs légitimes, qu'ils travaillent avec des CPU ou des GPU. 

RandomX a deux modes avec des besoins de mémoire et des performances différents. Le mode rapide nécessite 2 Go de mémoire partagée, mais 4x-6x les performances du mode lumière qui ne nécessite que 256 Mo de RAM. Le mode rapide est destiné aux mineurs dédiés. Le mode Light est conçu pour permettre aux nœuds complets de valider des blocs sans avoir besoin de 2+Go de RAM, de sorte que les petits périphériques (comme les ordinateurs monocartes ARM, par exemple Rock64) peuvent toujours être utilisés comme des nœuds autonomes. 

| CPU | OS | Threads | RAM | CryptoNight-R (v8) | RandomX Fast Mode | RandomX Light Mode |
|--|--|--|--|--|--|--|
| AMD Ryzen 7 1700 | Ubuntu 16.04 | 8 | 16 GB DDR4 | 650 H/s | 4100 H/s | 620 H/s |
| Intel Core i7-8550U | Windows 10 | 4 | 16 GB DDR4 | 240 H/s | 1700 H/s | 350 H/s |
| Intel Core i3-3220 | Ubuntu 16.04 | 4 | 4 GB DDR3 | 75 H/s | 510 H/s | 150 H/s |  

| GPU | Clockspeed | CryptoNight-R (v8) | RandomX |
|--|--|--|--|
| GTX 1660 Ti | 2070/13760 MHz | 626 H/s (98 W) | 660 H/s (103 W) |
| GTX 1080 Ti | 1930/10010 MHz | 787 H/s (145 W) | 1136 H/s (190 W) |  

## _La Collaboration RandomX_ 

RandomX a été développé pour Monero par tevador, hyc, vielmetti, antanst et SChernykh. D'autres organisations sont déjà intéressées par son adoption. [Arweave](https://www.arweave.org/), un facilitateur de stockage sans serveur a fait don de l'audit Trail of Bits à la communauté Monero et va implémenter RandomX avant Monero pour leur propre utilisation. Arweave fournit une approche innovante basée sur les cryptomonnaies pour le stockage décentralisé à long terme des données. L'exploitation minière sur Arweave repose à la fois sur la preuve du travail et - comme nouveau concept unique à Arweave - sur la preuve d'accès. Les mineurs d'Arweave sont incités par la preuve d'accès à la duplication et ont un accès rapide aux données stockées dans le réseau. 

[Wownero](http://wownero.org/) lance également RandomX dans sa prochaine mise à jour v0.6 et l'appellera RandomWOW. Le code RandomX sera mis à jour une fois les audits terminés, de façon a être prêt pour le prochain "fork" du réseau Monero. Une autre différence est que RandomWOW aura un scratchpad plus petit pour le hachage, 1Mo au lieu de 2Mo, un plus petit nombre d'itérations d'exécution de VM, et une augmentation des exécutions de VM en chaîne par hachage pour augmenter le coût de compilation du programme pour les GPU. 

