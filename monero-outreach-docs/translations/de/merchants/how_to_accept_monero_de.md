# Wie man Monero akzeptiert

Wenn Du in imstande bist, eine App zu installieren, dann besitzt du die notwendigen Fähigkeiten, um Monero (XMR) in Deinem Geschäft akzeptieren zu können. Dieser Leitfaden erklärt die verbreitetsten Möglichkeiten, wie Händler Monero annehmen, und wie Du damit beginnen und darauf aufbauen kannst.

Zunächst gibt es keine spezielle Art von Monero-Händlerkonto - Du benötigst lediglich eine normale Wallet und eine Adresse, um zu starten. Es wird empfohlen, eine separate Adresse für geschäftliche Transaktionen einzurichten, aus den gleichen Gründen, wie es empfohlen wird, getrennte Geschäfts- und Privatkonten zu haben. Du kannst die gleiche Wallet-Software verwenden, aber eine eigene Adresse für das Geschäft hilft, die Konten zu organisieren.

Wenn Du nicht bereits eine Monero-Wallet/Adresse hast, solltest Du diese zuerst erstellen. Die offiziellen Monero GUI/CLI-Wallets von [getmonero.org/downloads](https://www.getmonero.org/downloads/) werden immer empfohlen. Außerdem wird in dieser Anleitung auf mobile Wallets verwiesen und Du kannst weitere Informationen darüber auf unserer Seite [Einrichtung der Monero-Wallet](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html) finden.

### _Die Anatomie einer Monero-Transaktion_

Monero-Transaktionen durchlaufen die nachfolgenden Schritte. Es ist nicht notwendig, die technischen Aspekte davon vollständig zu verstehen, aber als Händler solltest Du über ein Grundverständnis dieser Schritte verfügen, um darüber entscheiden zu können, welche Kompromisse für Dich richtig sind.

1. **Einkauf** - Nachdem Du die Kosten für den Einkauf Deines Kunden in lokaler Fiatwährung errechnet und ggf. die Umsatzsteuer hinzugefügt hast, muss der entsprechende Betrag in XMR berechnet werden.
2. **Zahlung** - Der Kunde scannt Deinen QR-Code, um Dich in XMR zu bezahlen. Die Monero-Transaktionsgebühr wird vom Kunden bezahlt und zum Zeitpunkt der Transaktion berechnet.
3. **Transaktionspool** - Innerhalb einer Sekunde wird die Transaktion dem Monero-Netzwerk mitgeteilt und in den Transaktionspool, auch Mempool genannt, gelegt. Du kannst die Existenz Deiner Transaktion im Mempool überprüfen z. B. unter xmrchain.net/txpool.
4. **Bestätigung** - Innerhalb von 4 Minuten wird die Transaktion in der Regel in einem Block auf der Blockchain sein und Du kannst darauf vertrauen, dass sie gültig ist. Die Zahlung wird nun in Deiner Wallet als gesperrtes Guthaben erscheinen. Deine Transaktion wird durch 9 weitere Blöcke bestätigt, bevor sie freigegeben wird und nicht mehr rückgängig gemacht werden kann.

In der Regel prüft Deine Wallet alle 90 Sekunden, ob neue Transaktionen eingetroffen sind, dabei kann es jedoch zu Verzögerungen kommen. Abhängig davon, wann Deine Wallet auf neue Transaktionen prüft und wie schnell Deine Transaktion in einen neuen Block gelangt, beträgt die tatsächliche Wartezeit, bevor sie in Deiner Wallet auftaucht, zwischen 4-12 Minuten. Für einen genaueren Blick auf den Monero-Transaktionsprozess und die durchschnittliche Dauer besuche [monero.how/how-long-do-monero-transactions-take](https://www.monero.how/how-long-do-monero-transactions-take).

Wenn eine Wartezeit von 4-12 Minuten für Dein Unternehmen nicht praktikabel ist, kannst Du eine Transaktion ohne Bestätigung in einer Sekunde annehmen. Anstatt auf die erste Bestätigung zu warten, schaust Du in den Transaktionspool, um zu prüfen, ob die Transaktion darin existiert. Es besteht ein Risiko, weil die Transaktion noch nicht bestätigt wurde, aber ein Angriff mit doppelten Ausgaben ist unwahrscheinlich, wenn die Person vor Dir steht. Bei kleineren Einzelhandelstransaktionen ist der Vorteil, die Transaktion in einer Sekunde abzuschließen, ein geringes Risiko wert, und wenn sich etwas für Dich nicht richtig anfühlt, kannst Du Dich von Fall zu Fall immer noch umentscheiden und die erste Bestätigung abwarten.

### _Transaktionen identifizieren_

Eine Sache, die offensichtlich wird, wenn Du anfängst, Monero zu akzeptieren ist, dass Du nicht automatisch die Adresse des Absenders kennst, weil Transaktionen grundsätzlich privat sind. Abhängig von Deinem Geschäft könnte die Verknüpfung der Transaktion und der Zahlung keine große oder eine wirklich große Sache sein. Das hängt von Dir ab, die gute Nachricht ist, dass es mehrere einfache Techniken gibt, die Dir dabei helfen, Deine XMR-Zahlungen zuordnen zu können.

Die erste ist einfach, mach Dir eine Notiz. Wenn Du mit einem relativ geringen Volumen an Transaktionen zu tun hast, kannst Du einfach Deine Rechnungs- oder Transaktionsnummer als Notiz in Deiner Wallet hinzufügen, wenn Du XMR erhältst. Alternativ kannst Du die Monero-Transaktions-ID in Deinem Point-of-Sale-System (POS) oder Deiner Buchhaltungssoftware notieren.

Wenn Du aber unbedingt die Zahlung eines Kunden mit einer Transaktion verknüpfen musst, ist die Verwendung von Moneros Subadressen die Antwort. Eine Subadresse ist eine Adresse zur einmaligen Verwendung, und da sie kostenlos sind und Du so viele erstellen kannst wie Du möchtest, kannst Du jedem Kunden eine eindeutige Subadresse geben, um jede Zahlung zuordnen zu können. Diese Funktion ermöglicht es dir außerdem, Deine Hauptadresse privat zu halten.

### _Multisig-Transaktionen_

Multisignatur-Transaktionen erfordern die Freigabe durch mehrere Beteiligte, bevor sie dem Netzwerk bekannt gegeben werden können. Du kannst zum Beispiel eine Transaktion so einrichten, dass das Guthaben erst freigegeben wird, wenn sowohl der Käufer als auch der Verkäufer zustimmen. Wir werden in diesem Text nicht näher auf Multisig eingehen, unter [getmonero.org/resources/user-guides/multisig-messaging-system.html](https://www.getmonero.org/resources/user-guides/multisig-messaging-system.html) kannst du jedoch mehr darüber erfahren.

### _Die LeMonero Enterprises, LLC_

Mit dem Überblick darüber, wie eine Monero-Transaktion funktioniert, kannst Du dieses Wissen mit realen Anwendungsbeispielen auf das fiktive Unternehmen LeMonero Enterprises, LLC anwenden. Es ist so eine "vom Tellerwäscher zum Millionär"-Geschichte der Monero-Adoption und -Integration, bei der wir Limonade verkaufen und unsere Kunden auf drei verschiedene Arten in Monero bezahlen werden, während das Unternehmen weiter wächst.

In all diesen Beispielen nehmen wir an, dass wir unsere Limonade in lokaler Fiatwährung für 1 € verkaufen. Unsere Buchhaltung und unsere Steuerlast sind ebenfalls in Fiatgeld zu zahlen. Die genauen Konditionen hängen davon ab, wo Du lebst und wie Dein Geschäft reguliert ist.

### _Der LeMonero Stand_

In unserem Limonadenstand haben wir eine einfache Geldkassette und ein Notizbuch, um jeden Verkauf aufzuzeichnen, wie es auf Bauernmärkten, Festivals, Pop-up-Veranstaltungen des Einzelhandel und auf Trödelmärkten üblich ist, wo die Einrichtung eingeschränkt ist. Die gute Nachricht ist, dass die Annahme von Monero für diese Art von einfachen Transaktionen nur ein Smartphone erfordert.

Bei Zahlungen in Monero beginnt die Transaktion genauso wie mit Fiatgeld. Du bereitest die Limonade zu, ermittelst die Summe und erfasst die Transaktion in Deinem Notizbuch entsprechend Deiner buchhalterischen Pflichten.

Ein Betrag von 1,00 € wird unmittelbar vor der Zahlung in XMR umgerechnet. Der Wechselkurs ändert sich ständig. Zum Zeitpunkt der Übersetzung dieses Artikels kostete 1 XMR 210,08 €, also würde eine 1,00 € Limonade 0,0045235 XMR kosten.

Der Kunde muss bei der Zahlung mit dem Smartphone Deine Adresse auf sein Telefon bekommen, um Dir die 0,0045235 XMR zu senden. Das Kopieren und Einfügen oder das Abtippen der Adresse funktioniert auch, doch normalerweise werden Monero-Adressen bequem mit QR-Codes gescannt. Der QR-Code enthält Deine Monero-Adresse in einer Form, die die Wallet des Kunden einlesen kann. Deine Wallet generiert diese für Dich automatisch, wenn Du auf "Empfangen" klickst und Du kannst Deinen Bildschirm so drehen, dass der Kunde den QR-Code scannen kann. Alternativ kannst Du einen QR-Code ausdrucken und versenden und Deine Wallet nur verwenden, um die Transaktion zu bestätigen.

Sobald der Kunde Dir die XMR schickt, wird die Transaktion an das Monero-Netzwerk gesendet. Das Guthaben erscheint in 4-12 Minuten nach der ersten Bestätigung in Deiner Wallet.

Wir müssen nur selten einen Kunden warten lassen, da wir den Limonaden-Kunden, vor allem den Stammkunden, Vertrauen entgegenbringen können. Jemandem, der eine große Bestellung hat, erklären wir vielleicht einfach, dass es ein paar Minuten dauern wird.

### _Das LeMonero Café_

Mit harter Arbeit ist unser kleiner Limonadenstand zu einem Limonaden-Café gewachsen. Wir sind jetzt ein unabhängiger Einzelhändler mit Ladengeschäft. Zusätzlich zu Bargeld und Monero wie zuvor akzeptiert das Café Kredit-/Debitkarten und hat ein POS-System, um Transaktionen aufzuzeichnen und das Inventar zu verwalten, anstatt wie zuvor nur ein Notizbuch zu verwenden.

LeMonero hat höhere Betriebskosten und wir können es uns nicht leisten, die XMR nur in unserer Wallet zu halten - wir müssen einige XMR in Fiatgeld umwandeln, um Rechnungen bezahlen zu können. Obwohl wir uns dazu entscheiden haben, diese Fiatzahlungen manuell durchzuführen, wenn für uns am vorteilhaftesten ist. Wir brauchen aber immer noch einen Zahlungsabwickler, damit die Kunden schnell und einfach bezahlen können.

Die meisten Geschäftsinhaber sind mit Kredit-/Debit-Zahlungsabwicklern vertraut, Drittanbietern, die Dir das Terminal vermieten und Dich in ihr Netzwerk aufnehmen und die Gebühren pro Transaktion und pro Monat berechnen. Ein Monero-Zahlungsabwickler kann genau so funktionieren, oder Du kannst mit ein wenig Software Dein eigener Zahlungsabwickler sein und überhaupt keine Transaktionsgebühren mehr bezahlen.

Da die Software von Monero Open-Source ist, kannst Du Dein eigenes Zahlungsgateway erstellen (wie cool ist das denn), aber Monero Integrationen hat die Arbeit bereits für Dich erledigt und Bibliotheken und Plug-ins erstellt, die alle schweren Aufgaben übernehmen [github.com/monero-integrations](https://github.com/monero-integrations).

Alternativ bietet ein Monero-Zahlungsabwickler eines Drittanbieters Softwarepakete, Apps und Schnittstellen, die die Einrichtung vereinfachen. Sie verfügen auch über Schnittstellen und Werkzeuge, mit denen Du Dein Konto verwalten kannst, sowie über Kunden- und Techniksupport. Sieh Dir unseren [Leitfaden für Monero-Zahlungsabwickler](https://www.monerooutreach.org/merchants/monero-payment-processor-guide.html) an, um zu entscheiden, welches System das richtige für Dich ist.

### _LeMonero.com_

Unser Limonaden-Café macht die Leute verrückt nach mehr und wir haben uns um einen Online-Shop und weiteren Filialen vergrößert. Die gute Nachricht ist, dass wir unseren Zahlungsabwickler nicht wechseln müssen, wir müssen ihn nur mehr nutzen.

Die Integration eines Abrechnungssystem in unseren Online-Shop ist im Vergleich zu physischen Transaktionen in Echtzeit einfach. Egal, ob Sie einen Open-Source-Zahlungsabwickler oder einen Drittanbieterdienst verwenden, Plug-ins für WooCommerce, Shopify usw. sind verfügbar und einfach zu installieren.

Wir können jetzt eine automatische Abrechnung in Fiatgeld haben. Als Limonadenstand haben wir unsere XMR-Zahlungen behalten. Als wir nur ein Café betrieben, haben wir davon einige liquidiert, wenn der Wechselkurs günstig war. Aber unsere Cashflow-Bedürfnisse haben sich verändert. Wir brauchen einen vorhersehbaren XMR-zu-Fiat Wechselkurs, auch wenn das zusätzliche Gebühren erfordert und der Verkauf zu einem ungünstigen Zeitpunkt erfolgt.

Die meisten Drittanbieter von Zahlungssystemen bieten eine automatische Fiat-Konvertierung mit Deiner Börse gegen eine Gebühr an. Je nach Anbieter können zusätzliche Transaktions- oder Abhebungsgebühren anfallen, aber der Komfort kann es wert sein.

Mit einem Open-Source-Zahlungsanbieter steht es Dir frei, Deine eigene Lösung zu entwickeln, indem Du die API Deiner bevorzugten Börse mit monero-wallet-rpc-Aufrufen verwendest. Dies würde den Rahmen dieses Tutorials sprengen, aber Du kannst unter [getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/resources/developer-guides/wallet-rpc.html) mehr darüber erfahren.

### _Mehr erfahren_

- Wie man Monero mit den offiziellen Monero-Wallets akzeptiert: [getmonero.org/get-started/accepting](https://www.getmonero.org/get-started/accepting/)
- [Monero Händler FAQs](https://www.monerooutreach.org/merchants/monero-merchant-faqs.html)
- Monero Multisignaturen erklärt: [hackernoon.com/monero-multisignatures-explained...](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
- Potenzielle Risiken bei der Akzeptanz von Transaktionen ohne Bestätigungen: [reddit.com/r/Monero/.../potential_risks_of_accepting_zero_confirmation](https://www.reddit.com/r/Monero/comments/7s937y/potential_risks_of_accepting_zero_confirmation/)

Illustrationen von:

