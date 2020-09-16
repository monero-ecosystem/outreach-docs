# Una vista de cerca a RPC-Pay

**_“Pasado por alto y poco apreciado hasta el momento, RPC-Pay permite microtansacciones instantáneas y privadas, y es la nueva unidad de pago oculta más pequeña en el universo de Monero.”_ Enero 29 del 2020**  

¿Por qué ejecutar un nodo público de Monero? Cuesta dinero, pero no hace dinero; al menos no directamente. Una preocupación recurrente es cómo incentivar más de estos nodos. RPC-Pay ofrece este incentivo y mucho más. Nos da una manera de usar los hashes en la minería de Monero, pero solo los hashes, para pagar por las llamadas de procedimiento remoto (RPC - Remote Procedure Calls) desde cualquier servidor habilitado para RPC-Pay, justo como un nodo de Monero. Los hashes recibidos como pago son usados por el servidor para obtener ingresos, y debido a RandomX de Monero, los hashes de la minería pueden ser calculados eficientemente por los CPUs más comunes. Pagar solamente con hashes en vez de Monero como tal, significa que RPC-Pay no sobrecarga la red ni deja registro alguno. Con RPC-Pay, minar hashes se convierte en la nueva unidad de pago oculta más pequeña en el universo de Monero.

### _RPC (Llamadas de procedimiento remoto)_

Antes de estudiar sobre qué es RPC-Pay, es útil comprender el concepto amplio de RPC. RPC es el proceso por el cual un programa (un cliente) solicita información y cálculos desde otro programa (el servidor). El servidor puede estar en cualquier computador en el Internet. Una solicitud RPC es como una llamada de subrutina en un programa normal, excepto que con el RPC, el trabajo de subrutina se realiza en el servidor. Un software intermediario específico se encarga de la red de comunicación entre la consulta y la respuesta para que el programador la vea sin inconvenientes. Muchos tipos de software de interfaz han sido utilizados a través de los años para implementar llamadas RPC.

Una familia actual de software de interfaz RPC utiliza el lenguaje de JavaScript de notación de objetos (JSON) para formar mensajes. JSON es un formato de texto estándar para intercambiar información. Se basa en el par "nombre-valor" y listas de datos para definir información de una manera amplia, extendible y legible para las personas. La codificación JSON es el principal método usado por el esquema RPC de Monero.

Para Monero, el RPC ya está siendo utilizado de muchas maneras. Por ejemplo, _monerod_, es el daemon estándard que contiene la mayoría de funcionalidades de Monero. Implementa el lado del servidor del RPC para una variedad de funciones de llamadas relacionadas a la cadena de bloques. Y el programa _monero-wallet-rpc_, que se entrega con la instalación estándard de Monero, implementa el lado del servidor de las funciones del monedero, mientras que al mismo tiempo es un cliente a un servidor _monerod_. Las llamadas RPC de Monero trabajan muy parecido a la comunicación entre un navegador (browser) y un servidor web. La información es enviada usando el método POST y devuelta como texto, usualmente JSON. Si estás interesado en ejemplos detallados en el uso de las llamadas RPC de Monero, mira el [Ejemplo #1](https://www.monerooutreach.org/stories/RPC-Pay.html#box1) sobre usar llamadas RPC de Monero. 

### _La minería de hashes_

El proceso de minería para el algoritmo RandomX Prueba de Trabajo (PoW) de Monero comienza al ejecutar un programa pseudoaleatorio (función de la nueva transacción), un nonce (número criptográfico arbitrario de un solo uso), una dirección de pago y datos del bloque anterior. Ejecutar un programa aleatorio como este es fácil para los ordenadores CPU, pero difícil para los ASIC. Luego, a la salida del programa, se le aplica una función hash criptográfica y convertida a un número de 256 bits. Si este número es menor en un umbral específico, cuenta como el haber minado un nuevo bloque.

Lo bueno de este proceso de hashing es que la dirección de pago está especificada antes de la generación del hash, lo que permite crear hashes especificamente para alguien más. Los hashes, se crean utilizando la dirección de pago, y esta propiedad, es la que le permite a los pools de minería funcionar. Hay ciertas analogías a la minería de hashes en el mundo real. Es una creación que solo tiene valor al dueño de la dirección de destino y dura hasta que el siguiente bloque sea minado. Los bloques de Monero son minados cada dos minutos.

Para RPC-Pay, los hashes son calculados por el cliente RPC mismo o por un ayudante al cliente (con mayor potencia), y los hashes son enviados al servidor a medida que son calculados. Cada hash enviado cuenta como pago. Un porcentaje minúsculo de los hashes que, cuando se representen como un número y minen un bloque por ser lo suficientemente pequeños, eventualmente tendrán valor al servidor. Estos hashes exitosos ocurren de manera aleatoria dentro de los tantos pagos con los hashes. El servidor, luego, cuenta todos los hashes para crédito, pero solo recibe pago a sí mismo cuando recibe y publica un hash exitoso en la red de Monero.

### _RPC-Pay_

RPC-Pay es una nueva característica añadida al _monerod_ y a monederos que habilita pagos para las llamadas RPC, utilizando hashes de minería. Esta capacidad está configurada a través de la línea de comando al iniciar el software del _monerod_. Parámetros específicos de inicio se ilustran más abajo en el [Ejemplo #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2). De manera similar, hay comandos con el monedero CLI que lo habilitan para crear hashes y pagarle al monerod. Estos también están representados en el [Ejemplo #2](https://www.monerooutreach.org/stories/RPC-Pay.html#box2).

Con el lanzamiento actual de Monero, hay un comando en el _monerod_, rpc_payments, relacionado con el RPC (del mismo tipo de comandos que se pueden escribir directamente a la consola del _monerod_). Este comando muestra información de los clientes que pagan y sus balances en la ventana de la consola. Ten en cuenta que el nodo olvidará los balances de créditos después de no haber sido tocado por seis meses.

RPC-Pay ofrece muchas ventajas. Apoya a la descentralización porque muchas personas querrán ejecutar un servidor que se pague a sí mismo, versus un menor número de personas que querrán asumir el costo de ejecutar uno. Pagos para RPC también estimula a los usuarios de los monederos para que ejecuten su propio nodo para evitar pagar. Todo esto fortalece y descentraliza la red.

RPC-Pay es privado. No se guardan grandes balances con créditos que requieran de compartir información para respaldos o por seguridad. Los hashes de minería usados para los pagos son anónimos, sin la posibilidad de rastrear su propiedad en la cadena de bloques. Una identificación de pagos (payment ID) puede ser usada para rastrear y guardar balances, pero con un procedimiento operativo basado en pequeños balances, esta identificación puede ser cambiada con regularidad o definitivamente no ser usada.

Es importante también considerar las desventajas en la implementación del RPC-Pay en el actual _monerod_ y el monedero. Puede ser una carga a clientes con baja potencia, tal como los dispositivos móviles quienes deben apoyarse de la ayuda de otros dispositivos para sus hashes. Además, las ganancias al servidor son aleatorias. La ganancia solo viene cuando el cliente suministra un hash que logra minar un bloque, mientras que la salida del servidor debe ser continua, igualando la provisión regular de los hashes. Finalmente, la cantidad de ganancias que un servidor puede hacer está limitado por el cronograma de la minería de Monero y tenderá a ser pequeña.

Hay más de RPC-Pay que solo programas de Monero pagando a otros programas del mismo Monero, ya que cualquier servidor puede usar RPC-Pay para tener ganancia. El software en el nodo de Monero oficila y el monedero es de código abierto y puede ser reutilizado para servicios innovadores, o para que otras aplicaciones puedan comunicarse con las instancias del monerod. El concepto central simplemente es que el servidor le da su propia dirección de Monero a sus clientes y estos la usan para crear hashes enviándolos al servidor como pago en forma de minería. El [Ejemplo #3](https://www.monerooutreach.org/stories/RPC-Pay.html#box3) da un ejemplo del código del software de RPC-Pay.

### _Primo_

Un nuevo ejemplo en la aplicación de RPC-Pay es el projecto Primo ([repo.getmonero.org/selene/primo](https://repo.getmonero.org/selene/primo)). Primo es un protocolo y paquete de programas que soportan la monetización del contenido para los sitios web. Le permite a los indeseables anuncios ser reemplazados con la generación de hashes invisibles y discretos. Un visitante en un sitio web con Primo habilitado que no quiera ver anuncios puede optar por calcular hashes de minería para Monero.

Primo tiene tres componentes, el primero es el módulo _primo-apache_ para uso en el servidor web. El dueño del sitio web instala este módulo y configura qué tipo de contenido requiere de pago, y de cuánto. El servidor web se comunica con una instancia del _monerod_, quien se encarga de la contabilidad en los pagos de los hashes y de usar los hashes exitosos para recaudar las ganancias de la minería. El segundo componente es la extensión _primo-firefox_. Un visitante a un sitio web que quiera utilizar RPC-Pay tendrá esto cargado en el navegador de Firefox. Y el tercer componente es la herramienta gráfica de control _primo-control-center_. Con estos componentes el usuario puede configurar qué sitios web reciben pago en Firefox. 

Primo ofrece recompensa al dueño del sitio web y evita anuncios al visitante al mismo tiempo que se fortalece la red de Monero. Los clientes que proveen los hashes y el servidor que los usa, forman un proceso completo de minería. Y entre más diferentes sean los mineros para Monero mejor. Primo es un gran ejemplo de las posibilidades para RPC-Pay.

### _Mirando hacia adelante_

RPC-Pay fue lanzado por primera vez en la versión 0.15 de Monero. Es completamente nuevo. Con el tiempo, capacidades se le agregarán y a medida que RPC-Pay evolucione también lo harán sus usos. Primo es la primera aplicación externa sirviendo de ejemplo a otros. Cualquier servidor en el Internet que proporcione datos y cálculos a los clientes es un potencial candidato para usar RPC-pay para financiarse. Con RandomX como el algoritmo PoW (prueba de trabajo) de Monero, también implementado en la version 0.15, cualquier computador puede calcular los hashes de manera eficiente para hacer pagos con RPC-Pay. Hoy, es el momento perfecto para esta nueva característica que producirá muchos desarrollos emocionantes.

### _Guías para empezar_

##### _#1: Ejemplo de Monero RPC_
---

Usando la herramienta de línea de comandos curl ([curl.haxx.se](https://curl.haxx.se/)), puedes hacer llamadas RPC tanto para tu propia instancia monerod o a un servidor público. Por ejemplo, si quieres saber cuántos bloques hay en la cadena de bloques, puedes utilizar el comando RPC get_block_count. Para obtener esta información de un servidor público en el mundo de Monero, instala curl y en la línea de comandos escribe lo siguiente:

```
curl -X POST [uwillrunanodesoon.moneroworld.com:18089/json_rpc](http://uwillrunanodesoon.moneroworld.com:18089/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Obtendrás una respuesta que se verá así:

```
{ "id": "0", "jsonrpc": "2.0", "result": { "count": 2021560, "status": "OK", "untrusted": false } }
```

El número de bloques dentro de la cadena de bloques cuando hicimos la llamada fue de 2,021,560.

Si estás ejecutando tu propia instancia de _monerod_ con la configuración estándar, puedes obtener la misma información en el mismo computador con el siguiente comando que es similar al anterior:

```
curl -X POST [127.0.0.1:18081/json_rpc](http://127.0.0.1:18081/json_rpc) -H 'Content-Type:application/json' --data "{\"jsonrpc\":\"2.0\",\"id\":\"0\",\"method\":\"get_block_count\"}"
```

Para mayor información sobre la interfaz RPC del _monerod_, sigue el siguiente link [www.getmonero.org/es/resources/developer-guides/daemon-rpc.html](https://www.getmonero.org/es/resources/developer-guides/daemon-rpc.html). Y para información relacionada a la interfaz del monedero RPC, sigue este [www.getmonero.org/es/resources/developer-guides/wallet-rpc.html](https://www.getmonero.org/es/resources/developer-guides/wallet-rpc.html).

##### _#2: Configurando el daemon y el monedero_
---

Para probar tu propio daemon _monerod_ funcionando con RPC-Pay, ejecútalo con la siguiente opción:

```
monerod --restricted-rpc --rpc-payment-address 4xxxxxx --rpc-payment-credits 250 --rpc-payment-difficulty 1000
```

La dirección de pago es una dirección estándar de Monero que recibirá el pago cuando eventualmente un hash mine un nuevo bloque. Los valores de rpc-payment-credits y payment-difficulty funcionan juntos para que el cliente reciba la relación de créditos/dificultad por cada hash. Estos ejemplos, que podrás cambiar para que se adapten a tus necesidades, daría 250/1000 = 0.25 créditos por cada hash. Puedes correr el monedero en el mismo computador:

```
monero-wallet-cli
```

Una vez el monedero CLI este iniciado, al escribir start_mining_for_rpc comenzará el proceso RPC-Pay. Los créditos pueden ser monitoreados usando el comando rpc_payment_info. El valor de credits-target es el número de créditos que el monedero intentará mantener. Después de haber encontrado este número de créditos, la minería debería parar. Puedes configurar este objetivo utilizando el siguiente comando en el monedero CLI:

```
set credits-target 50000
```

El valor de auto-mine-for-rpc-payment-threshold es la tasa mínima de créditos que el monedero puede minar. Si el servidor proporciona una menor tasa entonces el monedero no enviará hashes. Puedes configurar este umbral utilizando el siguiente comando en el monedero CLI:

```
set auto-mine-for-rpc-payment-threshold 0.25
```

##### _#3: Ejemplo de código_
---

El código para RPC-Pay puede ser escrito en C (u otros lenguajes) para la comunicación de redes usando librerías libres. A continuación hay un ejemplo de cómo los datos RPC-Pay en C pueden comunicarse con la instancia del monerod utilizando curl. Esta es la misma familia de curl que fue usada en la caja del Ejemplo 1 para la interconexión textual. Curl es una librería y una herramienta de línea de comandos. El código que vas a ver es una versión simplificada de la función call_monero() en Primo, que parte del módulo de primo-apache. Puedes ver el código original en el repositorio [repo.getmonero.org/selene/primo/blob/master/webserver/apache/mod_primo.c](https://repo.getmonero.org/selene/primo/-/tree/master).

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
