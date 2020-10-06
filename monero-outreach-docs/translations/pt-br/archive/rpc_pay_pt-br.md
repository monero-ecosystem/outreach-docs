# RPC - Pay de perto

**_"Ignorado e pouco valorizado até então, o RCP-Pay permite microtransações instantâneas e privadas e é a mais nova menor unidade de pagamento no universo Monero."_ - 29 de Janeiro de 2020**

Por que rodar um nó público do Monero? Gera gastos, mas não gera dinheiro - pelo menos, não diretamente. Uma preocupação recorrente é como incentivar mais desses nós. O RPC-Pay oferece esse incentivo e muito mais. Ele fornece uma maneira de usar hashes de mineração de Monero - apenas os hashes - para pagar as Chamadas de Procedimento Remoto (do inglês Remote Procedure Calls, RPC) de qualquer servidor habilitado para o RPC-Pay, como, por exemplo, um nó do Monero. As hashes recebidas como pagamento são usadas pelo servidor para ganhar dinheiro e, devido ao RandomX do Monero, as hashes de mineração podem ser calculadas de maneira eficiente usando as CPUs mais populares. Pagar apenas com hashes em vez de Monero em si significa que o RPC-Pay não sobrecarrega a rede Monero e nem deixa registros. Com o RPC-Pay, as hashes de mineração se tornam a mais nova menor unidade de pagamento no universo Monero.

### _RPC_

Antes de estudar o RPC-Pay, é importante entender o vasto conceito de RPC. RPC é o processo pelo qual um programa (um cliente) solicita dados e cálculos de outro programa (um servidor). O servidor pode estar em qualquer computador conectado à Internet. Uma solicitação RPC é como uma chamada de sub-rotina em um programa comum, exceto que, com o RPC, o trabalho da sub-rotina é feito no servidor. Softwares intermediários especiais lidam com a comunicação de rede de ambas solicitação e resposta, de forma que seja imperceptível ao programador. Muitos tipos diferentes de interface de software têm sido usadas para implementar o RPC ao longo dos anos.

Uma família moderna de interface RPC usa a linguagem JavaScript Object Notation (JSON) para formar mensagens. A JSON é um formato textual padrão para câmbio de dados. Ela depende de pares nome-valor e listas de dados para definir a informação de uma maneira que seja robusta, extensível e capaz de ser lida por humanos. A codificação JSON é o método primário usado pela estrutura do RPC do Monero.

No Monero, o RPC já está sendo usado em uma variedade de maneiras. Por exemplo, o daemon padrão do Monero, contendo a maioria das funcionalidades do Monero, é o _monerod_. Ele implementa a parte de servidor do RPC para uma variedade de chamadas de funções relacionadas à blockchain. E o programa _monero-wallet-rpc_, entregue com a instalação padrão do Monero, implementa a parte de servidor de funcionalidades de carteira enquanto ele próprio é cliente de um servidor _monerod_. As chamadas RPC do Monero funcionam como um navegador comunicando com um servidor da web. Os dados são enviados usando o método POST, e a informação devolvida é textual, geralmente em JSON. Se você estiver interessado em exemplos detalhados de mensagens RPC, por favor, veja o [Exemplo #1](https://www.monerooutreach.org/stories/RPC-Pay.html#box1) em como usar chamadas RPC do Monero.

## _Hashes de mineração_

O processo de mineração para a Prova de Trabalho do RandomX do Monero começa executando um programa pseudo-aleatório que é uma função das novas transações, de um nonce, de um endereço de pagamento, e de dados de um bloco anterior. Executar um programa aleatório como esse é fácil para a CPU, mas difícil para ASICs. A saída do programa passa por uma função criptografada de hash, que o transforma em um número de 256-bit. Se esse número é menor que o limite especificado, então conta-se como uma mineração de um novo bloco.

Uma beleza desse processo de hash é que o endereço de pagamento é especificado antes da hash ser gerada, o que permite que hashes sejam criadas especificamente para outra pessoa. Essa propriedade permite que as pools de mineração funcionem - hashes são feitas usando os endereços de pagamento da pool. Existem poucas analogias da hash de mineração com o mundo físico. É uma criação que só pode ter valor para o dono do endereço de destino, e esse valor dura até que o próximo bloco seja minerado. Os blocos do Monero são minerados a cada 2 minutos aproximadamente.

Para o RPC-Pay, as hashes são calculadas pelo próprio cliente do RCP ou por um ajudante (mais poderoso), e as hashes são enviadas ao servidor assim que elas são calculadas. Toda hash enviada conta como um pagamento. Uma porcentagem minúscula de hashes realmente se tornará um valor para o servidor - aquelas que, quando representadas por um número, mineram um bloco por serem pequenas o suficiente. Essas hashes bem-sucedidas ocorrem de forma aleatória dentre as várias hashes de pagamento. O servidor, então, conta todas as hashes para crédito, mas apenas recebe o pagamento em si quando ele recebe e publica uma hash de mineração bem-sucedida na rede Monero.

## _RPC-Pay_

RPC-Pay é um novo recurso adicionado ao _monerod_ e às carteiras que habilita o pagamento para chamadas RPC usando hashes de mineração. Essa capacidade é configurada através da linha de comando quando o software do _monerod_ está sendo inciado. Parâmetros de inicialização representativos estão ilustrados abaixo no [Exemplo #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2). De forma similar, existem comandos com a carteira CLI que habilitam a criação de hashes e o pagamento ao _monerod_. Esses comandos também estão apresentados no [Exemplo #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2).

Com o atual lançamento de Monero, existe um comando _monerod_ (do tipo que pode ser digitado diretamente no terminal _monerod_) relacionado ao RPC, o rpc_payments. Esse comando disponibiliza informação sobre clientes pagantes e seus balanços na janela do terminal. Note que o nó vai esquecer sobre os balanços de crédito caso eles não sejam mexidos por seis meses.

O RPC-Pay oferece muitas vantagens. Ele sustenta a descentralização porque muitas pessoas vão querer rodar um servidor que se paga, contra um número menor de pessoas que estão dispostas a rodar um que gere custos. O pagamento para RPC também incentiva alguns usuários de carteira para rodarem seus próprios nós para evitar ter que pagar. Tudo isso reforça e descentraliza a rede.

O RPC-Pay é privado. Nenhum grande balanço de crédito que exija compartilhamento de informação para backup ou segurança é mantido. As hashes de mineração usadas como pagamento são anônimas, sem uma forma de rastrear o proprietário na blockchain. Uma identidade de pagamento pode ser aplicada para acompanhar e manter balanços, mas com um procedimento de operação baseado em balanços pequenos, essa identidade pode ser mudada regularmente ou nem sequer usada.

É importante considerar também as desvantagens da atual implementação _monerod_/carteira do RPC-Pay. Isso pode sobrecarregar clientes com baixo poder de processamento, como dispositivos móveis, os quais dependem de outros computadores ajudantes para suas hashes. Ademais, o rendimento para o servidor é aleatório. Ele vem somente quando o cliente fornece uma hash capaz de minerar um bloco, enquanto a saída do servidor deve ser contínua, casando com a provisão regular de hashes. Finalmente, a quantidade de renda que um servidor pode ter é limitada pela agenda de mineração do Monero e tenderá a ser pequena.

Tem mais sobre o RPC-Pay que apenas programas Monero pagando outros programas Monero, já que qualquer servidor consegue usar o RPC-Pay para gerar renda. O software do nó oficial do Monero e da carteira é de código aberto e pode ser reutilizado para aplicações inovadoras, ou outras aplicações podem se comunicar com as instâncias _monerod_. O conceito fundamental é simplesmente que o servidor dá seu endereço Monero para seus clientes e seus clientes usam isso para criar hashes de mineração Monero que são mandadas ao servidor como pagamento. O [Exemplo #3](https://www.monerooutreach.org/stories/RPC-Pay.html#box3) dá um exemplo de código-fonte de software de RPC-Pay.

## _Primo_

Um exemplo de aplicação do novo RPC-Pay é o projeto Primo [(repo.getmonero.org/selene/primo)](https://repo.getmonero.org/selene/primo). Primo é um protocolo e pacote de software que suporta a entrega de conteúdo de sites pagos. Ele permite que anúncios indesejados nos sites sejam substituídos pela geração invisível e driscreta de hashes. Caso um visitante de um site habilitado para o Primo não queira ver anúncios, ele pode optar por, no lugar dos anúncios, calcular hashes de mineração Monero.

O Primo tem 3 componentes. O primeiro é o módulo _primo-apache_ para uso no servidor web. O dono do site instala esse módulo e configura quais conteúdos exigem pagamento e quanto deve ser pago. O servidor web se comunica com a instância _monerod_, que lida com a contabilidade dos pagamentos de hashes e usa hashes bem-sucedidas para coletar a arrecadação da mineração. O segundo componente é a extensão _primo-firefox_. Um visitante do site que queira usar RPC-Pay terá ela instalada no seu navegador Firefox. E o terceiro componente é a ferramenta de controle gráfico _primo-control-center_. Com ela, o usuário do Firefox pode configurar quais sites recebem pagamento.

O Primo oferece compensação para o dono do site e para os usuários que evitam anúncios, tudo isso enquanto fortalece a rede Monero. Os clientes fornencendo hashes e os servidores usando essas hashes formam um processo de mineração completo. E quanto maior a diversidade de mineradores de Monero, melhor. O Primo é um exemplo excelente de possibilidades para RPC-Pay.

## _Olhando para frente_

O RPC-Pay foi lançado a primeira vez com a versão Monero 0.15. É novinho. Com o tempo, recursos serão adicionados, e conforme o RPC-Pay for evoluindo, suas aplicações também evoluem. O Primo é a primeira aplicação de fora, servindo como um exemplo para os outros. Qualquer servidor na Internet fornecendo dados ou cálculos para clientes é um candidato potencial para usar o RPC-Pay para arrecadar dinheiro. Com o RandomX como algoritmo de prova de trabalho do Monero, também novo na versão 0.15, qualquer computador pode calcular hashes de maneira eficiente para fazer pagamentos RPC-Pay. O momento é certo para esse novo recurso e ele provocará muitos desenvolvimentos interessantes.

### _Guias de introdução_

#### _#1: Exemplo de RPC Monero_
---

Usando a linha de comando curl ([curl.haxx.se](https://curl.haxx.se/)), você pode enviar chamadas de RPC Monero tanto para sua própria instância _monerod_ como para um servidor público. Por exemplo, se você quiser saber quantos blocos existem na blockchain do Monero, você poder usar o comando RPC _get_block_count_. Para ter essa informação de um servidor público no Mundo Monero, instale o curl e na linha de comando, escreva o seguinte:

```
curl -X POST [uwillrunanodesoon.moneroworld.com:18089/json_rpc](http://uwillrunanodesoon.moneroworld.com:18089/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Você terá uma resposta mais ou menos assim:

```
{ "id": "0", "jsonrpc": "2.0", "result": { "count": 2021560, "status": "OK", "untrusted": false } }
```

O número de blocos na blockchain quando isso foi rodado era de 2.021.560.

Se você estiver rodando sua própria instância _monerod_ com uma configuração padrão, você conseguirá a mesma informação com o seguinte comando, muito similar, no mesmo computador:

```
curl -X POST [127.0.0.1:18081/json_rpc](http://127.0.0.1:18081/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Para mais informações sobre a interface _monerod_ RPC, veja o [www.getmonero.org/resources/developer-guides/daemon-rpc.html](https://www.getmonero.org/pt-br/resources/developer-guides/daemon-rpc.html). E para informações sobre a interface carteira RPC, veja [www.getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/pt-br/resources/developer-guides/wallet-rpc.html).

#### _#2: Configurando Daemon e Carteira_
---

Para testar seu próprio daemon funcional _monerod_ com o RPC-Pay, rode ele com as seguintes opções:

```
monerod --restricted-rpc --rpc-payment-address 4xxxxxx --rpc-payment-credits 250 --rpc-payment-difficulty 1000
```

O endereço de pagamento é um endereço Monero padrão que receberá pagamentos sempre que um pagamento de hash de mineração minerar um novo bloco. Os valores de rpc-payment-credits e de payment-difficulty trabalham juntos para que o cliente receba a razão créditos/dificuldade para cada hash de mineração fornecido. Esses exemplos, que você vai querer mudar para se adequar às suas necessidades, dariam 250/1000 = 0,25 créditos por hash. Você pode rodar a carteira no mesmo computador:

```
monero-wallet-cli
```

Uma vez que a sua carteira CLI é iniciada, ao digitar _start_mining_for_rpc_ o seu processo RPC-Pay vai começar. Os créditos podem ser monitorados usando o comando _rpc_payment_info_. O valor credits-target é o número de créditos que a carteira vai tentar alcançar. Após atingir esse número de créditos, ela deve parar de minerar. Você pode configurar essa meta usando um comando como o seguinte na sua carteira CLI:

```
set credits-target 50000
```

O valor auto-mine-for-rpc-payment-threshold é a taxa mínima de crédito pela qual sua carteira vai minerar. Se o servidor fornece uma taxa menor, a carteira não enviará hashes. Você pode configurar esse limite usando um comando como o seguinte na sua carteira CLI:

```
set auto-mine-for-rpc-payment-threshold 0.25
```

#### _#3: Exemplo de código_
---

O código para RPC-Pay pode ser escrito em C (ou outras linguagens) usando bibliotecas livres para comunicação em rede. Abaixo está um exemplo de como dados em C de RPC-Pay podem se comunicar com uma instância _monerod_ usando o curl. Essa é a mesma família curl que foi usada na interface textual mostrada no Exemplo 1. O curl é tanto uma biblioteca como uma ferramenta da linha de comando. O código abaixo é uma versão simplificada da função call_monero() no Primo, que é parte do módulo primo_apache. Você pode ver o código original em [repo.getmonero.org/selene/primo/blob/master/webserver/apache/mod_primo.c](https://repo.getmonero.org/selene/primo/-/tree/master).

```
/* Note! Simplified, without some initialization, error checks, and memory cleanup. */
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
