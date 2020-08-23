# Cartilha carteira de papel Monero

**_“Tudo que você precisa para armazenar Monero são ferramentas primitivas. Um lápis e um papel por exemplo, mas você também pode esculpir em pedra ou moldar em argila, no estilo paleolítico. Como isto é possível?”_**
_13 de Julho, 2020_

Acontece que uma carteira software, a maneira mais comum de armazenar Monero (XMR), atualmente não guarda seu Monero no sentido convencional da palavra carteira. Em vez disso, o Monero existe como um livro razão público, a blockchain Monero, e sua carteira guarda uma senha especial chamada de chave privada de gasto que permite alterar esses registros. Este artigo lhe dará base e orientação de como usar uma cópia física de uma chave privada de gasto - chamada de carteira de papel - para armazenar Monero.

### _Base técnica_

É importante ter um modelo mental de como uma carteira de papel Monero funciona para se sentir confiante e usá-la com segurança. A chave privada de gasto mencionada acima, na forma hexadecimal (usando 0-9 e a-f), se parece com isto:

_Chave privada de gasto:_
**09f8225e9f6dd95457a0bca31b66a599 6e6da8be8195025817c36bf490ae0903**

Representando aproximadamente 256 bits de informação arbitrários, tem tantos caracteres e é tão complicado que ninguém pode adivinhar. Você pode apenas anotar e esconder, e assim você próprio controla seu Monero.

Como o formato da chave privada de gasto é demasiadamente complexo e propenso a erros, relações tem sido criadas com grupos regulares de palavras, chamadas frases mnemônicas, e são mais amigáveis. As duas mais importantes relações são: 

**Relação 1 (25 Palavras):** A relação incorporada na carteira oficial do Monero usa 25 palavras ordenadas escolhidas de um conjunto de 1626 palavras. Inclui restrições internas para que uma seleção aleatória de 25 palavras geralmente não seja válida. Isso permite ao software detectar erros. A lista de palavras em inglês pode ser vista aqui: [github.com/monero-project/monero/blob/master/src/mnemonics/english.h](https://github.com/monero-project/monero/blob/master/src/mnemonics/english.h). A frase mnemônica da relação referente à chave privada de gasto mostrada acima é a seguinte: _{moon pram oust mime boil boat nutshell moisture ionic enjoy below ungainly loaded rage etched atom reduce almost glass vexed jaded coils pioneer pyramid nutshell}._

**Relação 2 (24 Palavras):** A relação padrão da Proposta de melhoria do Bitcoin (BIP39) é uma relação de uso geral usado, por exemplo, pela carteira hardware Ledger. É composta de 24 palavras ordenadas, escolhidas de um conjunto de 2048. Assim como a Relação 1, tem restrições internas para que a maioria das combinações de palavras seja inválidas. A Lista de Palavras em Inglês pode ser vista aqui: [github.com/bitcoin/bips/blob/master/bip-0039/english.txt](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt). Um exemplo de frase mnemônica deste tipo é o seguinte: _{open birth pepper electric nuclear shine stable ritual napkin quarter aunt demand thing cable tuna lucky vehicle taste tourist grape buffalo fitness indoor draft}._

Ambas estas relações são padrões e amplamente usadas. Se você salvar sua chave privada de gasto usando uma delas você poderá acessar seu XMR 10, 20 ou 30 anos depois. 

As três representações-1) Relação de 25-palavras Monero, 2) BIP39 relação de 24-palavras, e 3) Forma codificada original - codificam um número aleatório de 32-byte que possui uma única restrição: deve estar abaixo de um máximo determinado. Com esta restrição, a chave privada de gasto no formato hexadecimal original parece aleatória exceto pelo penúltimo digito, que é quase sempre 0, como no exemplo mostrado no início desta seção. (Pode ser projetado para ser 1, mas provavelmente você nunca verá isso aleatoriamente.) Software pode criar uma chave privada de gasto gerando um número com 32 bytes aleatórios e tomando o restante depois de dividi-lo pelo valor máximo permitido. A aleatoriedade usada para fazer isso deve ser de alta qualidade e não previsível porque prever isso permitiria calcular a chave privada de gasto e roubar o Monero controlado por ela.

Em um moderno software Monero, a chave privada de gasto é usada para criar duas outras importantes chaves: uma chave privada de visualização e uma chave pública (ou endereço). A chave privada de visualização permite observar a entrada de XMR que é enviada para a conta usando a chave pública. Chaves privadas de visualização hoje em dia são feitas a partir de chaves privadas de gasto usando fórmulas fixas. (No início da história do Monero, algumas chaves privadas de visualização eram criadas independentemente da chave privada de gasto. Aqueles de vocês com esse tipo de chave provavelmente sabem do que estou falando.) Uma chave privada de visualização correspondente à chave privada de gasto do exemplo anterior, em hexadecimal, se parece com isso:

_Chave privada de visualização:_
**c072ce1678325c1fc09f06ed3f72bdc 290b675747cc01d5255773a63604e8a01**

Assim como a chave privada de gasto, o penúltimo dígito da chave privada de visualização é quase sempre 0, e muito raramente 1.

A chave pública (também chamada de endereço) é longa, e geralmente mostrada como uma sequência (ao invés de hexadecimal). Aqui está a chave pública correspondente a chave privada de gasto mostrada anteriormente:

_Chave Pública (Endereço):_
**44XiEedj1ivSCY6A1dFCDCCxZ3nxUQyD aGauuvgYNCAjbKSPzCe3RQ3goiXVvmfX axdYecaBQVNHPGszK9Jmp7Lg3SPAMr1**

(Não envie Monero para este endereço! Qualquer um que conhece a chave privada de gasto-i.e., qualquer um que lê este artigo pode tomá-lo para si.)

A chave pública é uma sequência de 95-caracteres iniciada com o número 4. É composta de 58 tipos de caracteres que são escolhidos para serem de fácil visualização (você não terá dúvidas entre o dígito 0 e a letra O, por exemplo). Tem restrições evitando que caracteres aleatórios ou erros formem endereços válidos. 

O processo pelo qual essas três chaves são produzidas no software é mostrada no diagrama seguinte:

	                          Frase Mnemônica
			                         ↑↓
       Dados aleatórios ----> Chave privada de gasto ----> Chave privada de visualização 
                                      |
                                      |
				                      |----> Chave Pública (Endereço)

Um processo criptográfico torna as setas vermelhas no diagrama acima irreversíveis. Mesmo conhecendo a chave pública e a chave privada de visualização não é possível calcular a chave privada de gasto.

### _Gerando chaves Monero_

Você pode criar chaves baseado no processo acima usando 1) carteiras software, 2) websites com finalidades específicas, ou 3) carteiras hardware.

**Método de geração de chave 1:** Praticamente qualquer carteira software pode ser usada para gerar chaves, mas você terá que confiar na competência e honestidade do software. É seguro usar a carteira oficial Monero ou a carteira recomendada pelo site oficial Monero, [getmonero.org/pt-br/downloads/](https://www.getmonero.org/pt-br/). O grupo de divulgação Monero Outreach tem recomendações alinhadas às do site oficial em seu próprio site [Monero Wallet Quickstart](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html).

Os passos para gerar chaves usando a carteira oficial são os seguintes: A carteira oficial Monero pode ser baixada em [getmonero.org/pt-br/downloads/](https://www.getmonero.org/pt-br/downloads/). Depois rodando a GUI (Interface Gráfica do Usuário) você deve navegar para "Criar uma nova carteira" e gerar a frase mnemônica de 25-palavras representando a chave privada de gasto usando a Relação 1 discutida acima. Navegando dentro da GUI, você pode também ter acesso a chave privada de gasto original, a chave privada de visualização, e a chave pública.

**Método de geração de chave 2:** Um site com finalidade específica que funciona apenas para gerar chaves, principalmente para carteiras de papel: [moneroaddress.org](https://moneroaddress.org/). Este site, criado pelo estimado desenvolvedor Monero moneromoo e considerado seguro por toda a comunidade, permite a você inserir um texto aleatório personalizado para gerar uma chave privada de gasto - um recurso reconfortante se você gosta de ter controle sobre a entrada aleatória. As etapas para usar este método são dadas abaixo:

Abra o site moneroaddress.org no seu navegador, carregue a página, após isso desconecte sua internet para gerar as chaves. Insira um texto bastante aleatório (mais de 50 caracteres imprevisíveis) ou deixe a linha em branco para usar a aleatoriedade gerada pelo computador, e clique em GENERATE WALLET. Isto irá gerar a chave privada de gasto, a chave privada de visualização, e a chave pública (chamada de public address neste site). Alternativamente, como incremento de segurança, o software para o site pode ser baixado como arquivo HTML e rodado em um computador desconectado da internet, ou o código fonte pode ser baixado do Github github.com/moneromooo-monero/monero-wallet-generator/.

Para geração de carteira de hardware, você pode usar uma Ledger ou uma Trezor. As etapas para geração da carteira com a Ledger são mostrados abaixo.

Baixe a Ledger Live no site [shop.ledger.com/ledger-live](https://www.ledger.com/ledger-live/). Então de dentro da Ledger Live, baixe o app específico para Monero para dentro de sua Ledger, e use-o para criar uma carteira baseado no mnemônico Ledger de 24-palavras provindos da Relação 2, usando a carteira oficial Monero. A carteira oficial Monero tem uma opção que suporta este processo com a Ledger. Este método de geração de chave tem a desvantagem de ser difícil extrair a chave privada de visualização, mas esta desvantagem é compensada pela habilidade de usar a própria Ledger para visualizar transações recebidas.

### _Gerando carteira de forma segura_

Deve-se tomar cuidado quando gerar suas chaves com os métodos acima. Uma criptomoeda privada é exclusivamente espoliável, pois é amplamente vantajosa, incorpórea, não rastreável, e não requer presença física para ser movimentada. Seja cuidadoso, ou alguém irá tomar seu Monero. Entretanto, seja razoável. Considere que se você tem pouco dinheiro, você vai carregá-lo em uma carteira de bolso, enquanto que grandes quantias são transportados em carros-fortes. Você deve ver a segurança da sua carteira de papel Monero de forma similar ao exemplo dado, e adotar uma segurança proporcional ao tamanho de suas reservas. 

Para o nível de segurança de uma carteira de bolso, você pode usar seu celular ou seu computador pessoal. Há um debate em qual é mais seguro, mas para este nível de segurança é o suficiente desde que se tome as medidas básicas de precaução. Se você está usando um smartphone, não use um que está desbloqueado. Se você está usando um computador, use um programa antivírus e desconecte o computador da internet quando estiver gerando carteiras. Não use qualquer dispositivo que você suspeita. Com estes passos você pode aplicar as técnicas da última seção para gerar suas carteiras com nível de segurança carteira de bolso ou nível de segurança carteira de papel.

Para uma segurança nível carro-forte, você deve usar um computador que nunca mais irá se conectar a Internet, e você deveria limpar a memória depois da geração das chaves (para que ninguém possa recria-las em caso de ter acesso físico ao computador). Quase todo mundo tem um computador velho. Você pode usá-lo, ou você pode comprar um novo laptop de última geração por poucas centenas de reais. Se você imprimir suas chaves da carteira para guardar, você deveria usar uma impressora sem memória embutida (tal como uma HP Deskjet 1100). Você deveria verificar o hash do software carregado no computador carteira (instalado por CD ou Pen drive já que - novamente - não deve haver conexão direta com a internet). Você pode ver exemplos desses hashes, para a carteira oficial Monero, em [getmonero.org/pt-br/downloads/](https://www.getmonero.org/pt-br/downloads/). Quando o software for assinado, você deve verificar a assinatura.

### _Criando sua carteira_

Com as técnicas e precauções da seção anterior, você está pronto para gerar chaves de forma segura, e tudo que falta é armazenar de forma física a carteira. A abordagem mais comum é imprimir a chave privada de gasto (em uma de suas três formas) em papel. Esta é a carteira de papel. Salve a chave privada de visualização e a chave pública digitalmente, em qualquer lugar. Então você pode ocultar a carteira de papel e enviar Monero para ela quando quiser, usando a chave pública compartilhável. E você pode verificar para ter certeza que os fundos estão chegando usando a chave privada de visualização.

Você pode usar métodos sem papel, também. O nome carteira de papel se deve por estar em papel, mas para este artigo a definição de carteira de papel é estendida para incluir outros mecanismos físicos de gravação. Ferramentas estão disponíveis comercialmente para fazer carteira de papel em metal compatível com Monero. Alguns destes são símbolos deslizantes em placas, alguns são gravados e alguns estampados. Muitos utilizam um padrão, como BIP39 (Relação 2, acima). Para encontrar exemplos, procure na Amazon por "criptomoedas, aço, carteira" (apesar de alguns serem feitos de cobre). Um benefício de uma carteira de papel metálica é que ela não é sensível como o papel a danos com água e fogo - isto ajuda a proteger a carteira de se perder, e é provavelmente mais relevante para o nível de segurança carro-forte discutido acima.

Você é livre para ser criativo na escolha de um material. O mundo é transcendentemente complexo, e você pode se esconder nesta complexidade escolhendo um único método. Os ladrões teriam dificuldade em descobrir que você escreveu sua chave privada de gasto dentro de uma mesa que você fez como carpinteiro, por exemplo, ou se sua chave for entalhada em arame farpado se você for um vaqueiro. Suas palavras mnemônicas podem ser escritas a mão nas páginas de um livro, se você tem uma biblioteca em casa. Encontre a técnica especial para você.

### _Proteja sua carteira_

Depois que você criou a carteira, você tem que colocá-la onde suas chaves não serão roubadas. Quanto esforço é gasto para escondê-la nos retorna às considerações a respeito dos níveis de segurança, carteira de bolso versus carro-forte. Quanto maior o valor, menor deve ser a acessibilidade. Para quantias nível carteira de bolso você pode simplesmente colocá-la em uma gaveta de difícil acesso. Para mais segurança, você vai desejar escondê-la com mais esforço, possivelmente dentro de sua casa. Você pode querer enterrá-la. Ou você pode desejar colocá-la em um cofre em um banco. Muito vídeos no Youtube guiam como esconder coisas dentro de casa. Assista e faça algo diferente. Sua casa e o mundo são complexos - abrace isso para esconder sua carteira.

### _Evitando perda_

Também tome cuidado para evitar perdas. Você poderia esquecer onde escondeu sua carteira. Você talvez acidentalmente jogou a carteira fora. Um desastre natural poderia tirá-la de você. Sua morte poderia tirá-la de sua família. E se você tomar medidas para se proteger de perdas, como você evita que essas etapas torne o roubo mais provável? Uma abordagem comum é confiar em uma ou mais pessoas, mas com verificações sobre esta confiança. É possível dividir a chave privada de gasto com várias pessoas. Técnicas criptográficas existem para ter certeza que M de N (onde M e N podem tomar qualquer valor onde M<=N) pessoas devem aceitar em recriar sua chave privada de gasto. Técnicas simples também costumam funcionar. Se você tem uma frase com 24-palavras, você poderia dar para duas pessoas 12 palavras cada (12 palavras é bastante seguro). Ou pode ser que você dê apenas informações suficientes para recuperar sua chave com muito trabalho. Você poderia contar a alguém, por exemplo, "minha carteira de papel Monero está enterrada em algum lugar do jardim, e valerá a pena encontrá-la se eu morrer."

Redundância ajuda a prevenir perda de chaves. Se você tem duas cópias e esconde elas bem separadas, problemas localizados como desastres naturais serão superados.

### _Sumário_

Este artigo abordou a arte e ciência do uso de carteiras de papel Monero. Você precisará de um software para gerar suas chaves. Carteira software, moneroaddress.org, ou uma carteira hardware fará isto. Se você está com pressa e pouca quantia, use moneroaddress.org, e se você tem mais fundos e deseja mais proteção, use a carteira oficial Monero em um computador offline que nunca ficará online novamente. Sua carteira de papel precisa armazenar pelo menos a chave privada de gasto, ou na sua forma bruta ou a forma de frase mnemônica. Você deve armazenar esta chave em um meio físico e escondê-la de forma criativa. Você deve tomar cuidado para não perder sua carteira de papel tendo cópias redundantes e descobrir uma maneira de confiar em outras pessoas, com limites nesta confiança, ou através de pistas ou usando responsabilidade M de N. Usando sua chave de visualização, que você pode armazenar e compartilhar sem risco de perder seu Monero, você será capaz de monitorar as entradas de transações recebidas em sua carteira de papel usando a chave pública compartilhada, tudo isso enquanto sua chave privada de gasto fica escondida.

### _Aprenda mais_

- [Carteira Monero Início Rapído](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html) - Um olhar e tipos de carteiras e como escolher a melhor para suas necessidades.
- [Uma carteira segura é uma carteira feliz](https://www.monerooutreach.org/praticas_recomendadas_monero/carteira-segura-uma-carteira-feliz.html) - Melhores práticas para sua carteira Monero.
