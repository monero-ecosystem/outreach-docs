# Cómo aceptar Monero

Si eres capaz de instalar una aplicación, serás capaz de configurar tu negocio para aceptar Monero (XMR). Esta guía explica las formas más comunes que los comerciantes usan para aceptar monero y cómo iniciarse de la forma menos sufrida y trabajar sobre ello a medida que creces.

Lo primero que debes saber es que no hay ningún tipo de cuenta para comerciantes en Monero, sólo necesitas un monedero y una dirección para empezar. Sin embargo, es recomendable que crees una dirección separada para tu negocio por las mismas razones que se sugiere tener separadas las cuentas corrientes personales y las de los negocios. Puedes usar el mismo software para el monedero, pero tener dedicadas unas direcciones para el negocio ayudará a mantener las cuentas organizadas.

Si todavía no tienes un monedero o dirección de Monero, deberás crear primero una. Los monederos GUI/CLI oficiales de Monero de [getmonero.org/es/downloads](https://www.getmonero.org/downloads/) siempre serán la opción recomendada. Además, esta guía hará referencias a monederos móviles, de las cuales puedes encontrar información en nuestra página [Guía de Inicio Rápido del Monedero de Monero](https://www.monerooutreach.org/stories/monero-wallet-quickstart.html).

### _La Anatomía de una Transacción de Monero_

Las transacciones de Monero pasan por los siguientes pasos. No es necesario entender los aspectos técnicos de esto, pero como comerciante, necesitas tener un conocimiento básico de los pasos para ser capaz de decidir qué intercambios te vienen mejor.

1. **Compra** - Tras sumar la compra de los consumidores en tu moneda local y aplicar los impuestos de venta (si corresponde), simplemente necesitas calcular el monto correspondiente en XMR.
2. **Pago** - El cliente escanea tu código QR para pagarte en XMR. La tarifa de transacción de Monero es pagada por el emisor y calculada al momento de la misma.
3. **Conjunto de Transacciones** - En el primer segundo, la transacción es anunciada en la red de Monero y situada en el conjunto de transacciones, también llamada mempool. Puedes comprobar la existencia de tu transacción en la mempool. Aquí encontrarás una mempool de ejemplo: [xmrchain.net/txpool](https://xmrchain.net/txpool).
4. **Confirmación** - En menos de 4 minutos, la transacción estará normalmente en un bloque de la cadena de bloques y tendrás la certeza de que es válida. El pago aparecerá ahora en tu monedero como fondos bloqueados. Tu transacción será confirmada por 9 bloques más antes de ser desbloqueada y virtualmente imposible de revertir.

Puede haber un retraso en cuan rápido tu monedero revisa nuevas transacciones, a veces 90 segundos. Entonces, dependiendo de cuándo revisa tu monedero nuevas transacciones y cómo de rápido se mete tu transacción en un bloque minado, el tiempo real esperado es de unos 4 a 12 minutos para que la transacción aparezca en la monedero. Para un vistazo más profundo en el proceso de transacción de Monero y la duración promedio, visita [monero.how/how-long-do-monero-transactions-take](https://www.monero.how/how-long-do-monero-transactions-take).

Si una espera de 4-12 minutos es imposible para tu negocio, puedes hacer una transacción de 0 confirmaciones en un segundo. En vez de esperar a la primera confirmación, echa un vistazo en la mempool para revisar que la transacción exista. Hay un riesgo, porque la transacción no ha sido confirmada, pero un ataque de doble gasto es improbable si la persona está en frente de tí. Para unas transacciones al por menor, los beneficios de completar la transacción en un segundo suelen acarrear un riesgo menor y si sientes que algo no está bien, siempre puedes esperar individualmente a la primera confirmación.

### _Identificando Transacciones_

Algo que es obvio cuando empiezas a aceptar Monero es que no conoces automáticamente la dirección de quien hace el envío, porque las transacciones son privadas. Dependiendo de tu negocio, enlazar la transacción y el pago podría no ser algo importante, o podría ser algo realmente importante, eso depende de tí. La buena noticia es que hay varias técnicas simples para ayudarte a identificar con seguridad tus pagos en XMR.

La primera es simple, haz una nota. Si estás negociando con un volumen bastante bajo de transacciones, puedes simplemente añadir tu factura o número de transacción como una nota en tu monedero cuando recibas fondos. Otra forma sería anotar el ID de transacción en el sistema de tu punto de venta o en el software de contabilidad.

Pero cuando necesitas identificar el pago de un cliente con una transacción, la respuesta son las subdirecciones de Monero. Una subdirección es una dirección de un solo uso, y como son gratis y puedes crear tantas como quieras, puedes dar una subdirección única a cada consumidor para ser capaz de trazar cada pago. Esta faceta es también útil si quieres mantener tu dirección principal en privado.

### _Transacciones Multifirma_

Las transacciones multifirma requieren la firma de varios participantes antes de que pueda ser anunciada en la red. Por ejemplo, podrías planificar una transacción en la que los fondos no serían liberados hasta que el comprador y el vendedor no estén conformes. No vamos a profundizar en este artículo en esta clase de transacciones, pero visita [getmonero.org/resources/user-guides/multisig-messaging-system.html](https://www.getmonero.org/resources/user-guides/multisig-messaging-system.html) para aprender más.

### _LeMonero Enterprises, LLC_

Con este resumen de cómo funcionan las transacciones de Monero, vamos a aplicarlo a algunos ejemplos del mundo real usando nuestra empresa ficticia LeMonero Enterprises, LLC. La adopción e integración de Monero es como una historia "De Pobre a Rico" donde nosotros vamos a vender limonada y nuestros consumidores van a pagar en Monero de tres formas diferentes a medida que crecemos.

En todos estos ejemplos, vamos a decir que estamos vendiendo nuestra limonada, valuada en nuestra moneda local, por $1. Nuestra contabilidad y carga fiscal también estará en la moneda local. Tus condiciones dependerán de donde vivas y cómo está regulado tu tipo de negocio.

### _Puesto de LeMonero_

En nuestro puesto de limonada tenemos una simple caja de cambio y un cuaderno para grabar cada venta, como es común en los mercados de productores, festivales, eventos minoristas y ventas de artesanías comunitarias donde el equipamiento es limitado. La buena noticia es que aceptar Monero en este tipo de transacciones solo requiere de un móvil.

Para los pagos en Monero, la transacción comienza igual que con el dinero tradicional. Preparas la limonada, estableces el total y guardas la transacción en el cuaderno acorde a los requisitos de tu contabilidad.

Un total de $1.00 es convertido a XMR justo antes del pago. La tasa de cambio cambia constantemente. Al momento de la redacción, 1 XMR cuesta $61.40, por lo que una limonada de $1.00 serían 0.0162 XMR.

El cliente necesita tu dirección de Monero en su móvil para pagarte 0.0162 XMR. Copiar y pegar la dirección suele ir bien, pero normalmente se puede escanear con un código QR. El código QR contiene tu dirección de XMR, de forma que el monedero de tu cliente puede escanearla. Tu monedero la genera cuando seleccionas 'recibir', y puedes girar tu móvil hacia tu consumidor para que la escanee. Otra alternativa sería tener tu código QR impreso y así usar únicamente tu monedero para confirmar la transacción.

Tan pronto como el cliente te envíe la transacción, esta es emitida a la red de Monero. Los fondos aparecerán en tu monedero en 4-12 minutos tras la primera confirmación.

Sin embargo, rara vez tenemos que hacer esperar a un cliente, ya que la confianza se puede extender a los clientes de limonada, especialmente a los habituales. Para las escasas personas con grandes pedidos, deberíamos explicarles simplemente que ello tomaría unos pocos minutos.

### _Tienda LeMonero_

Con trabajo duro, nuestro pequeño puesto de limonada se ha convertido en una tienda. Ahora somos un establecimiento fijo. Además de Monero y el efectivo, la tienda acepta tarjetas de crédito y débito y tiene un buen sistema de pagos para grabar las transacciones y administrar el inventario en vez de un cuaderno.

LeMonero tiene una gastos generales elevados, y no podemos permitirnos mantener únicamente pagos en XMR, necesitamos convertir algunos XMR en dinero tradicional para pagar las facturas, aunque elegimos liquidarlo manualmente cuando más nos conviene. Todavía necesitamos un procesador de pagos, sin embargo, las comprobaciones de los clientes son fáciles y rápidas.

Muchos dueños de negocios están familiarizados con procesadores de pago de crédito/débito, terceros que te alquilan un terminal, quienes te meten en su red de pagos y te cargan con comisiones por cada pago y cada mes. Un procesador de pagos de Monero puede funcionar así, o puede ser tu propio procesador de pagos con un poco de software y sin tener que pagar una tarifa.

Como el software Monero es de código abierto, puedes crear tu propia pasarela de pago desde cero (eso es genial), pero las integraciones de Monero han hecho ya el trabajo por ti y crearon bibliotecas y complementos que hacen todo el trabajo duro en [github.com/monero-integrations](https://github.com/monero-integrations).

Alternativamente, un procesador de pagos Monero de terceros tendrá software y aplicaciones e interfaces empaquetadas que simplifican la configuración. También tendrán interfaces y herramientas para que usted administre su cuenta y un soporte técnico y de atención al cliente. Echa un vistazo a nuestra guía de procesadores de pago de Monero para ayudarte a decidir que configuración te viene mejor.

### _LeMonero.com_

Nuestra tienda de limonada está encantándole a la gente y nos hemos expandido a las ventas en línea y a más locales. La buena noticia es que no necesitamos cambiar nuestro procesador de pagos, solo necesitamos usarlo más.

La integración del carrito de compras es fácil en comparación con las transacciones físicas en tiempo real. Ya sea que estés utilizando un procesador de pagos de código abierto o un servicio de terceros, los complementos para WooCommerce, Shopify, etc. están disponibles y son fáciles de instalar.

Ahora podemos tener liquidaciónes automáticas en dinero tradicional. Como puesto de limonada, mantenemos nuestros pagos en XMR; cuando éramos una tienda, liquidábamos algunos cuando el cambio era favorable. Pero nuestras necesidades de flujo de caja se han intensificado. Necesitamos un cambio de XMR a fiat predecible, incluso si eso significa tarifas adicionales o un momento desfavorable.

La mayoría de los procesadores de pagos de terceros proporcionarán conversión a fiat automática con los intercambios de sus socios por una tarifa. Pueden haber tarifas de transacción o retiro adicionales dependiendo de los proveedores, pero si nos conviene, puede valer la pena.

Con un procesador de pagos de código abierto eres libre de desarrollar tu propia solución usando la API de tu exchange preferido con llamadas al monero-wallet-rpc. Esto va más allá de el objetivo de este tutorial, pero puedes encontrar más sobre ello en [getmonero.org/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/resources/developer-guides/wallet-rpc.html).

### _Aprende más_

- Cómo aceptar Monero con los monederos oficiales: [getmonero.org/es/get-started/accepting](https://www.getmonero.org/es/get-started/accepting/index.html)
- [Monero Merchant FAQs](https://www.monerooutreach.org/merchants/monero-merchant-faqs.html)
- Multifirmas de Monero explicadas: [hackernoon.com/monero-multisignatures-explained...](https://hackernoon.com/monero-multisignatures-explained-46b247b098a7)
- Potenciales riesgos de las transacciones con cero confirmaciones: [reddit.com/r/Monero/.../potential_risks_of_accepting_zero_confirmation](https://www.reddit.com/r/Monero/comments/7s937y/potential_risks_of_accepting_zero_confirmation/)

Ilustraciones por: