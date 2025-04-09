# A . Cuestionario
## 1) Motivaciones para la nube
- ¿Qué problemas o limitaciones existían antes del surgimiento de la computación en la nube y cómo los solucionó la centralización de servidores en data centers?
  
Antes del surgimiento de la computación en la nube, las empresas necesitaban invertir grandes cantidades en hardware, software, infraestructura física, mantenimiento,
actualizaciones constantes y personal especializado. Esto generaba altos costos y sistemas vulnerables a fallos locales.
Con la centralización de servidores en data centers y el uso de la nube, las empresas pueden escalar sus recursos según la demanda, reduciendo costos operativos y aumentando la disponibilidad.
Además, si un entorno local falla, el proceso no se detiene, ya que los servicios continúan ejecutándose.

- ¿Por qué se habla de “The Power Wall” y cómo influyó la aparición de procesadores multi-core en la evolución hacia la nube?
  
Se refiere al límite físico que enfrentaron los procesadores cuando, al aumentar la velocidad del reloj (GHz), también aumentaba el consumo de energía y la generación de calor de forma peligrosa , por este motivo
surgió la arquitectura multi-core, donde en lugar de tener un solo núcleo muy rápido, se integraron varios núcleos en un mismo chip. Así, se podían realizar más tareas al mismo tiempo . Gracias a los procesadores
multi-core, los servidores en la nube pueden manejar muchas tareas de múltiples usuarios al mismo tiempo, facilitando la virtualización, el escalado de recursos y el rendimiento necesario para servicios en línea
modernos.

## 2) Clusters y load balancing
- Explica cómo la necesidad de atender grandes volúmenes de tráfico en sitios web condujo a la adopción de clústeres y balanceadores de carga.

Cuando los sitios web empezaron a recibir mucho tráfico, un solo servidor no era suficiente para atender a todos los usuarios. Para solucionarlo, 
se comenzaron a usar clústeres de servidores, que trabajan juntos para repartir el trabajo. Además, se usan balanceadores de carga para distribuir 
las solicitudes entre los servidores del clúster, evitando sobrecargas y asegurando que el sitio funcione rápido y sin interrupciones.

- Describe un ejemplo práctico de cómo un desarrollador de software puede beneficiarse del uso de load balancers para una aplicación web.

Un desarrollador de software está construyendo una aplicación web que se espera tenga un alto volumen de usuarios, como una tienda en línea.
Sin un balanceador de carga, si demasiados usuarios acceden al mismo tiempo, el servidor podría volverse lento o incluso caerse. Usando un 
load balancer, el desarrollador puede distribuir las solicitudes de los usuarios entre varios servidores, asegurando que cada uno maneje solo
una parte del tráfico, lo que mejora el rendimiento, la disponibilidad y la escalabilidad de la aplicación.

## 3) Elastic computing
- Define con tus propias palabras el concepto de Elastic Computing.

Elastic Computing( Computacion elastica) existe gracias al cloud computing y los provedores de este. Consiste en que el provedor de tu servicio en la nube atraves de su monitereo se encargara de brindarte los recursos que necesites, como lo es el poder de computo, el almacenamiento, memoria RAM, etc., dependiendo de la demanda que tengas en ese instante.  Esto permite ahorrar costos ya que solo pagas por los recursos que consumes.

- ¿Por qué la virtualización es una pieza clave para la elasticidad en la nube?

La virtualizacion permite crear entornos virtuales que operan de forma independiente del hardware, por lo tanto es posible copiar, mover, clonar o eliminar sin alterar la infraestructura fisica. Esto es clave para la elasticidad porque permite crear o eliminar instancias dependiendo de la demanda
  
- Menciona un escenario donde, desde la perspectiva de desarrollo, sería muy difícil escalar la infraestructura sin un entorno elástico.

Cuando un videojuego grande va a ser lanzado, se genera mucha expectación y millones de usuarios intentan loggearse al instante en que el videojuego sale. Esta alta demanda (que suele durar unos días) puede traer problemas serios en los sistemas de login, matchmaking, descarga del cliente del juego, y gestión del tráfico de red.
Desde la perspectiva de desarrollo, escalar manualmente toda la infraestructura para soportar esta carga temporal sería muy complejo y costoso. Sin un entorno elástico, sería necesario aprovisionar muchos más servidores de forma anticipada, lo que implicaría altos costos cuando la demanda baje.
Un entorno de elastico permite escalar automáticamente los recursos según la carga real del sistema: aumentando la capacidad durante el lanzamiento y reduciéndola cuando la demanda baja
Modelos de servicio (IaaS, PaaS, SaaS, DaaS)

## 4) Modelos de servicio (IaaS, PaaS, SaaS, DaaS)
- Diferencia cada uno de estos modelos. ¿En qué casos un desarrollador optaría por PaaS en lugar de IaaS?

IaaS (Infrastructure as a Service): Provisión de infraestructura, como lo son los servidores virtuales, redes, almacenamientopara que el usuario la administre.
PaaS (Platform as a Service): Plataforma gestionada para desarrollar, desplegar y escalar aplicaciones sin preocuparse por la infraestructura.
SaaS (Software as a Service): Software listo para usarse a través de internet, sin necesidad de instalación ni mantenimiento.
DaaS (Desktop as a Service): Escritorios virtuales accesibles desde cualquier lugar, gestionados por el proveedo

Un desarrollador optaría por PaaS en lugar de IaaS cuando necesita enfocarse únicamente en escribir y desplegar su código y no quiere encargarse de configurar servidores, redes o sistemas operativos
  
- Enumera tres ejemplos concretos de proveedores o herramientas que correspondan a cada tipo de servicio.



## 5) Tipos de nubes (Pública, Privada, Híbrida, Multi-Cloud)
- ¿Cuáles son las ventajas de implementar una nube privada para una organización grande?
  
-  ¿Por qué una empresa podría verse afectada por el “provider lock-in”?
  
- ¿Qué rol juegan los “hyperscalers” en el ecosistema de la nube?

# B) Actividades de investigación y aplicación

## 1)

## 2)

## 3)Armar una estrategia multi-cloud o híbrida
-Diseña una estrategia (de forma teórica) para migrar el 50% de tus cargas de trabajo a un segundo proveedor de nube, con el fin de no depender exclusivamente de uno.
Para seleccionar al nuevo proveedor, debemos evaluar distintos factores, como el costo, la ubicación de sus servidores, el soporte técnico, los servicios que ofrecen en su plataforma, entre otros. Es necesario analizar las cargas de trabajo en función de su criticidad, los requisitos de rendimiento, la sensibilidad de los datos y cuáles pueden aprovechar mejor las funciones que el nuevo servicio de nube ofrece.
-Explica dónde iría la base de datos, cómo manejarías la configuración de red y cuál sería el plan de contingencia si un proveedor falla
Lo más sensato es que la base de datos se mantenga en el lugar donde estaba originalmente almacenada, ya sea en el servicio de nube original o en el data center propio, y luego hacer conexiones seguras desde el segundo servicio de nube. Si tuviéramos dos bases de datos, una en cada servicio de nube, esto resultaría más costoso y habría que establecer mecanismos de sincronización entre ambos proveedores. Para la conexión de red, se pueden utilizar VPNs para conectar el data center propio y los dos servicios de nube. Si el proveedor del servicio fuera una empresa grande, como AWS, se podría usar sus servicios de conexión directa que ofrecen. Para las cargas de trabajo críticas, mantenemos una réplica pasiva en el otro proveedor de nube. En caso de fallo del proveedor primario, se activa la réplica en el proveedor secundario. También podemos distribuir las cargas de trabajo críticas entre ambos proveedores de nube de forma activa. De este modo, si un proveedor falla, el otro proveedor puede absorber el tráfico adicional.
## 4) Debate sobre costos

# Comparación de Tipos de Nube

| Tipo de Nube    | Costos Iniciales (CAPEX vs. OPEX)                      | Flexibilidad y Escalabilidad                     | Cumplimiento con Normativas             | Barreras/Complejidades al Cambiar de Proveedor     |
|-----------------|--------------------------------------------------------|--------------------------------------------------|------------------------------------------|-----------------------------------------------------|
| *Nube Pública* |  OPEX: Pago por uso, sin inversión inicial            |  Alta escalabilidad a demanda                   |  Depende del proveedor y región          |  Alto dependencia (vendor lock-in) si se usan servicios nativos  |
| *Nube Privada* |  CAPEX: Alta inversión en infraestructura             |  Limitada; escalar requiere más inversión       |  Control total sobre los datos          |  Menor lock-in si se usan tecnologías abiertas     |
| *Nube Híbrida* |  Mixto: inversión + operación                         |  Flexibilidad combinada con escalabilidad       |  Posibilidad de segmentar según normativa |  Complejidad técnica en interoperabilidad          |
| *Multi-Cloud*  |  OPEX: sin gran inversión inicial, pero más gestión   |  Muy alta; acceso a múltiples proveedores        |  Difícil de gestionar entre proveedores  |  Menor lock-in, pero mayor complejidad operativa   |

# C) Ejercicio de mini-proyecto