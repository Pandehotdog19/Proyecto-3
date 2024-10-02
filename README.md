# Preguntas Teóricas

1. Fundamentos de Erlang:

- ¿Qué características de Erlang lo hacen adecuado para aplicaciones de alta concurrencia y escalabilidad? Erlang es adecuado para aplicaciones de alta concurrencia y escalabilidad porque permite crear procesos livianos de forma eficiente, gestionando miles de ellos simultáneamente. Estos procesos son independientes y se comunican mediante mensajes asíncronos, evitando bloqueos y estados compartidos. Además, Erlang tiene un sistema de tolerancia a fallos con supervisores que reinician procesos fallidos automáticamente, garantizando la disponibilidad del sistema.
- Explica el modelo de actores en Erlang y cómo se aplica en la gestión de procesos concurrentes. El modelo de actores en Erlang se basa en procesos que actúan como "actores", cada uno con su propia memoria y sin compartir estado con otros procesos. Estos actores se comunican enviándose mensajes asíncronos, lo cual elimina problemas de sincronización y evita bloqueos. En la gestión de procesos concurrentes, cada actor es un proceso independiente, lo que permite que múltiples tareas se ejecuten simultáneamente de manera segura y eficiente, facilitando el diseño de sistemas altamente concurrentes y distribuidos.

2. Características de Cowboy:

- ¿Cuáles son las principales ventajas de usar Cowboy como servidor HTTP en aplicaciones Erlang? Las principales ventajas de usar Cowboy como servidor HTTP en aplicaciones Erlang son su ligereza y eficiencia. Cowboy está diseñado para manejar un alto volumen de conexiones simultáneas con bajo consumo de recursos, aprovechando los procesos livianos de Erlang. Además, se integra de manera nativa en el ecosistema de Erlang, lo que permite aprovechar la concurrencia y la tolerancia a fallos del lenguaje, y ofrece soporte para protocolos como HTTP/1.1, HTTP/2 y WebSockets, brindando flexibilidad para diferentes tipos de aplicaciones.
- Describe cómo Cowboy maneja las conexiones concurrentes de manera eficiente. Cowboy maneja las conexiones concurrentes de manera eficiente utilizando procesos livianos de Erlang. Cada conexión se gestiona como un proceso independiente, lo que permite manejar múltiples conexiones simultáneamente sin interferencias. Estos procesos son aislados, de modo que si uno falla, no afecta a los demás, garantizando la estabilidad y el manejo eficiente de altas cargas de tráfico.

3. Uso en la Industria:

- Menciona tres empresas que utilizan Erlang/Cowboy en su infraestructura y explica brevemente cómo lo emplean. Tres empresas que utilizan Erlang/Cowboy en su infraestructura son:

1. **WhatsApp**: Utiliza Erlang para gestionar millones de conexiones simultáneas de usuarios, aprovechando la alta concurrencia y la eficiencia en la comunicación entre procesos.
2. **RabbitMQ**: Está desarrollado en Erlang y utiliza su capacidad para manejar mensajería distribuida, beneficiándose de la confiabilidad y la tolerancia a fallos que ofrece Erlang.
3. **AdRoll**: Emplea Cowboy para gestionar grandes volúmenes de tráfico HTTP, utilizando su capacidad para manejar conexiones concurrentes de manera eficiente y con bajo uso de recursos.
- ¿En qué tipos de aplicaciones es menos común utilizar Cowboy y por qué? Cowboy es menos común en aplicaciones con interfaces gráficas complejas (GUI), ya que su enfoque principal es manejar solicitudes HTTP y WebSockets, no la presentación de interfaces de usuario. Cowboy está diseñado para servir conexiones y no proporciona herramientas nativas para el desarrollo de interfaces ricas, lo cual lo hace menos adecuado para aplicaciones que requieren una experiencia visual interactiva.

4. Integración con Otros Frameworks:

- ¿Cómo se integra Cowboy con el framework Phoenix en Elixir? Cowboy se integra con el framework Phoenix en Elixir como el servidor HTTP subyacente. Phoenix utiliza Cowboy para manejar las conexiones HTTP y WebSockets, delegando en él la gestión de estas conexiones. Esta integración permite que Phoenix se beneficie de la eficiencia y la capacidad de manejo de conexiones concurrentes de Cowboy, mientras que Phoenix proporciona una capa adicional de abstracción para la lógica de la aplicación, facilitando el desarrollo de aplicaciones web modernas y en tiempo real.
- Explica la relación entre Phoenix Channels y Cowboy en el manejo de WebSockets. Phoenix Channels es una característica de Phoenix que permite la comunicación en tiempo real entre el cliente y el servidor a través de WebSockets. La relación entre Phoenix Channels y Cowboy radica en que Cowboy es el encargado de manejar la conexión WebSocket subyacente. 
Cuando se establece una conexión WebSocket, Cowboy se ocupa de la gestión de esta conexión, incluyendo el proceso de apertura y cierre. Una vez establecida la conexión, Phoenix Channels se encarga de la lógica de la aplicación, permitiendo a los desarrolladores enviar y recibir mensajes a través de canales específicos. Esto proporciona una interfaz más sencilla y poderosa para trabajar con WebSockets, facilitando el desarrollo de aplicaciones interactivas en tiempo real sin tener que manejar directamente los detalles de bajo nivel que Cowboy gestiona.

5. Desafíos y Consideraciones:

- ¿Cuáles son los principales desafíos al aprender y utilizar Cowboy para nuevos desarrolladores? Los principales desafíos al aprender y utilizar Cowboy para nuevos desarrolladores incluyen:

1. **Curva de aprendizaje**: Cowboy, al estar basado en Erlang, puede ser complejo para quienes no están familiarizados con la sintaxis funcional y el modelo de actores de Erlang. Esto puede dificultar la comprensión de conceptos básicos de concurrencia y manejo de procesos.

2. **Manejo de configuraciones**: Configurar Cowboy adecuadamente puede ser complicado, especialmente para principiantes. Los desarrolladores deben entender cómo funcionan los procesos concurrentes y cómo se estructuran las aplicaciones en Erlang para configurarlo correctamente.

3. **Debugging y errores**: La naturaleza concurrente de Cowboy puede hacer que el seguimiento de errores y el debugging sean más desafiantes. Los errores pueden manifestarse en procesos separados, lo que dificulta identificar la fuente del problema.

4. **Documentación y recursos limitados**: Aunque la comunidad de Erlang y Cowboy es activa, la cantidad de recursos y documentación puede no ser tan amplia como en otros frameworks más populares, lo que puede dificultar el aprendizaje.
- Discute cómo la tolerancia a fallos de Erlang beneficia a las aplicaciones desarrolladas con Cowboy. La tolerancia a fallos de Erlang beneficia a las aplicaciones desarrolladas con Cowboy de varias maneras:

1. **Reinicio de procesos**: Erlang está diseñado para manejar fallos mediante un sistema de supervisores que pueden reiniciar automáticamente los procesos que fallan. Esto asegura que las aplicaciones permanezcan operativas incluso si uno o varios componentes fallan, lo cual es crucial para mantener la disponibilidad en aplicaciones web.

2. **Aislamiento de procesos**: Cada conexión manejada por Cowboy se gestiona como un proceso independiente en Erlang. Esto significa que si un proceso que maneja una conexión falla, no afectará a los demás procesos o conexiones, lo que permite que el sistema continúe funcionando sin interrupciones.

3. **Manejo de errores asíncronos**: Erlang facilita la gestión de errores asíncronos a través de su modelo de actores, permitiendo a los desarrolladores diseñar aplicaciones que pueden recuperarse de fallos sin interrumpir el flujo de trabajo. Esto es especialmente útil en aplicaciones que requieren alta disponibilidad y mínima latencia.

4. **Escalabilidad**: La tolerancia a fallos permite a las aplicaciones que utilizan Cowboy escalar de manera eficiente. Los procesos pueden ser distribuidos y reiniciados en diferentes nodos del sistema sin afectar la experiencia del usuario, permitiendo que la aplicación maneje picos de tráfico sin comprometer la estabilidad.

# Link de Asciinema 

[![asciicast](https://asciinema.org/a/eaJ0BVRgFUqc4hpZpsWD652R3.svg)](https://asciinema.org/a/eaJ0BVRgFUqc4hpZpsWD652R3)
