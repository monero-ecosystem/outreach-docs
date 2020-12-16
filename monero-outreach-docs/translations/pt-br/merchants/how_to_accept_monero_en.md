# Como aceitar Monero

Se você consegue instalar um aplicativo, você estará pronto para aceitar Monero (XMR) no seu negócio. Esse guia explica as formas mais comuns que comerciantes usam para aceitar Monero e como começar sem dor de cabeça a se desenvolver e a crescer o seu negócio.

Primeiramente não há um tipo especial de conta comercial Monero - você apenas precisa de uma carteira e um endereço normal para começar. É recomendado que você crie um endereço separado para transações comerciais pela mesma razão de que é cômodo e seguro ter contas pessoais e de negócios separadas. Você pode usar o mesmo software para a carteira, mas ter endereços dedicados para negócios irá ajudar manter as contas organizadas.

Se você ainda não tem uma carteira/endereço Monero então é melhor criar uma primeiro. As carteiras Monero GUI/CLI oficiais de [getmonero.org/downloads](https://web.getmonero.org/pt-br/downloads/index.html) são sempre recomendadas. Além disso, esse guia irá indicar carteiras mobile e você pode achar informação sobre elas na página de [Configuração da Carteira Monero](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html). 

### _A anatomia de uma transação Monero_

Transações Monero seguem os seguintes passos. Não é necessário entender os aspectos técnicos disso, mas como um comerciante, você precisa ter um conhecimento básico dos passos para ser capaz de decidir quais tradeoffs são melhores para você.

    1. **Compra** - Depois de adicionar a compra do cliente em moeda local e aplicar os impostos se necessário, você simplesmente precisa calcular o valor correspondente em XMR.
    2. **Pagamento** - O cliente escaneia seu QR code para pagar em XMR. A taxa de transação é paga pelo cliente e calculado durante o processo de pagamento.	
    3. **Pool de Transações** - Dentro de um segundo, a transação é anunciada para a rede Monero e colocada no pool de transações, também chamada de mempool (pool de memória). Você pode verificar a existência de sua transação no mempool, um exemplo pode ser visto aqui: xmrchain.net/txpool
    4. **Confirmação** - Dentro de 4 minutos, a transação irá geralmente estar em um bloco da blockchain e você pode ter confiança de que ela é válida. O pagamento irá aparecer em sua carteira como fundos bloqueados. Sua transação será confirmada por mais 9 blocos antes de ser desbloqueada e virtualmente impossível de se reverter.
    
Pode haver um lag na verificação de novas transações, geralmente 90 segundos. Portanto, dependendo de quando sua carteira verifica se há novas transações e com que rapidez sua transação entra em blocos minerados, o tempo real esperado antes que ela apareça em sua carteira é de 4 a 12 minutos. Para uma análise mais aprofundada do processo de transação do Monero e da duração média, visite [monero.how/how-long-do-monero-transactions-take](https://www.monero.how/how-long-do-monero-transactions-take).

Se uma espera de 4 a 12 minutos for inviável para seu negócio, você pode fazer uma transação de zero confirmações em um segundo. Em vez de esperar pela primeira confirmação, você examina o pool de transações para verificar se a transação existe. Há um risco porque a transação não foi confirmada, mas um ataque de gasto duplo é improvável se a pessoa estiver na sua frente. Para transações de varejo de menor escala, o benefício de concluir a transação em um segundo geralmente vale o baixo risco e se algo não estiver parecendo certo para você, você sempre pode escolher aguardar a primeira confirmação dependendo do caso.

### _Identificando Transações_

Uma coisa que se torna óbvia quando você começa a aceitar Monero é que você não sabe o endereço do remetente porque as transações são privadas. Dependendo de sua empresa, vincular a transação ao pagamento pode não ser grande coisa ou pode ser realmente um grande problema. Dependerá de você, a boa notícia é que existem várias técnicas simples para ajudá-lo a identificar seus pagamentos XMR.

A primeira é simples, faça uma anotação. Se estiver lidando com um volume bastante baixo de transações, você pode simplesmente adicionar sua fatura ou número de transação como uma nota em sua carteira quando você receber fundos. Como alternativa, você pode anotar a ID da transação Monero em seu sistema de ponto de venda (POS) ou software de contabilidade.

Mas quando é absolutamente necessário vincular o pagamento de um cliente a uma transação, usar os subendereços do Monero é a resposta. Um subendereço é um endereço descartável e, como são gratuitos e você pode criar quantos quiser, pode atribuir um subendereço exclusivo a cada cliente para que possa controlar cada pagamento. Esse recurso também é útil se você deseja manter seu endereço principal privado.

### _Transações de Assinatura Múltipla_

As transações com várias assinaturas exigem assinatura com várias partes antes de serem anunciadas na rede. Por exemplo, você pode organizar uma transação de forma que os fundos não sejam liberados até que o comprador e o vendedor concordem. Não nos aprofundaremos em vários tipos de assinaturas nesse artigo, mas visite [getmonero.org/resources/user-guides/multisig-messaging-system.html](https://www.getmonero.org/pt-br/resources/user-guides/multisig-messaging-system.html) para obter mais informações.

### _LeMonero Enterprises, LLC_

Com essa visão geral de como funciona uma transação Monero, vamos aplicá-la a alguns exemplos do mundo real usando nossa empresa fictícia LeMonero Enterprises, LLC. É uma história de ascenção da adoção e integração do Monero, onde venderemos limonada e nossos clientes pagarão em Monero de três maneiras diferentes conforme crescemos.

Em todos esses exemplos, digamos que estamos vendendo nossa limonada em moeda fiduciária local por $ 1. Nossa contabilidade e carga tributária também são fiduciárias. Suas condições dependerão de onde você mora e de como seu tipo de negócio é regulamentado.

### _Barraca de LeMonero_

Em nossa barraca de limonada, temos uma caixa de dinheiro simples e um caderno para registrar cada venda, como é comum em feiras de fazendeiros, festivais, eventos de varejo e vendas de artesanato comunitário, onde a escala do negócio é limitada. A boa notícia é que para aceitar o Monero para esse tipo de transação simples, basta um smartphone.

Para pagamentos em Monero, a transação começa da mesma forma que fiat. Você prepara a limonada, calcula o total e registra a transação em seu caderno de acordo com suas necessidades contábeis.

Um total de $ 1,00 é convertido em XMR imediatamente antes do pagamento. A taxa de câmbio está mudando constantemente. No momento em que este artigo foi escrito, 1 XMR custava $ 61,40 USD, então uma limonada de $ 1,00 custaria 0,0162 XMR.

O cliente precisa obter o seu endereço no telefone para pagar à você 0,0162 XMR. Copiar e colar texto às vezes funciona, mas geralmente os endereços Monero podem ser trocados por códigos QR. O código QR contém seu endereço Monero em um formato que a carteira do cliente pode digitalizar. Sua carteira gera isso para você quando você clica em ‘receber’ e você pode virar a tela da carteira para que o cliente a escaneie. Como alternativa, você pode imprimir e postar um código QR e, em seguida, apenas usar sua carteira para confirmar a transação.

Assim que o cliente lhe envia o XMR, a transação é transmitida para a rede Monero. Os fundos aparecerão em sua carteira entre 4 e 12 minutos após a primeira confirmação.

No entanto, raramente temos que manter um cliente esperando, pois há a confiança nos clientes, especialmente os clientes regulares. Para alguém novo com um pedido grande, podemos explicar que isso levará alguns minutos.

### _Lanchonete LeMonero_

Com muito trabalho, nossa pequena barraca de limonada se transformou em uma lanchonete. Agora somos um varejista independente de tijolo e argamassa. Assim como antes, aceitamos dinheiro e Monero, mas agora a lanchonete aceita cartões de crédito/débito e possui sistema de POS (terminal de pagamento, similar a um caixa eletrônico) para registrar transações e gerenciar estoque em vez de um notebook.

LeMonero tem despesas gerais mais altas e não podemos apenas reter os pagamentos de XMR - precisamos converter um pouco de XMR em dinheiro fiduciário para pagar as contas, embora optemos por liquidar manualmente em fiat quando for mais vantajoso. Ainda precisamos de um processador de pagamento, dessa forma, os check-outs dos clientes serão rápidos e fáceis.

A maioria dos proprietários de empresas está familiarizada com processadores de pagamento de crédito/débito, terceiros que alugam o terminal de você, o colocam em sua rede e cobram taxas de transação por mês. Um processador de pagamentos Monero pode funcionar assim ou você pode ser o seu próprio com um pequeno software e não pagar nenhuma taxa de transação.

Como o software Monero é de código aberto, você pode criar seu próprio gateway de pagamento do zero (muito legal isso, né?), mas Monero Integrations já fez o trabalho para você e criou bibliotecas e plug-ins que fazem todo o trabalho pesado em [github.com/monero-integrations](https://github.com/monero-integrations).

Como alternativa, um processador de pagamento Monero de terceiros terá softwares, aplicativos e interfaces que simplificam a configuração. Eles também terão interfaces e ferramentas para você gerenciar sua conta e suporte técnico/ao cliente. Consulte nosso Guia do Processador de Pagamentos Monero para obter ajuda para decidir qual configuração é a certa para você.

### _LeMonero.com_

Nosso lanchonete está deixando as pessoas satisfeitas e animadas, nós acabamos de expandir nossas operações para vendas online e mais lojas físicas. A boa notícia é que não precisamos mudar nosso processador de pagamentos, apenas precisamos usá-lo mais.

A integração do carrinho de compras é fácil em comparação com as transações físicas em tempo real. Esteja você usando um processador de pagamento de código aberto ou serviço de terceiros, plug-ins para WooCommerce, Shopify, etc. estão prontamente disponíveis e são fáceis de instalar.

Agora podemos ter liquidação automática em fiat. Como uma barraca de limonada, retemos nossos pagamentos XMR; quando éramos uma lanchonete, vendíamos algumas moedas quando preço era favorável. Mas nossas necessidades de fluxo de caixa se intensificaram. Precisamos de um XMR previsível para a troca fiduciária, mesmo que isso signifique taxas adicionais ou um momento ruim.

A maioria dos processadores de pagamento de terceiros fornecerá conversão fiduciária automática por uma taxa. Pode haver transação adicional ou taxas de saque dependendo dos provedores, mas a conveniência pode valer a pena.

Com um processador de pagamento de código aberto, você pode desenvolver sua própria solução usando a API de sua exchange preferida com monero-wallet-rpc. Isso está além do escopo deste tutorial, mas você pode encontrar mais informações em [getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/pt-br/resources/developer-guides/wallet-rpc.html).

### _Saiba Mais_

      - Como aceitar Monero com carteiras oficiais Monero: [getmonero.org/get-started/accepting](https://www.getmonero.org/pt-br/get-started/accepting/index.html)
      - [FAQs dos Comerciantes Monero](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
      - Explicando Assinaturas Múltiplas de Monero: [hackernoon.com/monero-multisignatures-explained...](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
      - Riscos Potenciais de Aceitar Transações de Zero Confirmação: [reddit.com/r/Monero/.../potential_risks_of_accepting_zero_confirmation](https://www.reddit.com/r/Monero/comments/7s937y/potential_risks_of_accepting_zero_confirmation/)

Ilustrado por:
