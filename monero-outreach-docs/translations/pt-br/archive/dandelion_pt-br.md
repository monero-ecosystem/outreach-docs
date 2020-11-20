# Dandelion++ for Monero

**“Dandelion++ impede que pessoas mal-intencionadas associem seu endereço IP às suas transações com Monero.” - 03/02/2020**  


Monero fica em sua rede de comunicação par a par (P2P). A rede de computadores que armazenam a Blockchain – chamados de nós – compartilham informações que suprem a rede Monero, como os endereços de nós, dados históricos da blockchain, e novas transações a serem adicionadas aos blocos. Os nós são identificados pelos endereços IP (Internet Protocol na sigla em inglês), expondo assim ao risco de que observadores possam associar endereços IP’s às transações, retirando o anonimato dos dados que eles contêm. Dandelion++ é um método para ocultar esta conexão que está planejado para o próximo lançamento do software Monero. Este artigo descreve como Dandelion++ funciona e o que irá fazer pelos usuários do Monero.


### Rede P2P do Monero 

Monero possui duas partes conceituais: 1) uma rede P2P e 2) aplicações que rodam sobre esta rede. Aplicações lidam com endereços, chaves e transações, enquanto a rede organiza e garante o fluxo de informações. Para entender o Dandelion++, é importante considerar ambas as estruturas da rede P2P e o caminho que as carteiras usam para comunicar as transações.


Sua estrutura compreende milhares de nós ao redor do mundo – dezenas de milhares se incluirmos os nós passivos – cada um conectado à internet geralmente por um pequeno grupo de outros nós chamados pares [1]. A comunicação dos nós com outros pares usa o mesmo Protocolo de Controle de Transmissão (TCP), protocolo usado pelos navegadores e servidores da internet. Os pares de um nó aparecem aleatoriamente e não precisam estar próximos geograficamente. Um número comum de pares é oito, mas alguns nós tem centenas, com cada um deles encontrando seus pares perguntando primeiramente a nós mestres especiais por seus pares, depois perguntando por novos pares, e assim por diante. O resultado é uma rede de vários computadores, cada um se comunicando através de TCP com apenas uma coleção espalhada, geralmente limitada, de outros computadores.


A carteira Monero deve se comunicar com um destes nós como uma porta de entrada para a rede P2P. Algumas carteiras como a carteira GUI oficial, podem operar seu próprio nó, enquanto outras, como MyMonero em um smartphone, sempre usam um nó remoto. Carteiras gastam Monero criando e transmitindo transações via seu nó de entrada, com o objetivo de que a transação eventualmente encontre um caminho para um nó minerador para inclusão em um bloco minerado. Cada transação guarda informações que é limitada, mas contém alguns dados significativos, incluindo um conjunto de possíveis fontes de fundos gastos. 


Agora mesmo, um nó Monero inicia a transmissão de uma nova transação usando um processo chamado inundação. Ele comunica a transação para todos os seus pares, que por sua vez comunicam para todos os seus pares, e assim por diante, com algumas verificações para prevenir comunicações redundantes. A informação viaja em todas as direções através da rede como uma onda. Algumas criptomoedas, como Bitcoin, randomizam o tempo desta transmissão, mas o Monero não o faz.


### O Problema

Seu endereço de IP pode dizer muito sobre você. (Para ter uma amostra do que se sabe sobre seu endereço IP, visite sites de informações de IP como [whatismyipaddress.com](https://whatismyipaddress.com/).) Com informações de seu Provedor de Serviço de Internet (ISP na sigla em inglês) ou provedor de Rede Virtual Privada (VPN na sigla em inglês), conforme o caso, pode lhe identificar até pelo nome. Qualquer conexão entre seu endereço IP e suas transações cria vazamentos de informações – até mesmo o mero fato de executar uma transação Monero provavelmente não é algo que você queira que estranhos observem. O problema é que uma inundação de transações na rede P2P do Monero permite fazer apenas esta conexão entre a transação e o endereço IP [2].

Conectar um endereço IP a uma transação não é fácil ou infalível. Requer muito trabalho e observação. Mas usando um botnet, por exemplo, conectado à rede P2P do Monero permite o cálculo de uma provável origem por meio de análise do tempo e comparação com informações conhecidas sobre pares. Quando há um barulho alto, você sabe em que direção olhar porque seu cérebro extrai a direção pelo tempo e pela distorção do som em cada ouvido. A análise de criptomoedas inundadas por pacotes recebidos de locais diferentes permite que um espião adversário faça o mesmo. A criação de transação é como um barulho alto para um nó botnet que funciona como um ouvido.


### Dandelion


Para sanar este problema, conceituados pesquisadores da Universidade de Illinois primeiro desenvolveram um conjunto de técnicas que eles chamaram de Dente-de-Leão [2]. O foco inicial era o Bitcoin, mas aplicável ao Monero tão bem quanto. A ideia com o Dandelion (dente-de-leão, na tradução literal) é primeiramente encaminhar transações para um nó remoto em um caminho especial indetectável e depois iniciar a inundação.


Os autores do Dandelion mergulharam na teoria e prática do uso de botnets para encontrar fontes de transações de criptomoedas. Isto inclui a criação de modelos matemáticos para anonimato (por favor veja [2] para informações detalhadas) que foram usadas para analisar três técnicas de programação: 1) inundação básica (Método do Monero), 2) inundação randomizada chamada de difusão (Método do Bitcoin), 3) difusão por proxy. A última técnica encaminha a transação para um nó aleatório, que então a transmite usando difusão. Todas as três técnicas foram consideradas inadequadas pelos modelos matemáticos dos autores.


Para resolver esta inadequação os autores propuseram o Dandelion. Dandelion define um processo para encontrar um nó Proxy para transmissão, chamado fase de anonimato (ou haste). E estabelece outro processo para transmitir, chamado de fase de propagação (ou penugem). No geral, as duas fases usam conjuntos diferentes de conexões de pares com a importante diferença que a conexão da fase do anonimato define alterações com o tempo. A descritiva do nome Dandelion vem de um processo de primeiro procurar um nó proxy ao longo de um caminho de pesquisa especial, então deste nó proxy a informação se espalha rápida e simetricamente – o formato do fluxo de informações se assemelha a flor de um Dente-de-Leão, daí o nome Dandelion.


Dandelion, ao ser analisado usando os modelos matemáticos dos autores, quando usado por todos os nós, prova ser resistente à espionagem por uma equipe de nós que são observadores passivos. Com o Dandelion, um botnet participando honestamente em uma rede P2P não pode associar endereços IP às transações de maneira confiável. 


### Dandelion++


Contudo, um adversário buscando associar endereços IP às transações pode não ser passivo, e pode não seguir as regras da rede. Alguns nós honestos podem não rodar Dandelion. Motivados pelo crescimento do mercado de análises de criptomoedas em larga escala, tal como pela Chainalysis [4], os autores revisaram as suposições de seus primeiros trabalhos e, com colaboradores, um ano depois desenvolveram Dandelion++ [3]. Dandelion++ torna o Dandelion resistente a ataques de desanonimização em larga escala e que não seguem regras.


Os criadores do Dandelion++ simularam um adversário como um botnet com vários nós espiões distribuídos ao longo da rede, formando uma fração significativa da rede geral. Em seu modelo, estes nós não precisam seguir as regras. Eles podem gerar qualquer número de conexões de saída para qualquer nó honesto ou adversário. Eles usam todas as informações disponíveis, incluindo o horário e os endereços dos remetentes. É neste ambiente muito hostil que o Dandelion++ é bem sucedido em proteger o anonimato.


Dandelion++, assim como Dandelion, tem uma fase “haste” e uma fase “penugem”. Na nova fase “haste”, para implementar conectividade dinâmica, o Dandelion++ procede em intervalos discretos, chamados épocas. Cada nó muda de época independentemente, normalmente a cada poucos minutos. Com cada nova época, um nó escolhe duas novas conexões de retransmissões aleatórias de suas conexões de saída. Então sempre que o nó cria sua própria transação ele envia através de uma dessas duas retransmissões, sempre fazendo a mesma escolha para uma dada época. E sempre que ele obtém uma transação de outro nó para encaminhar durante a fase “haste”, se for uma retransmissão (veja mais sobre isso abaixo), ele o envia aleatoriamente por uma das duas retransmissões. 


A fase “penugem” no Dandelion++ usa difusão, o processo de inundação onde o tempo da comunicação é aleatório para tornar difícil para um nó espião localizar a fonte. Uma vez que a transação iniciou, o processo continua a se propagar usando difusão, nunca retrocedendo à fase “haste”. A difusão inicia, porém, com o Dandelion++, ela toma um caminho especial. Para cada época, um nó se classifica como retransmissor ou difusor. O modo é determinado aleatoriamente ao início de cada época. Se um nó é um difusor, sempre que é fornecida uma transação para retransmitir como fase “haste”, ele a transmite usando difusão, assim iniciando a fase “penugem”.


Há um adicional, uma peça complementar para o Dandelion++, chamado de mecanismo à prova de falhas. Cada nó que retransmite uma transação durante a fase “haste” inicia uma contagem para aquela transação. Se o limite de tempo for ultrapassado sem que o nó receba a mesma transação de volta durante a fase “penugem”, o nó inicia sua própria fase “penugem”. Isto serve a dois propósitos: Isso frustra as tentativas de desanonimização usando o tempo, e derrota os ataques chamados buraco negro, onde nós adversários descartam transações durante a fase “haste” ao invés de retransmiti-los. 


Com estas técnicas no lugar, dá garantias formais de resistência a desanonimização. Ele alcança isso usando técnicas locais, ao contrário da rede Tor, que requer um raciocínio global. Cada elegante nó Dente-de-Leão++ toma suas próprias decisões sobre seu comportamento. O resultado é um rápido e eficiente, ainda eficaz, técnica para prevenir que adversários sofisticados, associem endereços IP a transações. 

### Integração com Monero

Apesar de que o Dente-de-Leão foi explicitamente desenvolvido para o Bitcoin, ele foi recentemente aplicado ao Monero pelo desenvolvedor Lee Clagett (vtnerd), com teste e revisão feito pelo desenvolvedor moneromooo. Discussões e alterações de arquivo feitos por estes proeminentes desenvolvedores Monero pode ser vistos como partes do pull request (solicitação de puxar no inglês literal) do controle de fontes [5]. Um pull request é parte de um processo formal pelo qual novos códigos entram no código base do Monero. Apesar de que o pull request do Dente-de-Leão++ foi aprovador por moneromooo, no momento da escrita deste artigo ainda não foi completamente revisado e não foi incorporado ao código base do Monero.

Quando liberado, Dente-de-Leão++ será usado como padrão, embora será possível desliga-lo, definindo a probabilidade de entrar no modo “penugem”, probabilidade em 100% no código C++ do arquivo cryptonote_config.h e recompilá-lo. Importante, até neste caso de recompilação direcionada, o novo lançamento usará difusão, com atrasos aleatórios, ao invés de inundação básica. A data para lançamento não está definida. A adição do Dente-de-Leão++ não requer um hard fork (termo inglês para bifurcação da blockchain). 

Há algumas pequenas desvantagens e limitações. Dente-de-Leão++ adiciona atrasos para a propagação das transações. Isto vem de múltiplas fontes, que são discutidas pelos autores do Dente-de-Leão++ [3]. Primeiramente, a existencia da fase “haste” adiciona atrasos, possivelmente poucos segundos, baseado na analise dos autores e avaliações experimentais. A difusão adiciona atrasos aleatórios durante a fase “penugem”, normalmente menos que um segundo. E a rede deve estar sujeita a um ataque buraco negro, a espera da confirmação pelo iniciador poderia atrasar a transmissão por minutos. Além disso, Dente-de-Leão++ não criptografa os pacotes P2P, e não protege a espionagem a nível ISP/VPN – para isso, você pode usar Tor.

### Sumário

Um poderoso método para prevenir a desanonimização está chegando ao Monero, Dente-de-Leão++. Este método, desenvolvido originalmente para o Bitcoin, e aplicado ao Monero pelo desenvolvedor Lee Clagett, previne adversários de associar endereços IP às transações Monero até mesmo em ataques sofisticados em larga escala. Está focado particularmente sobre resistência a botnets. Dente-de-Leão++ usa fases “haste” e “penugem” que fazem o fluxo de informação tomar a forma de uma flor de Dente-de-Leão, daí o seu nome. Através disso, torna-se difícil para um observador localizar a fonte de uma transação.  Esta bonita nova característica irá aumentar os já excelentes recursos de privacidade do Monero e levar o Monero adiante em seu caminho de contínua melhoria.

[1] Exploring the Monero Peer-to-Peer Network, T. Cao, J. Yu, J. Decouchant, X Luo, and P. Verissimo, [eprint.iacr.org/2019/411.pdf](https://eprint.iacr.org/2019/411.pdf).  
[2] Dandelion: Redesigning the Bitcoin Network for Anonymity, S.B. Venkatakrishan, G. Fanti, and P. Viswanath, SIGMETRICS ’17, June 5-9, 2017, Urbana-Champaign, [publish.illinois.edu/science-of-security-lablet/files/2016/07/Dandelion-Redesigning-BitCoin-Networking-for-Anonymity.pdf](http://publish.illinois.edu/science-of-security-lablet/files/2016/07/Dandelion-Redesigning-BitCoin-Networking-for-Anonymity.pdf)  
[3] Dandelion++: Lightweight Cryptocurrency Networking with Formal Anonymity Guarantees, G. Fanti, S.B. Venkatakrishnan, S. Bakshi, B. Denby, S. Bhargava, A. Miller, and P. Viswanath, arXiv:1805.11060v1, May 28, 2018, [arxiv.org/pdf/1805.11060.pdf](https://arxiv.org/pdf/1805.11060.pdf)  
[4] Chainalysis, [chainalysis.com](https://www.chainalysis.com/).  
[5] Adding Dandelion++ support to public networks: #6314, [github.com/monero-project/monero/pull/6314](https://github.com/monero-project/monero/pull/6314).  
