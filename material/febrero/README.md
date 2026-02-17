# Material cursado durante el mes de febrero

1. `2026.02.03`: Descripción general del curso: [Presentación del
   curso](./febrero/presentacion.pdf)
2. `2026.02.05`: Primer acercamiento: Seguimos una _vieja_ presentación
   mía (modificada por última vez en 2008): [Seguridad en redes: ¿qué es?
   ¿cómo lograrla?](./febrero/seg_en_redes.pdf) → **¿Qué es la seguridad de la
   información?** y **Características de un sistema seguro**
3. `2026.02.10`: Seguimos un poco lo delineado en la introducción del libro
   [Computer Security: Art and Science (2nd
   edition)](https://www.pearson.com/en-us/subject-catalog/p/computer-security-art-and-science/P200000000134/9780134097176):
   - Comenzamos platicando acerca de la _triada de la seguridad_, tambén
     conocida como los tres principales _aspectos_ o _servicios_ de la
     seguridad: **Confidencialidad, Integridad y Disponibilidad** (CIA, por
     sus siglas en inglés).
   - Caracterización de _amenazas y ataques_:
     - Fisgoneo (_snooping / eavesdropping / wiretapping_)
     - Modificación o alteración
     - Suplantación de identidad
 - Comenzamos a abordar el documento [Securing Cyberspace for Peace:
   Insights into Cyberthreats and International Security in
   2025](https://unidir.org/publication/securing-cyberspace-for-peace-insights-into-cyberthreats-and-international-security-in-2025/)
   presentado recientemente por UNIDIR (ONU). Citando del mensaje con que
   yo lo recibí de los colegas de [AMCID](https://amcid.org):
   
   > Este informe de UNIDIR examina los desarrollos clave en el panorama
   > global de ciberamenazas en 2025, centrándose en sus implicaciones
   > para la paz y la seguridad internacionales.  Organizado en tres
   > secciones interrelacionadas, el informe explora:
   > - ✅*Ciberamenazas en evolución*: desde los ataques a infraestructuras
   >   críticas y cadenas de suministro hasta el auge del ransomware.
   > - ✅ *Actores de ciberamenaza*: examina la creciente difuminación de
   >   las fronteras entre actores estatales y no estatales en el
   >   ciberespacio.
   > - ✅*Tecnologías emergentes*: centrada en la inteligencia artificial y
   >   la computación cuántica…
4. `2026.02.12`
   - Seguridad informática *capa a capa*. Textos introductorios (y bastante
     equivalentes):
     - [7 Layers of Cybersecurity Explained: A Complete Guide](https://axiomq.com/blog/7-layers-of-cybersecurity-explained-a-complete-guide/)
     - [Defense in Depth – The Layered Approach to Cybersecurity](https://cisotimes.com/defense-in-depth-the-layered-approach-to-cybersecurity/)
     - [What is layered security? A complete guide](https://www.comparitech.com/antivirus/what-is-layered-security/)
   - Artculo para revisar más a detalle: [A layered security architecture:
     Design issues](http://martinolivier.com/open/lasa.pdf) (Tillwick,
     Olivier 2004) presenta el tema, divide en “flujos de trabajo” y
     “servicios de seguridad”, presenta tabla detallando qué servicios
     están relacionados con cuáles capas y ante qué supuestos.
   - Dejo referencia específica para los interesados en IoT y redes
     móviles: [Physical Layer Security in Wireless Networks: A
     Tutorial](https://ieeexplore.ieee.org/iel5/7742/5751283/05751298.pdf)
     (Shiu, Chang, Wu, Huang, Chen 2011).
5. `2026.02.16`
   Discusión acerca de lo que presenta el texto de _Tillwick y Olivier_
   mencionado la clase anterior.
   - **Políticas y mecanismos** ⇒ Qué y cómo. Especificación, diseño e implementación.
   - **Evolución histórica** de los retos de seguridad en cómputo

     - _1940s/1950s_: El centro de datos y las mainframes; acceso
       físico. Seguridad como controles procedimentales y humanos;
       protección contra fallos, no ataques

	 - _1960s/1970s_: Inicios del _tiempo compartido_. Papel del sistema
	   operativo en tanto guardián. **CTSS** (1961): Contraseñas (para
	   _contabilidad_ sobre todo). Control de acceso a archivos para evitar
	   eliminaciones _accidentales_. **MULTICS** (1965): Acceso remoto. De
	   protección contra _errores_ a protección contra _usuarios_. Anillos
	   de protección. ACLs. Seguridad como _requisito de diseño_. Primer
	   virus teórico → Creeper.

     - _1980s_: Cómputo personal, LANs, BBSes. 1988: Morris. Viruses →
       Brain, Jerusalem, Stoned. Sistemas operativos personales _sin
       concepto de protección_. Equipos CERT/CC.

   Algunas lecturas para revisar en clase o posteriormente:
   - [The First Computer Virus of Bob
     Thomas](https://www.historytools.org/inventions/the-first-computer-virus-of-bob-thomas):
     Una de las reseñas más completas y con más ángulos abordados respecto
     al gusano _Creeper_, de 1971.
   - El tema me puso a leer acerca de víruses tempranos. Encontré
     información bastante interesante en [The Virus
     Encyclopedia](http://virus.wikidot.com/).
   - El primer virus realmente reconocible como tal es de 1984, y si no me
     equivoco, es el objeto de la [tesis doctoral presentada por Fred
     Cohen](https://all.net/books/DissertationOCR.pdf), asesorado por
     Leonard Adleman.
   - Fred Cohen escribió un libro en 1990, que está completo disponible en
     su sitio, llamado [A Short Course on Computer
     Viruses](https://all.net/books/virus/SCVirusOCR.pdf)
