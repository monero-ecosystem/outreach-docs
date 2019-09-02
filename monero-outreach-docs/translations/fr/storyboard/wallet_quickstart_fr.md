# Portefeuille Monero, démarrage rapide
*22/04/2019*  
Almutasim  
_**Les portefeuilles impliquent l'une des décisions les plus importantes que doivent prendre les utilisateurs.**_

Un portefeuille logiciel Monero est un programme permettant de stocker, envoyer et recevoir des Monero. Il vous donne le contrôle absolu sur vos Monero en toute confidentialité et sans intermédiaire. Personne ne peut connaître ou modifier l'ensemble des détails de vos transactions, à moins que vous n'ayez décidé de partager vos clefs de lecture à des fins d'audit, ce qui est l'essence même de l'expérience Monero.

Pour faire l'expérience de ce pouvoir, vous devrez choisir un portefeuille. L'aspect le plus critique de tout portefeuille réside dans sa crédibilité. Seuls les portefeuilles recommandés par la communauté (et par le site [getmonero.org](https://getmonero.org/fr/)) sont mentionnés dans cet article. Ensuite, vous voudrez choisir un portefeuille compatible avec votre environnement préféré - iPhone, Android ou ordinateur. Enfin, vous devrez choisir un portefeuille qui répond à vos besoins de confidentialité. Cet article vous guidera sur ce point.

Certains portefeuilles fonctionnent en utilisant leur propre copie de la chaîne de blocs de Monero. On appelle également cela faire fonctionner un nœud complet. Cela vous permet de contrôler la rapidité de vos transactions. Bien que vous puissiez vous appuyer sur un nœud distant sans risquer de perdre vos Monero, vous dépendez alors de la disponibilité du nœud distant (vous serez toujours en mesure de recevoir des Monero, mais vous pourriez ne pas pouvoir en envoyer). Un autre atout du fonctionnement de votre propre nœud complet réside dans la fierté de contribuer au réseau Monero. Les nœuds complets intègres rendent Monero plus fort. Apprenez-en plus ici : [monero.how/how-to-run-monero-node](https://www.monero.how/how-to-run-monero-node).

S'appuyer sur des nœuds distant, au contraire, permet (en utilisant ce qui est communément appelé un portefeuille léger) de s'affranchir des ressources de stockage nécessaires à la chaîne de blocs Monero. La chaîne de blocs (complète) fait plus de 75Go (28/07/2019) et continue de grossir. De nombreux portefeuilles s'appuyant sur des nœuds complets distants utilisent également moins de puissance de calcul et de bande passante. Si ces ressources sont limitées sur votre appareil, un portefeuille léger pourrait être préférable. Cela sera presque toujours le cas pour un portefeuille fonctionnant sur Smartphone.

Il y a deux types de portefeuilles légers : à protection ou à partage de clef de lecture. Les portefeuilles légers à protection de clef gardent vos clefs de lecture confidentielles, et doivent donc télécharger la chaîne de blocs, ou du moins les portions plus récentes que la date de création du portefeuille, pour pouvoir déterminer le solde du portefeuille. Les portefeuilles légers à partage de clef, par opposition, partagent vos clefs de lecture avec le serveur exécutant le nœud distant pour calculer le solde du portefeuille depuis celui-ci. Ces portefeuilles performants sont parfois appelés applications de portefeuilles. Le partage de vos clefs de lecture amoindrit la confidentialité si le serveur exécutant le nœud distant et connaissant les clefs de lecture n'est pas fiable car il permet l'observation des transactions entrantes. Remarquez, cependant, que des propriétaires de portefeuilles partagent parfois leurs clefs de lecture pour des besoins d'audit (elles ne permettent pas de transférer des Monero).

Pour une sécurité maximale (y compris en cas de compromission de votre appareil principal par un malware) des portefeuilles matériels spécialisés peuvent être utilisés. Les portefeuilles matériels sont de petits appareils électroniques interactifs qui stockent vos clefs privées et communiquent avec le logiciel sur l'appareil principal en n'utilisant que des informations publiques. Les portefeuilles matériels apportent une sécurité accrue pour un prix moyen entre 50€ et 150€.

Donc, en gardant tout cela à l'esprit, considérez les options suivantes : Si vous voulez faire fonctionner votre propre nœud complet, les portefeuilles GUI ou CLI officiels sont de bons choix. Le premier propose une interface graphique, alors que le second propose une interface textuelle. Les deux peuvent être configurés soit pour faire fonctionner un nœud complet, soit pour se connecter à un nœud distant avec une confidentialité accrue. Ils peuvent être téléchargés depuis [getmonero.org/fr/downloads](https://getmonero.org/fr/downloads/). Pour les appareils Android, Monerujo [monerujo.io](https://www.monerujo.io/fr/), ou pour iOS, Cake Wallet [cakewallet.io](https://cakewallet.io/) sont des portefeuilles légers à protection de clef de lecture recommandés. Si vous préférez un portefeuille léger à partage de clef de lecture, MyMonero [mymonero.com](https://mymonero.com/) basé sur un navigateur Web est recommandé. Edge Wallet [edge.app](https://edge.app/) est une autre option sérieuse de portefeuille léger à partage de clef de lecture, à la fois pour Android et pour iOS.

Lorsque vous choisissez l'un de ces portefeuilles, gardez à l'esprit que la plupart possèdent des fonctionnalités supplémentaires (à l'exception de Edge Wallet) dans le sens où ils peuvent être configurés pour se connecter soit sur un nœud distant tiers ou sur votre propre serveur exécutant un nœud. Ceci est illustré dans le tableau.

## Portefeuilles officiels

+ [getmonero.org/fr/downloads](https://www.getmonero.org/fr/downloads)
Si vous voulez faire fonctionner un nœud complet, les portefeuilles GUI ou CLI officiels sont de bon choix. Le premier propose une interface graphique, alors que le second propose une interface textuelle.

## Porte mobiles

+ [cakewallet.io](https://cakewallet.io/)  
Cake Wallet, un portefeuille léger à protection de clef de lecture, est disponible pour les appareils iOS.

+ [monerujo.io](https://www.monerujo.io/fr/)  
Monerujo, un portefeuille léger à protection de clef de lecture, est disponible pour les appareils Android.

+ [edge.app](https://edge.app/)  
Edge Wallet est disponible à la fois pour Android et pour iOS. C'est un portefeuille léger à partage de clef de lecture.

## Portefeuilles en ligne *(Optimisés pour le confort)*

+ [mymonero.com](https://mymonero.com/)  
MyMonero est un portefeuille léger basé sur navigateur Web. Il est également disponible sous la forme d'une application iOS ou Windows.

## Portefeuilles matériels *(Optimisés pour la sécurité)*

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)  
Ledger est un appareil hautement sécurisé qui conserve votre phrase mnémonique.
Non applicable

+ [trezor.io](https://trezor.io/)  
Trezor est une alternative d'appareil hautement sécurisé qui conserve votre phrase mnémonique.

En tant que portefeuille matériel fournissant une sécurité avancée pour le stockage et la transmission de Monero même en cas de compromission de l'appareil principal, Ledger, [ledger.com](https://shop.ledger.com/?r=92d74dc2847a) et Trezor, [trezor.io](https://trezor.io/), sont tous deux bien considérés.

Vous appuyer sur vos préférences de ressources allouées et de confidentialité pour guider votre choix maximisera votre expérience Monero. La richesses des options de portefeuille Monero (d'une rapide application MyMonero à un nœud complet faisant autorité couplé à un portefeuille matériel Ledger ou Trezor) permet à tous les utilisateurs de trouver avec Monero la solution qui leur correspond.

Pour en savoir plus : [medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
