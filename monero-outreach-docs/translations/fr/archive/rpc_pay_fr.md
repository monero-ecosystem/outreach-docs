# Paiement-RPC Vu de Près

**"Négligé et sous-apprécié jusqu'à présent, le Paiement-RPC permet des microtransactions instantanées et privées. Il s'agit de la nouvelle, et la plus petite, dénomination de paiement furtif de l'univers Monero." - 29 janvier, 2020**

Pourquoi héberger un nœud Monero publique? Cela vous coûte de l'argent, mais ne vous en rapporte pas - du moins pas directement. Une préoccupation récurrente au sein de la communauté Monero a été d'inciter plus d'utilisateurs à héberger des nœuds accessibles publiquement. Le Paiement-RPC est un système qui cherche à mettre en place cet incitatif, et plus encore. Il permet d'utiliser les hash de minage - uniquement les hash - comme paiement pour des Appels de Procédure à Distance ("Remote Procedure Call" - RPC - en anglais) pour les serveurs qui le permettent, dont les nœuds Monero. Les hash reçus en paiement sont utilisés par le serveur pour générer un revenu, et avec l'algorithme RandomX de Monero les hash de minage peuvent être calculés avec grande efficacité en utilisant des CPU courants. De plus, le paiement avec les hash (plutôt qu'avec des Monero) fait en sorte que le Paiement-RPC ne contraint pas le réseau Monero et ne laisse aucune trace de paiement. Grâce au Paiement-RPC, les hash de minage deviennent la nouvelle, et plus petite, unité de paiement de l'univers Monero.

### _RPC_

Avant d'approfondir le fonctionnement du Paiement-RPC, il est opportun de considérer le concept général derrière le fonctionnement des Appels de Procédures à Distance (RPC). Il s'agit d'un processus par lequel un programme (le client) effectue une requête pour des données et des calculs venant d'un autre programme (le serveur). Le serveur peut être situé sur n'importe quel ordinateur sur l'Internet. Une requête RPC s'apparente à un appel de procédure imbriqué dans un program régulier, à l'exception qu'avec RPC le travail de la procédure est effectué sur le serveur. Un logiciel intermédiaire dédié traite la communication de la requête et la réponse sur le réseau afin que le tout se fasse de manière fluide. Plusieurs logiciels ont été développés pour servir d'interface et permettre l'implémentation de RPC au fil des ans.

Une itération plus récente de logiciels d'interface RPC fait appel au langage de JavaScript Object Notation (JSON), un format textuel standard pour l'échange de données, pour la formation des messages. Grâce à des appariements de noms et valeurs ainsi que des listes de données, la définition des informations est robuste, extensible et lisible à l'humain. L'encodage JSON est désormais la méthode principale utilisée par l'infrastructure RPC de Monero.

Pour Monero, le processus RPC est déjà utilisé à plusieurs fins. Par exemple, le démon standard de Monero, qui contient la plupart des fonctionnalités de Monero, est _monerod_. Il implémente le RPC côté serveur pour plusieurs appels de fonctions reliés aux fonctionnalités de la chaîne de blocs. Le programme _monero-wallet-rpc_ (inclus avec l'installation standard de Monero), implémente l'instance côté serveur de la fonctionnalité du portefeuille tout en étant lui-même le client d'un serveur _monerod_. Les appels RPC de Monero opèrent d'une manière similaire à celle d'un fureteur internet qui communique avec un serveur web. Les données sont envoyées avec la méthode POST, et l'information retournée est textuelle (habituellement en JSON). Si vous voulez des exemples détaillés de messages RPC, voyez [Exemple #1](https://www.monerooutreach.org/stories/RPC-Pay.html#box1) sur l'utilisation des appels RPC Monero.

### _Hash de Minage_

Le processus de minage de Monero, basé sur l'algorithme RandomX pour certifier la Preuve de Travail (en anglais "Proof of Work" - PoW), démarre le calcul en exécutant un programme pseudo-aléatoire qui est fonction des nouvelles transactions, un nonce, une adresse de paiement, et des données du bloc précédent. L'exécution d'un tel programme aléatoire est trivial pour un CPU d'ordinateur mais très difficile pour un système dédié comme les ASICs utilisés pour miner d'autres cryptomonnaies. La sortie de ce programme subit ensuite un hachage cryptographique pour produire un chiffre à 256 bit. Si ce chiffre est inférieur à un seuil désigné, l'opération compte vers le minage d'un nouveau bloc sur la chaîne de blocs Monero.   

Un avantage de cette approche de hachage est que l'adresse de paiement est spécifiée avant même que le hash ne soit généré, ce qui permet à des hash d'être créés spécifiquement à l'intention d'un tiers. Cette propriété permet au pools de minage de fonctionner adéquatement - les hash sont générés en utilisant l'adresse de paiement du pool. Il n'existe pas vraiment d'analogie réelle qui permettrait de mieux comprendre la forme et le rôle d'un hash de minage. Il s'agit d'un concept artificiel qui renferme seulement une valeur pour le propriétaire de l'adresse de destination, et cette valeur expire dès lors qu'un nouveau bloc est miné. Un nouveau bloc de Monero est miné aux deux minutes.

Pour le Paiement-RPC, les hash sont calculés par le client RPC lui-même (ou par un tiers qui pourrait posséder une plus grande puissance de traitement), et les hash sont envoyés au serveur au fur et à mesure qu'ils sont calculés. Chaque hash envoyé compte comme un paiement. Une infime proportion des hash auront une valeur réelle pour le serveur - ceux qui, lorsque représentés sous forme numérique, minent un bloc en étant suffisamment petit. Ces hash "gagnants" ont une occurrence aléatoire au sein de la suite des hash de paiement. Le serveur tabule ensuite tous les hash pour calculer le crédit qui lui est dû, et reçoit ce paiement lorsque le hash de minage "gagnant" est publié sur le réseau Monero.

### _Paiement-RPC_

Le Paiement-RPC est une nouvelle fonctionnalité du _monerod_ et des portefeuilles qui permet un paiement aux appels RPC en utilisant des hash de minage. Cette fonctionnalité est configurée par la ligne de commande lors du démarrage du logiciel _monerod_. Voir ici une représentation des paramètres de démarrage typiques : [Exemple #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2). Il existe également des commandes pour le portefeuille CLI qui lui permettent de créer des hash et de payer monerod, qui peuvent être retrouvées ici: [Exemple #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2).

Dans la version courante de Monero, la commande pertinente à entrer dans le _monerod_ (qui peut être entrée directement dans la console _monerod_) est rpc_payments. Cette commande affiche l'information sur les clients payants et leur solde dans la fenêtre de la console. Fait à noter, un nœud oubliera le solde des crédits si les crédits demeurent intouchés pendant six mois.

Le Paiement-RPC offre plusieurs avantages, notamment d'encourager la décentralisation du réseau Monero en permettant à un serveur de générer un revenu afin de contrebalancer son coût d'opération et rendant ainsi la création d'un nœud plus intéressante et moins demandant à l'individu. Le paiement par RPC encourage également les utilisateurs de portefeuilles d'héberger leur propre nœud afin de ne pas avoir à payer de frais de transaction. Ces deux éléments contribuent de manière importante à la résilience et la décentralisation du réseau Monero.

Le Paiement-RPC est également privé. Il n'y a pas de grand solde de crédits dus qui seront maintenus et qui pourraient nécessiter un partage d'informations pour la redondance ou la sécurité. Les hash de minage utilisé pour le paiement sont anonymes et il n'est pas possible d'en identifier le propriétaire sur la chaîne de blocs. Un identifiant de paiement peut être appliqué pour faire le suivi des soldes, mais la procédure d'opération associée aux très petits montants en jeu permet à l'identifiant d'être régulièrement changé ou, à rigueur, de ne carrément pas être utilisé.

Il est également pertinent de considérer les désavantages de l'implémentation actuelle du Paiement-RPC dans le _monerod_ ou les portefeuilles. Celle-ci peut devenir un fardeau pour les utilisateurs ayant une faible capacité de calcul (p.ex. les appareils mobiles, qui sont dépendants du soutien d'un tiers avec plus de puissance de calcul pour leur hash). De plus, la récompense qui revient au serveur est aléatoire: elle est seulement octroyée lorsqu'un client fournit un hash "gagnant" qui servira à miner un bloc, tandis que les sorties du serveur doivent être continues et doivent fournir une provision régulière de hash. Finalement, les montants qu'un serveur peut générer sont limités par l'échéancier de minage de Monero et ont tendance à être faibles.

Le Paiement-RPC a plus encore à offrir qu'un simple mécanisme de paiement et de récompense entre les différents programmes de Monero, puisque tout serveur peut utiliser le Paiement-RPC pour générer un revenu. Le logiciel du Paiement-RPC, incorporé dans celui du nœud et portefeuille officiel de Monero, est à code source ouvert et peut être réutilisé pour d'autres applications innovantes, ou peut servir à habiliter d'autres applications à communiquer avec les instances monerod. Le concept fondamental demeure que le serveur donne son adresse Monero à ses clients, qui l'utilisent pour créer des hash de minage Monero qui sont ensuite envoyés au serveur en guise de paiement. [L'Exemple #3](https://www.monerooutreach.org/stories/RPC-Pay.html#box3) illustre une portion du code source du logiciel de Paiement-RPC.

### _Primo_

Le Projet Primo représente une nouvelle application du Paiement-RPC ([repo.getmonero.org/selene/primo](https://repo.getmonero.org/selene/primo)). Primo est un protocole et une suite logicielle qui supporte le paiement pour la livraison de contenu web. Il permet à des annonces web indésirables d'être remplacées par des générateurs de hash invisibles et discrets. Quelqu'un qui visite un site web qui roule Primo et qui ne veut pas voir d'annonces peut opter pour la génération de hash de minage Monero.

Primo possède trois composantes. La première est le module _primo-apache_ destiné au serveur web. Le propriétaire du site web installe le module et configure le contenu qui nécessitera un paiement, ainsi que le montant requis. Le serveur web communique avec une instance _monerod_, qui gère le suivi des paiements et transforme les hash "gagnants" en un revenu de minage. La seconde composante est l'extension _primo-firefox_. Un visiteur au site web qui désire utiliser le Paiement-RPC devra avoir l'extension activée dans le fureteur Firefox. La troisième composante est l'outil de contrôle graphique _primo-control-center_. Grâce à cet outil, l'utilisateur Firefox peut configurer quels sites web reçoivent un paiement.

Primo offre une compensation pour le propriétaire du site web et un mécanisme pour que les visiteurs puissent éviter de voir des annonces, tout en renforçant le réseau Monero. Les fournisseurs fournissent les hash et le serveur les utilise pour former un processus de minage complet. Plus le réseau de mineurs Monero sera diversifié, mieux ce sera pour l'écosystème entier. Primo est un excellent exemple des possibles applications du Paiement-RPC.

### _Regard Vers L'avenir_

Le Paiement-RPC a été intégré pour la première fois à la version 0.15 de Monero. Il est tout neuf. Avec le temps, des nouvelles fonctionnalités seront ajoutées : les applications potentielles du Paiement-RPC évolueront avec le système lui-même. Primo est la première application externe, qui servira d'exemple aux autres. Tout serveur sur l'Internet qui fournit des données ou des calculs aux clients est un client potentiel pour l'utilisation du Paiement-RPC à des fins de financement. Avec RandomX comme algorithme de preuve de travail de Monero, aussi inclus pour la première fois dans la version 0.16, tout ordinateur peut calculer des hash de minage pour alimenter le Paiement-RPC. Le temps est venu pour cette nouvelle fonctionnalité, et elle entrainera plusieurs développements excitants.

### _Guides de Démarrage_

##### _#1: Exemple de Paiement-RPC Monero_
---

En utilisant le curl de la ligne de commande ([curl.haxx.se](https://curl.haxx.se/)), vous pouvez envoyer des appels RPC Monero à votre propre instance monerod ou à un serveur publique. Par exemple, si vous voulez savoir combien de blocs composent la chaîne de blocs Monero, vous pouvez utiliser la commande RPC get_block_count. Pour obtenir cette information à partir d'un serveur publique chez Monero World, installez curl et entrez la commande suivante à la ligne de commande:

```
curl -X POST [uwillrunanodesoon.moneroworld.com:18089/json_rpc](http://uwillrunanodesoon.moneroworld.com:18089/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Vous aurez une réponse qui ressemble à ceci:

```
{ "id": "0", "jsonrpc": "2.0", "result": { "count": 2021560, "status": "OK", "untrusted": false } }
```

Le nombre de blocs dans la chaine de blocs était de 2,021,560 lorsque cette sortie a été générée.

Si vous faites rouler votre propre instance de _monerod_ en configuration standard, vous pouvez obtenir la même information avec les commandes suivantes (similaires) sur le même ordinateur:

```
curl -X POST [127.0.0.1:18081/json_rpc](http://127.0.0.1:18081/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Pour plus d'information à propos de l'interface entre _monerod_ et RPC, voir [www.getmonero.org/resources/developer-guides/daemon-rpc.html](https://www.getmonero.org/resources/developer-guides/daemon-rpc.html). Pour plus d'information à propos de l'interface entre le portefeuille et RPC, voir [www.getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/resources/developer-guides/wallet-rpc.html).

##### _#2: Mettre sur pied le Daemon et le Portefeuille_
---

Pour tester votre _monerod_ local qui fonctionne avec le Paiement-RPC, exécutez-le avec les options suivantes:

```
monerod --restricted-rpc --rpc-payment-address 4xxxxxx --rpc-payment-credits 250 --rpc-payment-difficulty 1000
```

L'adresse de paiement est une adresse Monero standard qui recevra un paiement lorsque le hash de minage découvre un nouveau bloc. Les valeurs crédits-paiement-rpc et difficulté-paiement travaillent de pair pour que le client reçoive le ratio crédits/difficulté pour chaque hash de minage fourni. Ces exemples, que vous devrez modifier selon vos besoins, donneraient 250/1000 = 0.25 crédits par hash. Vous pouvez alors exécuter le portefeuille sur le même ordinateur:

```
monero-wallet-cli
```

Lorsque le portefeuille CLI est initié, le processus de Paiement-RPC sera démarré avec la commande start_mining_for_rpc. Les crédits peuvent être suivis en utilisant la commande rpc_payment_info. La valeur crédit-cible représente le nombre de crédits que le portefeuille cherchera à conserver. Lorsque ce nombre sera atteint, il devrait cesser l'opération de minage. Vous pouvez fixer cette cible en utilisant une commande à la ligne comme celle-ci dans le portefeuille CLI:

```
set credits-target 50000
```

La valeur du seuil auto-mine-for-rpc-payment-threshold représente le taux de crédit minimal pour lequel le portefeuille exécutera une opération de minage. Si le serveur offre un taux inférieur au seuil, le portefeuille n'enverra pas de hash. Vous pouvez fixer ce seuil en utilisant une commande à la ligne comme celle-ci dans le portefeuille CLI:

```
set auto-mine-for-rpc-payment-threshold 0.25
```

##### _#3: Exemple de Code_
---

Le code pour le Paiement-RPC peut être en C (ou autres langages) à l'aide de librairies gratuites pour la communication de réseau. Ci-bas, un exemple de la manière dont les données Paiement-RPC en C peuvent être communiquées à une instance monerod en utilisant curl. Il s'agit de la même famille curl que nous avons utilisée pour l'interfaçage textuel dans la Boîte 1. Curl est une librairie et un outil de ligne de commande. Le code ci-bas est une version simplifiée de la fonction call_monero() dans Primo, qui fait partie du module primo-apache. Vous pouvez consulter le code original ici: [repo.getmonero.org/selene/primo/blob/master/webserver/apache/mod_primo.c](https://repo.getmonero.org/selene/primo/-/tree/master)

```
/* Note! Simplifié, sans certaines initialisations, vérifications d'erreurs, et nettoyages de mémoire. */
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
