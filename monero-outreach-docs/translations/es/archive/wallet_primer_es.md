# Primicia del monedero de papel para Monero

**_“Todo lo que necesitas para almacenar Monero son herramientas primitivas. Un papel y lapiz lo harán, pero también puedes tallarlo a piedra o moldearlo en arcilla, al estilo paleolítico, ¿Cómo es esto posible?”_**  
_13 de Julio, 2020_

Resulta que el software de un monedero, la manera más común de almacenar Monero (XMR), en el sentido de la palabra, en realidad no almacena Monero. En vez de eso, los Monero existen como registros en un archivo contable público, osea, la cadena de bloques de Monero, y tu monedero carga con una contraseña especial llamada la clave pública de gasto que permite cambiar los registros. Este artículo les dará una base y una guía en cómo utilizar una copia física de la clave privada de gasto para guardar Monero llamado monedero de papel. 

### _Base Técnica_

Es importante tener un modelo mental de cómo funciona un monedero de papel para estar confiado y sentirse seguro al usarlo. La clave privada de gasto que mencionamos anteriormente, en su forma hexadecimal (usando del 0 al 9 y de la 'a' a la 'f'), se ve algo así:

_Clave privada de gasto:_
**09f8225e9f6dd95457a0bca31b66a599 6e6da8be8195025817c36bf490ae0903**

Representa aproximadamente 256 bits de información aleatoria, contiene muchos caracteres y es tan complicado que nadie puede calcularlo. Puedes escribirla en algún lado y ocultarla, y entonces, serás dueño de los Monero que controla.

Debido a que la clave de gasto privada en su forma original, sin procesar, es difícil de manejar y fácil cometer errores en ella, ésta se convierte en un grupo de palabras regulares, llamada frase mnemónica, siendo más amigable. Las dos conversiones más importantes para Monero son las siguientes:

**Conversión 1 (25 palabras):** La asignación de palabras internas del monedero oficial de Monero usa 25 palabras seleccionadas de un conjunto de 1626 palabras. La asignación incluye restricciones para que la selección aleatoria de 25 palabras usualmente no sea válida. Esto le ayuda al software detectar errores. Puedes ver la lista de palabras en Inglés aquí: [github.com/monero-project/monero/blob/master/src/mnemonics/english.h](https://github.com/monero-project/monero/blob/master/src/mnemonics/english.h). La asignación de palabras para la dirección que mostramos anteriormente de la clave privada de gasto en frase mnemónica es: _{moon pram oust mime boil boat nutshell moisture ionic enjoy below ungainly loaded rage etched atom reduce almost glass vexed jaded coils pioneer pyramid nutshell}._

**Conversión 2 (24 palabras):** La propuesta de mejora estándar de Bitcoin 39 (BIP39), es un tipo común de conversión que utiliza, por ejemplo, el monedero de hardware ledger. La conversión utiliza 24 palabras ordenadas, seleccionadas de un conjunto de 2048. Como en el caso de la Conversión 1, esta opción también tiene sus propias restricciones internas, para que la mayoría de combinaciones de palabras no sean válidas. La lista de palabras en Inglés pueden ser vistas aquí: [github.com/bitcoin/bips/blob/master/bip-0039/english.txt](https://github.com/bitcoin/bips/blob/master/bip-0039/english.txt). Un ejemplo de la frase mnemónica de este tipo es la siguiente: _{open birth pepper electric nuclear shine stable ritual napkin quarter aunt demand thing cable tuna lucky vehicle taste tourist grape buffalo fitness indoor draft}._

Ambas asignaciones son estándares y ampliamente usadas. Si tu guardas la clave privada de gasto usando una de ellas podrás calcular la clave sin procesar y acceder a tus XMR en 10, 20 o 30 años.

Las tres representaciones, 1. Conversión de Monero de 25 palabras, 2. Conversión de 24 palabras BIP39 y 3. Formato sin procesar, codifican un número aleatorio de 32 bytes que tiene como única restricción estar por debajo de un máximo determinado. Con esta restricción, la clave privada de gasto en formato hexadecimal sin procesar, se ve como un número aleatorio excepto en su penúltimo dígito, el cual es casi siempre 0 como en el ejemplo que mostramos al inicio de esta sección. (Puede ser diseñado para ser 1 pero probablemente nunca veas esto aleatoriamente.) El software puede crear una clave privada de gasto generando un número con 32 bytes aleatorios y cogiendo el restante despues de dividirlo por el valor máximo permitido. La aleatoriedad utilizada para hacerlo debe ser de alta calidad y no predicable porque predecirlo permitiría calcular la clave privado de gasto y robar los Monero que controla. 

En el software moderno de Monero, la clave privada de gasto es utilizada para crear otras dos claves importantes: una clave privada de visualización y una clave pública (o dirección). La clave privada de visualización permite observar la entrada (input) de XMR que han sido enviados a la cuenta usando la clave pública. Las claves privadas de visualización actualmente están hechas por las claves privadas de gasto usando fórmulas fijas. (Al inicio de la historia de Monero, algunas claves privadas de visualización fueron creadas de manera independiente de las claves privadas de gasto. Aquellos de ustedes con este tipo de claves probablemente sepan quienes son.) La clave privada de visualización correspondiente al ejemplo de la clave privada de gasto anterior en su forma hexadecimal, se ve así:

_Clave privada de visualización:_
**c072ce1678325c1fc09f06ed3f72bdc 290b675747cc01d5255773a63604e8a01**

Al igual que la clave privada de gasto, el penúltimmo dígito hexadecimal de la clave privada de visualización siempre es 0 y muy rara vez 1. 

La clave pública (también llamada dirección) es más larga y usualmente se muestra como un hilo (string) en vez de un hexadecimal. Aquí está la clave pública correspondiente a la clave privada de gasto dada anteriormente:

_Clave pública (dirección):_
**44XiEedj1ivSCY6A1dFCDCCxZ3nxUQyD aGauuvgYNCAjbKSPzCe3RQ3goiXVvmfX axdYecaBQVNHPGszK9Jmp7Lg3SPAMr1**

(¡No envíen Monero a esta dirección! Cualquiera que conozca la clave privada de gasto, en otras palabras, cualquiera que lea este artículo, puede cogerlos.)

La clave pública es un hilo (string) de 95 caracteres que empieza con el número 4. Está compuesto por 58 tipos de caracteres que son seleccionados para ser visualmente claros (no tendrás inconvenientes, por ejemplo, con el dígito 0 o la mayúscula O). Tiene restricciones internas que ordenan que aquellos caracteres aleatorios o errores usualmente no formen una dirección válida.

El proceso por el cual estas tres claves están hechas con software se muestra en el siguiente diagrama:

			   Frase Mnemónica
			        ↑↓
 Datos Aleatorios ----> Clave Privada de Gasto ----> Clave Privada de Visualización
                                      |
                                      |
				          |    ----> Clave Pública (Dirección)

El proceso criptográfico hace que las flechas rojas en el diagrama anterior sea irreversible. El cálculo de la clave privada de gasto no es posible conociendo la clave pública y la clave privada de visualización.

### _Generando claves de Monero_

Puedes crear claves basado en el proceso anterior utilizando 1. software de monederos, 2. sitios web de propósito especial (special-purpose websites) o 3. monederos de hardware.

**Generación de claves método 1:** Casi todos los monederos de software pueden ser usados para generar claves, pero debes debes confiar en que el software sea competente y honesto. Es más seguro usar el monedero oficial de Monero o un monedero recomendado por el sitio web de Monero, [www.getmonero.org](https://www.getmonero.org/es/). Monero Outreach tiene las mismas recomendaciones iguales a las del sitio web oficial en la [Guía de Inicio Rápido para el Monedero de Monero](https://www.monerooutreach.org/cuentos/monedero-de-monero.html).

Los pasos para usar el monedero oficial para generar claves son los siguientes: El monedero lo puedes descargar en [getmonero.org/es/downloads](https://www.getmonero.org/es/downloads/). Despues de ejecutar el GUI (la interfaz gráfica), ve a "Crear un nuevo monedero" y obten una frase mnemónica de 25 palabras que representa la clave privada de gasto usando la Conversión 1 que analizamos anteriormente. Navegando en la GUI, también puedes obtener las claves privadas de gasto sin procesar, la clave privada de visualización y la clave pública. 

**Generación de claves método 2:** Existe un sitio web de propósito especial (special-purpose) solamente para generar claves, principalmente para monederos de papel: [moneroaddress.org](https://moneroaddress.org/). Este sitio, ampliamente considerado seguro por la comunidad y creado por el respetado desarrollador de Monero, moneromoo, te permite ingresar un texto personalizado aleatorio para generar la clave privada de gasto (característica que genera tranquilidad si te gusta tener el control del input, entrada). Los pasos para usar este método se dan a continuación. 

Ingresa al sitio web moneroaddress.org en un navegador, carga la página, despues de cargada desconecta la conexión a Internet para generar las claves. Introduce el texto que sea suficientemente aleatorio (más de 50 caracteres impredecibles) o dejalo en blanco para utilizar la aleatoriedad generada por el computador y dale clic en "GENERATE WALLET" (Generar Monedero). Esto te dará una clave privada de gasto, una clave privada de visualización y una clave pública (llamada 'public address' en este sitio web). También puedes, para incrementar la seguridad, descargar el software para el sitio web como un archivo HTML y ejecutarlo en un computador que este desconectado de la red o descargar el código desde Github github.com/moneromooo-monero/monero-wallet-generator/.

Para generar un monedero de hardware, puedes usar Trezor o un Ledger. Los pasos para generar un monedero con un Ledger están dados a continuación.

Descarga Ledger Live desde [shop.ledger.com/ledger-live](https://www.ledger.com/ledger-live/). Luego desde el Ledger Live, descarga la aplicación para Monero a tu Ledger y utilizalo para crear un monedero basado en la Conversión 2 de 24 palabras mnemónicas, usando el monedero oficial de Monero. El monedero oficial tiene una opción para Ledger que acompaña este proceso. Este método de generar claves tiene sus desventajas al ser difícil la extracción de la clave privada de visualización, pero esta desventaja es manejada por Ledger para tener la habilidad de ver las transacciones entrantes.

### _Generación segura del monedero_

Deben tomarse precauciones para crear las claves con los métodos mencionados anteriormente. Las criptomonedas privadas son peculiarmente codiciadas, al ser en términos generales muy fáciles de gastar, incorpóreas, no rastreables y no requieren de la presencia física para moverlas. Tengan cuidado o alguien puede coger los Monero. Se debe aplicar la razón. Considera que tienes un poco de dinero en efectivo para gastar, lo cargas en tu billetera, mientras que grandes volúmenes son movilizados en vehículos blindados. Debes considerar la seguridad para el monedero de papel de la misma manera y poner esfuerzos proporcionales al almacenamiento. 

Para la seguridad tipo billetera, se puede usar un telefono inteligente (smart phone) o un computador normal. Hay un debate abierto sobre cual es más seguro, pero para el almacenamiento tipo billetera, probablemente este bien usar cualquiera de las dos mientras se mantenga un nivel de precaución básico. Si estás usando un smart phone, usa uno que este liberado (que no tenga restricciones impuestas por el fabricante). Si estás usando un computador, corre un antivirus y desconecta el computador del Internet cuando crees un monedero. No utilices ningún dispositivo al que le tengas sospechas. Con estos pasos puedes aplicar las técnicas de la sección anterior y crear tu monedero tipo billetera de papel.

Para la seguridad tipo carro blindado, se debe usar un computador que nunca volverá a ser conectado al Internet y borrar toda su memoria despues de generar las claves (esto, por si alguien obtiene acceso al computador, no puedan recrear las claves). Casi todos tienen un computador viejo. Puedes usar ese o puedes comprar un portátil de bajo costo por unos cientos de dólares. Si imprimes las claves del monedero para almacenarlas, debes usar una impresora que tenga una memoria interna (igual que un HP Deskjet 1100). Debes revisar el hash del software instalado para el monedero en el computador (sea instalado desde un CD o una memoria USB, ya que no tiene conexión a internet directa). Puedes ver ejemplos de estos hashes, para el monedero oficial de Monero en [getmonero.org/es/downloads/](https://www.getmonero.org/es/downloads/). Si el software tiene firma, debes revisar la firma. 

### _Creando tu monedero_

Con las precuaciones y las técnicas de las secciones anteriores, estás listo para la generación de claves de manera segura, y todo lo que queda, es almacenarlas en un monedero físico. La manera más común (de tres maneras) es imprimir la clave privada de gasto en papel, eso es un monedero de papel. Guarda digitalmente, en cualquier parte, la clave privada de visualización y la clave pública. Despues, esconde el monedero de papel y envia Monero a conveniencia utilizando la clave pública. Para asegurarte que llegaron los fondos puedes validar con la clave privada de visualización.

Puedes utilizar métodos sin papel. El nombre monedero de papel viene por el uso normal en papel, pero para este artículo, la definición de monedero de papel se extiende para incluír cualquier mecanismo de impresión. Hay instrumentos comercialmente disponibles para hacer monederos de metal compatibles con Monero. Algunos recurren a símbolos, otros los graban y otros los estampillan. Algunos trabajan con el estándar, BIP39 (la Conversión de las claves del método 2). Para ver algunos ejemplos, haz esta busqueda en Amazon, “criptomoneda monedero acero” (aunque algunos son en realidad elaborados en cobre). El beneficio de un monedero de metal tipo "papel" es que no es sensible al daño con agua o fuego, esto protege al monedero de desaperecer y probablemente sea más compatible con la seguridad del carro blindado que analizamos anteriormente. 

Sientete libre de ser creativo al seleccionar un material. El mundo es trascendentalmente complejo y puedes ocultarte en esa complejidad al escoger un método único. El ladrón, por ejemplo, tendrá dificultad en darse cuenta que escribiste la clave privada de gasto internamente a una mesa que tu mismo hiciste o si la clave esta grabada en un alambre de púas tal como si trabajaras como un ganadero. Si tienes una biblioteca en casa, las palabras mnemónicas podrían estar en las páginas de un libro escritas de manera distribuida. Encuentra una técnica especial para ti.

### _Asegura tu monedero_

Despues de haber creado el monedero debes ponerlo donde las claves no puedan ser robadas. La cantidad de esfuerzo que se dedica al esconder la billetera versus el carro blindado depende de las consideraciones de seguridad que se tengan. Mayor valor, merece menor acceso. Para cantidades tipo billetera, puedes simplemente colocarla en un cajón. Para mayor seguridad, querrás esconderla haciendo un mayor esfuerzo, quizás dentro de tu casa. Querrás enterrarla. O querrás ponerla en una caja de deposito de un banco. Muchos videos en YouTube guían en cómo esconder cosas dentro de tu casa. Miralos, despues haz algo diferente. Tu casa y el mundo son complejos, aprovecha esto para esconder tu monedero. 

### _Evitar pérdida_

También cuídate de evitar la pérdida. Tal vez olvides donde escondiste el monedero. Accidentalmente podrías botar el monedero, algún desastre natural podría quitartela o tu muerte podría quitarsela a tu familia. ¿Si haces cosas para protegerte de alguna pérdida, cómo haces para mantener esos pasos para evitar el robo? Algo común podría ser confiar en una o más personas, pero con las debidas precauciones. Es posible dividir la clave privada de gasto en varias personas. Existen técnicas criptográficas para asegurarse de que cada N personas de M personas tengan que coincidir en la recreación de la clave privada de gasto. Técnicas simples también pueden servir. Si tienes una frase de 24 palabras, podrías darle 12 palabras a una persona y 12 a otra (12 palabras es bastante seguro). O podría ser que des la información necesaria para recuperar las claves despues de mucho trabajo. Por ejemplo, podrías decirle a alguien, “mi monedero de Monero esta enterrado en alguna parte del jardín y valdría la pena si te tomas el trabajo de encontrarlo si llego a morir.”

La redundancia ayuda a prevenir la pérdida de las claves. Si tienes dos copias y las escondes una separada de la otra, los problemas como los desastres naturalez serán superados.

### _En resumen_

Este artículo toca en la ciencia y el arte de usar monederos de papel para Monero. Necesitarás software para generar las claves. El software para el monedero, moneroaddress.org o un monedero de hardware generarán las claves. Si tienes prisa con pequeñas cantidades, usa moneroaddress.org, y si tienes más fondos y quieres mayor protección, utiliza el monedero en un computador que no volverá a conectarse a la red. El monedero de papel por lo menos necesita tener la clave privada de gasto en una de sus dos formas, sin procesar o en una de sus formas mnemónicas. Debes almacenar esta clave en un medio físico y esconderlo de manera creativa. Debes tener precaución de no perder tu monedero de papel teniendo varias copias y buscar la manera de confiar en otras personas, limitando esta confianza, sea a través de pistas o usando un esquema de responsabilidad M de N personas. Utilizando la clave privada de visualización, la cual puedes guardar y compartir sin el riesgo de perder Monero, podrás monitorear las transacciones entrantes al monedero de papel usando la clave pública, todo esto mientras la clave privada de gasto se mantiene oculta.

### _Aprende más_

- [Guía de Inicio Rápido para el Monedero de Monero](https://www.monerooutreach.org/cuentos/monedero-de-monero.html) - Una mirada a los tipos de monederos y cómo escoger uno que cumpla con tus necesidades.
- [Un Monedero Seguro es un Monedero Feliz](https://www.monerooutreach.org/mejores_practicas_monero/monedero-seguro-feliz.html) - Las mejores prácticas para tu monedero.