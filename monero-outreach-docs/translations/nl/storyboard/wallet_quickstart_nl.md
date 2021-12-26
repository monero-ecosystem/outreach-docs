# Monero Wallet Quickstart
*22/04/19*  
Almutasim  
_**Wallets vormen één van de belangrijkste beslissingen omtrent beveiliging voor de gebruiker.**_

Een Monero software wallet is een programma om Monero te bewaren, te zenden en te ontvangen. Het geeft je volledige controle over je Monero, met privacy, en zonder tussenpersoon. Niemand kan alle details te weten komen noch de transacties veranderen, tenzij je kiest je leessleutel te delen voor audits. Deze kracht is de essentie van de Monero-ervaring.

Om deze kracht te ervaren zal je een wallet moeten kiezen. Het eerste kritische aspect van eender welke wallet is de betrouwbaarheid. Enkel wallets aanbevolen door de gemeenschap (en de [getmonero.org](https://getmonero.org/) website) worden in dit artikel vermeld. Vervolgens hoort de wallet te passen bij je computer: iPhone, Android-telefoon, of laptop/desktop. Tenslotte hoort de gekozen wallet overeen te stemmen met je eigen privacybehoefte. Dit artikel zal je hierbij begeleiden.

Sommige wallets werken met een eigen kopie van Monero's blockchain. Dit wordt ook het runnen van een "full node" genoemd. Zo heb je controle over de timing van je transacties. Hoewel je kan vertrouwen op een "remote node" zonder extra risico je Monero te verliezen, hang je dan af van de beschikbaarheid van zulke node-op-afstand: je kan altijd ontvangen, maar mogelijk niet altijd verzenden. Een ander voordeel van je eigen full node te runnen is de eer bij te dragen aan het Moneronetwerk. Eerlijke full nodes maken Monero sterker. Voor meer informatie: [monero.how/how-to-run-monero-node](https://www.monero.how/how-to-run-monero-node).

De voordelen om daarentegen te vertrouwen op een remote node — ook wel "light wallet" of soms "lightweight wallet" genoemd — zijn onder meer dat er geen opslagcapaciteit nodig is voor Monero's blockchain. De blockchain is groter dan 50GB (in "unpruned" of ongesnoeide vorm) en groeit steeds. Vele wallets die remote nodes gebruiken, vragen ook minder rekenkracht en netwerkbandbreedte. Als deze middelen beperkt zijn op je computer, dan heeft misschien een light wallet de voorkeur. Dit zal bijna altijd het geval zijn voor een wallet op een smartphone.

Er zijn twee types light wallet: de leessleutel wordt of beschermd, of gedeeld. De leessleutelbeschermende light wallets houden je leessleutel volledig privé, en als gevolg moet je de blockchain downloaden (of althans het gedeelte gecreëerd later dan de aanmaakdatum van de wallet) om de Monero wallet-balans te berekenen. Leessleuteldelende light wallets delen daarentegen de leessleutel met de server waarop de remote node runt om op deze server de inkomende balans van de wallet te berekenen. Deze efficiënte wallets worden soms wallet apps genoemd. Het delen van de leessleutel vermindert privacy als de server waarop de leessleutellezende remote node runt niet vertrouwd is, want het laat observatie toe van de inkomende transacties. Merk wel op dat soms wallet-dragers sowieso de leessleutel delen vanwege auditing. Dit laat geen transacties toe. 

Voor maximale beveiliging — veiligheid zelfs als malware je primaire apparaat aantast — kan je hardware wallets gebruiken. Dit zijn kleine interactieve elektronische apparaten die je privésleutels opslaan en communiceren met de software op het primaire apparaat, met gebruik van alleen publieke informatie. Hardware wallets geven extra beveiliging voor een prijs van ongeveer $50-150.

Met dit alles in het achterhoofd, overweeg de volgende opties. Als je je eigen full node wilt runnen, dan is de officiële Monero GUI of CLI wallet een goede keuze. De GUI wallet biedt een grafische gebruikersinterface, de CLI wallet presenteert zich als tekst. Beide kunnen ingesteld worden of als full node, of om verbinding (met verbeterde privacy) te maken met een remote node. Deze kunnen worden gedownload van [getmonero.org/downloads](https://getmonero.org/downloads/). Voor je Android-telefoon zijn Monerujo [(monerujo.io)](https://www.monerujo.io/), of voor iOS, Cake Wallet [(cakewallet.io)](https://cakewallet.io/) de aanbevolen leessleutelbeschermende light wallets. Wil je een leessleuteldelende light wallet, dan is de browsergebaseerde MyMonero [(mymonero.com)](https://mymonero.com/) aanbevolen. Edge Wallet [(edge.app)](https://edge.app/) is een ander degelijk alternatief als leessleuteldelende light wallet voor zowel Android als iOS.

Als je je keuze maakt, bedenk dan dat de meeste wallets je de extra mogelijkheid geven (op Edge Wallet na) om of te verbinden met een remote server van derden, of met een server die je zelf runt. Zie tabel voor een overzicht.

## Officiële Wallets

+ [getmonero.org/downloads](https://www.getmonero.org/downloads)  
Als je een full node wil runnen is de officiële Monero GUI of CLI wallet een goede keuze. De eerste biedt een grafische gebruikersinterface, de laatste een tekstinterface.

## Mobiele Wallets

+ [cakewallet.io](https://cakewallet.io/)  
Cake Wallet, een leessleutelbeschermende light wallet, is beschikbaar voor iOS-apparaten.

+ [monerujo.io](https://www.monerujo.io/)  
Monerujo, een leessleutelbeschermende light wallet, is beschikbaar voor Android-apparaten.

+ [edge.app](https://edge.app/)  
Edge Wallet is beschikbaar voor zowel Android als iOS. Het is een leessleuteldelende light wallet.

## Web Wallets *(gericht op gebruiksgemak)*

+ [mymonero.com](https://mymonero.com/)  
MyMonero is een browsergebaseerde light wallet. Het is ook beschikbaar als iOS-app en als desktopapp.

## Hardware Wallets *(gericht op veiligheid)*

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)  
Ledger is een zwaar beveiligd apparaat dat je hersteltekst opslaat.

+ [trezor.io](https://trezor.io/)  
Trezor is een alternatief zwaar beveiligd apparaat dat je hersteltekst opslaat.

Zowel Ledger [(ledger.com)](https://shop.ledger.com/?r=92d74dc2847a) als Trezor [(trezor.io)](https://trezor.io/) staat hoog in aanzien als hardware wallet, wallets die voor zowel opslag als transacties extra beveiliging bieden, zelfs als het primaire apparaat gecompromitteerd is. (Merk op dat Ledger nu met andere wallets kan werken, terwijl Trezor nog werkt aan de ondersteuning van andere wallets.)

Als je je keuze tussen wallets laat afhangen van je voorkeur van middelen en privacy, staat je een optimale Monero-ervaring te wachten. Monero's talloze mogelijkheden aan wallets — van een vlugge Mymonero app tot een majestueuze Monero CLI wallet met full node en gecombineerd met een Ledger of Trezor — zijn de gebruikers van Monero in hun diverse behoeftes voorzien.

Voor meer informatie: [medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
