# Comment accepter Monero

Si vous êtes en mesure d'installer une application (app), alors vous serez capable de mettre sur pied le paiement par Monero (XMR) pour votre entreprise. Ce guide explique les manières les plus courantes dont les marchands acceptent les Monero, ainsi que comment démarrer facilement le paiement par XMR d'une manière qui peut suivre la croissance de votre entreprise.

Premièrement, il n'y a pas de compte marchand dédié pour les Monero - tout ce qu'il vous faudra pour commencer est un portefeuille régulier et une adresse. Il est fortement recommandé de garder des adresses distinctes pour vos transactions d'affaires, pour les mêmes raisons qu'il est recommandé d'avoir des comptes bancaires différents pour les transactions personnelles et les transactions d'affaires. Vous pouvez utiliser le même logiciel de gestion du portefeuille, mais cela aidera votre organisation de séparer les adresses.

Si vous n'avez pas déjà un portefeuille / une adresse Monero, vous devriez en créer dès maintenant. Les portefeuilles GUI/CLI officiels de Monero disponibles sur [getmonero.org/downloads](https://www.getmonero.org/downloads/) sont toujours recommandés. Le guide suivant vous donnera plus d'informations sur les portefeuilles mobiles: [Mis en Place d'un Portefeuille Monero](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html)

### _L'Anatomie d'une Transaction Monero_

Les transactions Monero procèdent par les étapes suivantes. Il n'est pas nécessaire de comprendre les aspects techniques de ce qui suit, mais en tant que marchand, vous devriez comprendre les notions de base afin de savoir quels sont les compromis que vous devrez faire.

1. **Achat** - Après avoir calculé le montant de l'achat et les taxes applicables (normalement dans la dénomination de votre monnaie fiduciaire locale), vous n'avez qu'à calculer le montant correspondant de XMR selon le taux de conversion courant.
2. **Paiement** - Le client capture votre code QR afin de vous payer en XMR. Les frais associés à la transaction en Monero sont assumés par l'émetteur et calculés au moment de la transaction.
3.  **Pool de Transaction** - En l'espace d'une seconde, la transaction est annoncée au réseau Monero et placée dans le pool de transaction, aussi connu sous le nom de mempool. Vous pouvez vérifier l'existence de votre transaction dans le mempool, dont un exemple peut être vu ici: xmrchain.net/txpool.
4. **Confirmation** - Dans un délai de 4 minutes, la transaction sera normalement inscrite sur un bloc de la chaine de blocs et vous pouvez alors être confiant de sa validité. Le paiement apparaîtra désormais dans votre portefeuille sous forme de fonds retenus. Votre transaction sera ensuite confirmée par les 9 prochains blocs avant que les fonds ne soient relâchés. La transaction est alors virtuellement impossible à renverser ou annuler.

Il pourrait y avoir un délai lorsque votre portefeuille recherche une nouvelle transaction effectuée, mais il se limite habituellement à 90 secondes. De cette manière, le délai entre l'exécution de la transaction et son apparition dans votre portefeuille sera de 4 à 12 minutes, tout dépendamment du moment où votre portefeuille initie la recherche pour la transaction et le temps requis pour que la transaction se retrouve sur un bloc miné. Pour un analyse plus approfondi du processus derrière les transactions Monero, visitez [monero.how/how-long-do-monero-transactions-take](https://www.monero.how/how-long-do-monero-transactions-take).

Si un délai de 4 à 12 minutes n'est pas compatible avec votre modèle d'affaire, vous pouvez faire une transaction à zéro confirmations en une seconde. Plutôt que d'attendre pour une première confirmation, vous pouvez consulter le pool de transactions pour vérifier que la transaction existe et y est inscrite. Il y a un risque associé à cette manière de procéder car la transaction n'est pas encore confirmée, mais une attaque de double-dépense est peu probable si la personne est physiquement devant vous. Pour des transactions commerciales de petite taille, l'avantage d'une transaction rapide vaut habituellement ce faible risque. Si quelque chose vous paraît anormal dans la transaction, vous pouvez toujours choisir d'attendre la première confirmation si les circonstances le justifient.

### _Identification des Transactions_

 Il devient rapidement évident, lorsque vous commencez à accepter le paiement en Monero, que vous ne pouvez pas automatiquement connaître l'adresse d'origine des transactions puisque celles-ci sont privées. Tout dépendant de votre domaine d'activité, l'association entre une transaction et un paiement reçu pourrait être critique ou superflue. Il existe plusieurs techniques simples pour vous aider à identifier positivement vos paiements XMR.

 La première est la plus simple: prenez-en note. Si vous faites affaire à un bas volume de transactions, vous pouvez ajouter le numéro de facture ou de transaction comme une note dans votre portefeuille lorsque vous recevez les fonds. Vous pourriez aussi prendre note du numéro d'identifiant (ID) de transaction Monero généré par votre terminal de point de vente ou par votre système comptable.

 Toutefois, si vous devez absolument lier le paiement d'un client à une transaction spécifique, l'utilisation des sous-adresses est la solution à privilégier. Une sous-adresse est une adresse à usage unique, et puisqu'elles sont gratuites et illimitées, vous pouvez générer une sous-adresse pour chaque client afin de suivre chaque paiement. Cette fonctionnalité est également utile pour éviter de divulguer votre adresse principale.

###_Transactions Multisig_

Les transactions multisig requièrent une signature de plusieurs parties avant d'être annoncée au réseau. Par exemple, vous pourriez préparer une transaction où les fonds ne seraient relâchés jusqu'à ce que l'acheteur et le vendeur donnent conjointement leur accord. Sans explorer les détails techniques des transactions multisig ici, vous pouvez trouver plus de renseignements au lien suivant: [getmonero.org/resources/user-guides/multisig-messaging-system.html](https://www.getmonero.org/resources/user-guides/multisig-messaging-system.html)

### _Entreprises LeMonero, LLC_

Forts de ces détails sur le fonctionnement des transactions Monero, examinons à présent un contexte d'utilisation réel par l'entremise d'une entreprise fictive, Entreprises LeMonero LLC. Histoire inspirante d'adoption et d'intégration de Monero, Entreprises LeMonero LLC vend de la limonade et offre à ses clients de payer avec des Monero de trois manières différentes.

Dans tous ces exemples, la limonade est vendue pour 1$ en monnaie fiduciaire locale. La comptabilité, ainsi que la taxation, sont également en monnaie locale. Vos conditions spécifiques varieront selon votre localisation et la règlementation entourant votre secteur d'activité.

### _Kiosque LeMonero_

Notre kiosque fictif possède une caisse et un carnet pour enregistrer les ventes, comme c'est souvent le cas dans les festivals ou les marchés éphémères où l'infrastructure de paiement est limitée. Dans un contexte comme celui-ci, tout ce qu'il vous faut pour accepter un paiement en Monero est un téléphone intelligent (smartphone).

Pour les paiements en Monero, la transaction débute de la même manière qu'avec des monnaies fiduciaires: vous préparez la limonade, calculez le montant dû et enregistrez la transaction dans votre carnet (selon le format qui convient à vos besoins de comptabilité).

Le montant de 1$ est ensuite converti en XMR avant d'initier le paiement. Le taux de change est plutôt variable: au moment d'écrire ces lignes, 1 XMR coûte $278.34 USD, donc une limonade à 1$ coûterait 0.0068 XMR.

Le client doit entrer votre adresse dans leur téléphone pour vous payer le montant de 0.0068 XMR. Les adresses Monero sont habituellement échangés par l'entremise de codes QR, quoique qu'il soit également possible de copier et coller textuellement l'adresse. Le code QR contient votre adresse Monero dans un format que les portefeuilles de vos clients peuvent lire. Votre propre portefeuille génère automatiquement ce code lorsque vous cliquez sur "recevoir", et vous pouvez alors présenter l'écran de votre téléphone à votre client pour qu'il puisse capturer le code QR avec son propre téléphone. Une autre approche consiste à imprimer en format papier le code QR de votre adresse, et utiliser votre portefeuille pour confirmer la transaction.

Dès lors que votre client vous envoie les XMR, la transaction est transmise au réseau Monero. Les fonds apparaîtront dans votre portefeuille entre 4 et 12 minutes suivant la première confirmation.

Dans notre exemple du kiosque de limonade, il serait rarement nécessaire de faire patienter les clients en attendant la confirmation de la transaction: nous pourrions raisonnablement faire confiance aux acheteurs de limonade, surtout les clients réguliers. Pour un client qui inspire moins de confiance, surtout s'il passe une grande commande, il serait probablement opportun de lui expliquer qu'il doit attendre quelques instants, le temps de recevoir la confirmation de transaction.

### _Café LeMonero_

Grâce à notre travail acharné au kiosque de limonade, ce dernier se transforme éventuellement en café. Nous sommes désormais un marchand indépendant avec un emplacement physique. En plus de la monnaie fiduciaire et le Monero, notre café accepte également les cartes débit/crédit et un système de point de vente enregistre les transactions et gère l'inventaire en place de notre carnet.

Les frais d'entretien et de gestion sont plus importants pour le Café LeMonero, et nous devons convertir une partie des paiements XMR en monnaie fiduciaire pour couvrir ces frais - conversion que nous pouvons faire manuellement lorsque le taux est avantageux. Il nous faut toujours un système automatisé pour traiter le paiement afin que les transactions à l'achat demeurent rapides et simples.

La plupart des commerçants sont familiers avec les systèmes de paiement par crédit/débit, où des tiers louent le terminal et vous donnent accès à leur réseau en échange de frais, qui peuvent être fixes et/ou sur une base transactionnelle. Un système de paiement Monero peut fonctionner de cette manière, ou vous pouvez être votre propre système de paiement à l'aide de quelques éléments logiciels - vous ne paierez alors aucun frais.

En opérant sur du code source libre, le logiciel Monero vous habilite à bâtir votre propre portail de paiement. L'équipe de Monero Integrations a par ailleurs déjà fait tout le travail en créant des librairies et des modules qui s'occupent de tous les aspects importants. Vous trouverez leur code ici: [github.com/monero-integrations](https://github.com/monero-integrations).

Sinon, vous pouvez opter pour des systèmes de paiement par Monero développés par des tiers, qui vous fourniront les logiciels, les applications et les interfaces nécessaires pour simplifier au maximum le démarrage. Ils offrent également des interfaces et outils pour vous permettre de gérer votre compte, ainsi que le soutien technique et le service à la clientèle. Allez voir notre Guide des Services de Traitement du Paiement par Monero afin de vous soutenir dans la sélection de votre solution.

### _LeMonero.com_

Notre café fait fureur et nous avons commencé à vendre nos produits en ligne, en plus d'augmenter le nombre d'emplacements physiques. La bonne nouvelle est que nous n'aurons pas besoin de changer de système de paiement, nous n'avons qu'à l'utiliser plus souvent.

L'intégration du panier lors d'achats en ligne est simple: que vous utilisiez un système de paiement à code source libre ou développé par des tiers, des modules pour WooCommerce, Shopify, et autres sont disponibles et faciles à installer.

Nous pouvons maintenant conclure les transactions automatiquement en monnaie fiduciaire. Avec notre kiosque, nous conservions nos paiement XMR; pour le café, nous liquidions une portion des XMR lorsque le taux nous était favorable. Nos besoins d'encaisse et de flux de trésorerie ont désormais augmenté et il nous faut un mécanisme de conversion systématique de XMR en monnaie fiduciaire, même si cela encours des frais supplémentaires ou un taux de conversion moins favorable.

La plupart des systèmes de paiement par des tiers offrent ce mécanisme d'échange en monnaie fiduciaire, service pour lequel ils chargent des frais. Le montant exacte des frais de transaction peut varier selon le fournisseur de service, mais cela peut certainement en valoir la peine pour des raisons pratiques.

Avec un système de paiement à code source libre, vous pouvez développer la solution qui vous convient le mieux en utilisant l'API de vos sites d'échange préférés et des appels monero-wallet-rpc. Ces notions dépassent la portée de ce guide, mais vous pouvez en lire plus ici: [getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/resources/developer-guides/wallet-rpc.html).

### _En Savoir Plus_

- Comment accepter des Monero avec le portefeuille officiel Monero: [getmonero.org/get-started/accepting](https://www.getmonero.org/get-started/accepting/)
- [FAQ Monero pour Marchands](https://www.monerooutreach.org/merchants/monero-merchant-faqs.html)
- Explications des Multisignatures Monero: [hackernoon.com/monero-multisignatures-explained...](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
- Les Risques Associés aux Transactions à Zéro Confirmations: [reddit.com/r/Monero/.../potential_risks_of_accepting_zero_confirmation](https://www.reddit.com/r/Monero/comments/7s937y/potential_risks_of_accepting_zero_confirmation/)

Illustrations Par:
