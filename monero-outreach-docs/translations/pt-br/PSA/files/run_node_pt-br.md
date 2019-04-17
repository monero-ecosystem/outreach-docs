# Faça Transações com Segurança, Rode um Nó Completo

**Como faço para ter o meu próprio nó completo?**

Você pode rodar um nó completo usando as carteiras oficiais CLI e GUI do Monero. Essas carteiras carregam consigo o programa daemon monerod, que é necessário para rodar um nó completo.

Ao usar a carteira Monero CLI (com linha de comando), o nó completo é executado pelo daemon, que é um programa separado, encarregado de baixar e de armazenar a blockchain em seu computador. Enquanto o daemon administra a blockchain, a conta do Monero é administrada pela carteira CLI.

Ao usar a carteira Monero GUI (com interface gráfica), o nó completo também é executado pelo daemon. Ele pode ser executado automaticamente durante a abertura da carteira, melhorando a experiência do usuário através da integração da carteira com o processo de sincronização da blockchain. O site Monero.how possui um guia fácil para vários sistemas.

**Minerando**: é necessário ter um nó completo para se minerar. Com um nó completo do Monero você pode minerar sozinho, contribuindo para manter a segurança da rede (Veja o artigo: [**Minere para Apoiar a Rede**](https://www.monerooutreach.org/praticas_recomendadas_monero/mina-para-apoiar-a-rede.php)). Rodar um nó completo ajuda os mineradores e outros nós a saberem que eles estão na cadeia correta, fortalecendo a blockchain e dificultando a realização de ataques. De fato, os nós do Monero só precisam estar conectados a um nó honesto para terem a garantia de que eles estão na cadeia correta.

As pools de mineração também rodam nós completos do Monero. Os recursos das pools de mineração fortalecem a segurança da rede e mantém a sua descentralização. Quanto maior for o número de pools de mineração e de mineradores solo na rede do Monero, mais segura e descentralizada ela será.

**Nós Remotos**: os nós remotos são nós completos administrados por terceiros que fornecem um serviço de compartilhamento de nós, permitindo que outros usuários se conectem a eles. Os usuários podem se conectar aos nós remotos para fazerem transações com Monero imediatamente, sem precisarem esperar pela sincronização de um nó completo. Ao longo dos anos, diversas melhorias na utilização dos nós remotos foram implementadas pelos desenvolvedores do Monero.

Embora o serviço dos nós remotos seja muito útil, aumentando a usabilidade e a adoção da moeda, ele também pode afetar um dos pilares essenciais da privacidade da rede Monero. Os nós remotos podem registrar o endereço IP, a "altura de restauração" e outros dados sobre blocos dos clientes que se conectam a eles. Se você se conecta à rede Monero apenas através de nós remotos de terceiros, você deve sempre ter essas limitações em mente.

Ao usar um nó remoto, você está confiando em outras pessoas para verificar e transmitir as suas transações, delegando para elas a escolha das regras de consenso da rede. Alguns dos operadores de nós remotos conhecidos pela comunidade incluem, porém não se limitam a: moneroworld, [**monerujo**](https://www.monerujo.io/) (carteira light para android), [**cakewallet**](https://cakewallet.io/) (carteira light para iOS) e [**mymonero**](https://mymonero.com/) (carteira light para web/desktop).

**Conclusão**
Agora que você está melhor informado, mantenha-se vigilante e busque usar todos os meios de privacidade disponíveis que você tiver! Para aprender mais sobre as melhores maneiras de se manter seguro enquanto usa Monero, visite: https://www.monerooutreach.org/praticas_recomendadas_monero/
