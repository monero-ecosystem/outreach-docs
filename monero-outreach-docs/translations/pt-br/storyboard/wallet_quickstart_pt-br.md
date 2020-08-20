# Guia rápido da carteira Monero
*22/04/19*
Almutasim
_**As carteiras envolvem uma das decisões de segurança mais importantes que os usuários tomam.**_


Uma carteira Monero de software é um programa para guardar, enviar ou receber Monero. Ela oferece controle total sobre seu Monero com privacidade e sem intermediários. Ninguém consegue ver todos os detalhes ou alterar suas transações — a não ser que você decida compartilhar suas chaves de visualização para fins de fiscalização — poder é a essência da experiência com Monero.

Para experimentar esse poder, você precisará escolher uma carteira. O primeiro aspecto crítico de qualquer carteira é sua confiabilidade. Apenas as carteiras recomendadas pela comunidade (e pelo site [getmonero.org](https://www.getmonero.org/pt-br/index.html)) são mencionadas nesse artigo. Depois você irá querer uma carteira que rode nos seus dispositivos de preferência — iPhone, Android, notebook ou computador desktop. Finalmente, você deve escolher uma carteira que combine com suas necessidades de privacidade. Esse artigo vai lhe guiar nesse sentido.

Algumas carteiras operam usando a sua própria cópia do blockchain do Monero. O que também é chamado de rodar um nó completo. Isso lhe dá controle sobre as linhas do tempo das suas transações. Embora você possa confiar em um nó remoto sem o risco de perder seu Monero, você dependerá da disponibilidade desse nó remoto — você sempre poderá receber, mas nem sempre terá disponibilidade para enviar. Outro benefício de rodar seu próprio nó completo é orgulho da contribuição para a rede Monero. Nós completos honestos tornam o Monero mais forte. Aprenda mais aqui_(em inglês)_: [monero.how/how-to-run-monero-node](https://www.monero.how/how-to-run-monero-node).

Os benefícios de confiar, em vez disso, em nós remotos — usando o que são chamadas de carteiras leves (do inglês "light" ou "lightweight") — incluem não precisar de recursos de armazenamento para o blockchain do Monero. O blockchain "não reduzido" (do inglês "unpruned") é maior que 50 GB e está crescendo. Muitas carteiras que usam nós completos remotos também utilizam menos poder de processamento e banda larga de rede. Se esses recursos forem limitados no seu dispositivo de informática, uma carteira leve pode ser a melhor opção. Esse vai ser quase sempre o caso de carteiras rodando em um smartphone, por exemplo.

Existem dois tipos de carteiras leves: as protetoras da chave de visualização e as de compartilhamento da chave de visualização. O primeiro tipo mantém sua chave de visualização completamente privada e, como consequência, precisam baixar o blockchain, ou pelo menos uma parte dele após a data de criação da carteira para calcular o saldo de Monero na sua carteira. Por outro lado, o segundo tipo de carteira compartilha sua chave de visualização com o servidor que está rodando o nó remoto para calcular o saldo dos depósitos na carteira. Essas carteiras eficientes são às vezes chamadas de apps de carteira. O seu compartilhamento de chaves de visualização reduz a privacidade se o servidor que roda o nó remoto com reconhecimento da chave de visualização não for confiável, pois ele permite que se veja todas as transações de depósito. Repare, porém, que às vezes os donos das carteiras comparatilham suas chaves de visualização para fiscalização mesmo assim — a chave de visualização não permite a transferência de Monero.

Para segurança máxima — segurança mesmo que seu dispositivo primário esteja contaminado por vírus — carteiras de hardware especializadas podem ser usadas. Carteiras de hardware são pequenos dispositivos eletrônicos interativos que armazenam suas chaves privadas e se comunicam com o software no dispositivo primário utilizando apenas informações públicas. Carteiras de hardware oferecem segurança extra por um preço entre $50-150 dólares (aproximadamente R$200-600).

Então, com tudo isso em mente, considere as seguintes opções: se você deseja rodar seu próprio nó completo, uma boa opção é a carteira GUI ou CLI oficial do Monero. A primeira oferece uma interface gráfica de usuário e a segunda, uma interface textual. Ambas podem ser configuradas tanto para rodar um nó completo quanto para se conectar com um nó remoto de uma maneira mais privada. Essas carteiras podem ser baixadas em [getmonero.org/downloads](https://www.getmonero.org/pt-br/downloads/). Para dispositivos Android, o Monerujo, em [monerujo.io](https://www.monerujo.io/), ou para iOS, a Cake Wallet, em [cakewallet.io](https://cakewallet.io/), são carteiras leves recomendadas do tipo que protegem sua chave de visualização. Se você preferir uma carteira leve do tipo que compartilha a chave de visualização, a carteira direto do navegador MyMonero, em [mymonero.com](https://mymonero.com/), é recomendada. A Edge Wallet, em [edge.app](https://edge.app/), é outra boa opção de carteira leve de compartilhamento de chave de visualização para ambos Android e iOS.

Quando estiver escolhendo entre essas carteiras, tenha em mente que a maioria — exceto a Edge Wallet — tem um recurso extra em que elas podem ser configuradas para se conectar tanto com um servidor remoto de terceiros quanto com um servidor que você roda com um nó. Isso é ilustrado na tabela.

## Carteiras oficiais

+ [getmonero.org/downloads](https://www.getmonero.org/pt-br/downloads/)
Se você quer rodar um nó completo, uma boa escolha é a carteira GUI ou CLI oficial do Monero. A primeira oferece uma interface gráfica de usuário e a segunda, uma interface textual.

## Carteiras móveis

+ [cakewallet.io](https://cakewallet.io/)
Cake Wallet, uma carteira leve protetora da chave de visualização, está disponível para dispositivos iOS.

+ [monerujo.io](https://www.monerujo.io/)
Monerujo, uma carteira leve protetora da chave de visualização, está disponível para dispositivos Android.

+ [edge.app](https://edge.app/)
Edge Wallet está disponível para ambos Android e iOS. É uma carteira leve de compartilhamento de chave de visualização.

## Carteiras web *(Otimizadas para conveniência)*

+ [mymonero.com](https://mymonero.com/)
MyMonero é uma carteira leve direto do navegador. Está disponível também como app para iOs e como app de desktop.

## Carteiras de hardware *(Otimizadas para segurança)*

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)
Ledger é um dispositivo de altíssima segurança que armazena sua semente mnemônica.
Não aplicável

+ [trezor.io](https://trezor.io/)
Trezor é um dispositivo alternativo de altíssima segurança que armazena sua semente mnemônica.

Para uma carteira de hardware que fornece segurança extra no armazenamento e transferência de Monero mesmo que o dispositivo primário esteja com vírus, tanto a Ledger, [ledger.com](https://shop.ledger.com/?r=92d74dc2847a), quanto a Trezor, [trezor.io](https://trezor.io/), são bem reconhecidas. (Repare que a Ledger funciona agora com carteiras Monero, enquanto a compatibilidade da Trezor com essas carteiras ainda está em desenvolvimento.)

Deixar que suas preferências de recursos e privacidade guiem sua escolha de carteira irá maximizar sua experiência com Monero. A riqueza do Monero em opções de carteira — do rápido aplicativo MyMonero até a oficial carteira CLI de nó completo, em conjunto com a Ledger ou a Trezor — permite que o Monero agrade às diversas necessidades dos seus usuários.

Para pesquisar mais: [medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
