# Guía de Inicio Rápido del Monedero de Monero
*04/22/19*  
Almutasim  
_**Los monederos implican una de las decisiones de seguridad más importantes que toman los usuarios.**_


Un software de un monedero de Monero es un programa para almacenar, enviar y recibir Monero. Te da control total sobre tus Monero con privacidad y sin intermediarios. Nadie puede cambiar o saber todos los detalles de tus transacciones, - a menos que eligas compartir tus claves de visualización para auditoría - poder esencial de la experienca de Monero.

Para experimentar este poder, necesitarás elegir un monedero. El primer aspecto crítico de cualquier monedero es su confiabilidad. Sólo monederos recomendados por la comunidad (y el sitio [getmonero.org](https://getmonero.org/es/)) son mencionados en este artículo. A continuación, querrás elegir un monedero que se ejecute en tu dispositivo de cómputo preferido — iPhone, Android, ordenador Portátil o de Escritorio. Finalmente, deberías elegir un monedero que concuerde con tus necesidades de privacidad. Este artículo te guiará en ello.

Algunos monederos operan usando su propia copia de la blockchain de Monero. A esto también se le llama ejecutar un nodo completo. Te da control sobre la puntualidad de tus transacciones, aunque puedes confiar en un nodo remoto sin el riesgo añadido de perder tus Monero. Si dependes en la disponibilidad del nodo remoto — siempre podrás recibir, pero es posible que no seas capaz de enviar. Otro beneficio de ejecutar tu propio nodo completo es el orgullo de contribuir a la red de Monero. Nodos completos honestos hacen más fuerte a Monero. Aprende más aquí: [monero.how/how-to-run-monero-node (en inglés)](https://www.monero.how/how-to-run-monero-node).

Los beneficios de confiar, en su lugar, en nodos remotos — usando lo que se conoce como monederos ligeros, o algunas veces livianos — incluyen que no necesitas recursos de almacenamiento para la blockchain de Monero. La (no reducible) blockchain es más grande que 50 GB y en aumento. Algunos monederos que utilizan nodos remotos completos también usan menos poder de procesamiento y banda ancha de red. Si estos recursos son limitados en tu dispositivo de cómputo, un monedero ligero puede ser preferido. Este casi siempre será el caso para un monedero ejecutándose en un teléfono inteligente.

Los monederos ligeros vienen en dos tipos: de protección de claves-de-visualización y de compartir claves-de-visualización. Los monederos ligeros de protección de claves de visualización mantienen tus claves de visualización completamente privadas, y por consecuencia tienen que descargar la cadena de bloques, o al menos la porción de ella después de la fecha de creación del monedero para calcular el balance del Monero en el monedero. Por otro lado, los monederos ligeros de compartir claves de visualización comparten la clave de visualización con el servidor ejecutando el nodo remoto para calcular el balance de entrada del monedero en el servidor. Estos eficientes monederos son a veces llamados aplicaciónes de monedero. El compartir las claves de visualización reduce la privacidad si el servidor ejecutando el nodo de reconocimiento de clave de visualización no es confiable, debido a que permite la observación de transacciones de entrada. Nótese, sin embargo, que algunas veces los dueños de monederos comparten sus claves de visualización para auditoría de todas formas — esto no da lugar para transferir Monero.

Para máxima seguridad — seguridad incluso si tu dispositivo primario está comprometido por malware — se pueden utilizar monederos hardware especializados. Los monederos hardware son pequeños dispositivos electrónicos que guardan tus claves privadas y se comunican con software en el dispositivo primario usando sólo información pública. Los monederos hardware otorgan seguridad extra por el típico precio de $50-$150.

Así que, con todo esto en mente, considera las siguientes opciones: si deseas ejecutar tu propio nodo completo, una buena elección es el monedero Monero GUI o CLI oficial. El primero provee una interfaz gráfica de usuario, y el segundo una interfaz textual. Ambos pueden ser configurados ya sea para ejecutar un nodo completo o conectarse a un nodo remoto en un modo mejorado de privacidad. Estos pueden ser descargados de [getmonero.org/es/downloads](https://getmonero.org/es/downloads/). Para dispositivos Android, Monerujo, en [monerujo.io](https://www.monerujo.io/), o para iOS, Cake Wallet, en [cakewallet.io](https://cakewallet.io/), son monederos ligeros de protección de claves de visualización. Si quisieras un monedero ligero de compartir claves de visualización, el monedero basado en navegador MyMonero, en [mymonero.com](https://mymonero.com/), se recomienda. The Edge Wallet, en [edge.app](https://edge.app/), es otra sólida opción de monedero ligero de compartir claves de visualización para ambos Android y iOS.

Al escoger entre estos, ten en cuenta que la mayoría tiene una opción extra en la cual — siendo la excepción The Edge Wallet — pueden ser configurados para conectarse ya sea a un servidor remoto de terceros o a un servidor que ejecutes con un nodo. Esto se ilustra en la tabla.

## Monederos Oficiales

+ [getmonero.org/es/downloads](https://www.getmonero.org/es/downloads)  
Si deseas ejecutar tu propio nodo completo, una buena elección es el monedero Monero GUI o CLI oficial. El primero provee una interfaz gráfica de usuario, y el último una interfaz textual.

## Monederos Móviles

+ [cakewallet.io](https://cakewallet.io/)  
Cake Wallet, un monedero ligero de protección de claves-de-visualización, está disponible para dispositivos iOS.

+ [monerujo.io](https://www.monerujo.io/)  
Monerujo, un monedero ligero de protección de claves-de-visualización, está disponible para dispositivos Android.

+ [edge.app](https://edge.app/)  
Edge Wallet está disponible para ambos Android y iOS. Es un monedero ligero de compartir claves de visualización.

## Monederos Web *(Optimizados para mayor conveniencia)*

+ [mymonero.com](https://mymonero.com/)  
MyMonero es un monedero ligero, basado en navegador. También está disponible como una app de escritorio y app de iOS.

## Monederos Hardware *(Optimizados para mayor seguridad)*

+ [ledger.com](https://shop.ledger.com/?r=92d74dc2847a)  
Ledger es un dispositivo altamente seguro que guarda tu semilla mnemónica. No aplica.

+ [trezor.io](https://trezor.io/)  
Trezor es una alternativo de dispositivo altamente seguro que guarda tu semilla mnemónica.

Para un monedero hardware que provea seguridad extra en almacenar y transmitir Monero incluso si el dispositivo primario se ve comprometido, ambos Ledger, [ledger.com](https://shop.ledger.com/?r=92d74dc2847a), y Trezor, [trezor.io](https://trezor.io/), son una buena consideración. (Nótese que Ledger trabaja ahora con monederos, mientras que el soporte para el monedero en Trezor está en progreso).

Dejar que tus preferencias de recursos y privacidad conduzcan en la elección de tu monedero maximizará tu experiencia en Monero. La riqueza de Monero en opciones de monedero — desde una rápida app MyMonero hasta un monedero autorizado de nodo completo Monero CLI combinado con una Ledger o Trezor — permite a Monero satisfacer las diversas necesidades de sus usuarios.

Para explorar más: [medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d (en inglés)](https://medium.com/@anhdres/how-to-choose-a-monero-wallet-c713abb2d64d)
