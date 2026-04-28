# Material cursado durante el mes de abril

## Unidad 3: Tipos de ataque

1. `2026.04.07`

   - Cruce de límites de confianza: Ejecución de JavaScript del lado del
     cliente ⇒ XSS (_Cross-Site Scripting_), CSRF (Cross-Site Request
     Forgery)
     - **XSS**: Inyección de _Javascript ejecutable_. Típicamente,
       contenido _a desplegar_ en el cliente Web, no sanitizado. _Vector_:
       Hacer que el cliente interprete contenido provisto por el atacante
       como _inicio de un script_ (p.ej. etiqueta `<script>` o un atributo
       `onerror` de elementos como `<img>`).
     - **CSRF**: Engaña a un cliente (típicamente Web, pero no es
       indispensable) para _realizar una petición cuyo destino controla_ el
       atacante. Normalmente, son peticiones `GET` (no `POST`). CSRF no
       permite mucha interactividad (sólo lanzar solicitudes específicas
       _con la autenticación_ del cliente.
     - _Mitigaciones_:
       - XSS → Codificación de todo el contenido proveniente de fuera del
         sistema _evitando caracteres con significado interpretable_ (`< >
         & # ' "`); [Content Security Policy
         (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CSP)
         desde el servidor HTTP
       - CSRF → _tokens_ ocultos que varíen _y sean validados_ por cada
         consulta (no sirve por sesión o por formulario: Por cada
         invocación). Puede enviarse como parámetro o como cookie (o como
         ambos). ¡Ojo! Si hay vulnerabilidad XSS, ésta puede _robar el
         token anti-CSRF_.
     - Espacio para jugar a romper sitios: [XSS
       Game](https://xss-game.appspot.com/). Y... hay que reconocer que no
       siempre es fácil hacerlo, así que si de a tiro no podemos, no está
       prohibido [hacer trampa aprendiendo cómo lo hizo alguien
       más](https://jh123x.com/blog/2022/google-xss-game/).
	   
	   Menos _lúdico_, pero también interesante →
       [XSSTrain](https://xsstrain.com/)

2. `2026.04.09`

	- Revisión de trabajo entregado: Para esta fecha teníamos la entrega de
      la [Actividad práctica: ¡Intentemos un ataque! (a uno
      mismo)](../../entregas/intentemos_ataque/README.md). Revisamos y
      comentamos el ejemplo desarrollado [por su compañero José
      Lili](../../entregas/intentemos_ataque/LiliBeltranJoseEmiliano/ReporteEjecutivo.md).

3. `2026.04.13`

   - Revisión de trabajo entregado: Revisamos también las entregas de los
     compañeros [Nicolás Campuzano (recorrido de directorios / ejecución de
     código
     arbitrario)](../../entregas/intentemos_ataque/NicolasCampuzano.md) y
     de [Carlos Camargo (escalación de
     privilegios)](../../entregas/intentemos_ataque/CVE dirty
     pipe.pdf). ¡Ojo! Engranar dos ataques como los que (de pura
     casualidad) presentaron los compañeros lleva al compromiso total de un
     servidor remotamente.

   - Comenzamos a acercarnos al tema de codificación de caracteres hablando
     de ASCII, tablas de códigos, y los problemas que conllevaban antes de
     la introducción de Unicode (1990).

4. `2026.04.15`

   - Codificación de datos (particularmente, de texto). Puntos de partida:
     - [The Absolute Minimum Every Software Developer Absolutely,
       Positively Must Know About Unicode and Character Sets (No
       Excuses!)](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
       (Joel Spolsky, 2003)
     - Cada decodificación _debe ser vista_ como una transformación → un
       _punto de costura_. Debilidades de esperar una representación y
       recibir otra... (relación con el ataque presentado por Nicolás)
     - Normalización de datos antes/después de validación
     - _Overlong sequences_ → Un mismo _codepoint_ Unicode puede ser
       representado por distintas secuencias de bytes, utilizando “overlong
       sequences” → [From Unicode to Exploit: The Security Risks of
       Overlong UTF-8
       Encodings](https://herolab.usd.de/the-security-risks-of-overlong-utf-8-encodings/)
       (Dominique Dittert, 2024)
     - [The Absolute Minimum Every Software Developer Must Know About
       Unicode in 2023 (Still No
       Excuses!)](https://tonsky.me/blog/unicode/) (Niki Tonsky, 2023)
     - [A Programmer’s Introduction to
       Unicode](https://www.reedbeta.com/blog/programmers-intro-to-unicode/)
       (Nathan Reed, 2017)
     - El caracter `/` (ASCII 47, hex 0x2F) puede ser representado con el
       byte `0x2F`, pero también con `0xC0 0xAF`
     - Un filtro que bloquea `..` para prevenir _directory traversals_ va a
       permitir `%C0%AE%C0%AE%C0%AF` (_overlong encoding_ de
       `../`). (CVE-2000-0884 IIS 4.0/5.0; viola RFC 3629)
     - Clases de caracteres equivalentes → Al normalizar caracteres
       _Fullwidth_ U+FF3C (`＼`) se convierte en U+5C (`\`) (CVE 2025-52488)

5. `2026.04.21`

   - Ya para cerrar con el tema de _codificación_...
     - Reordenamiento visual con marcadores `RTL`/`LTR` (U+200F RTL Mark,
       U+202E RTL override, U+202B RTL embedding, U+2067 RTL isolate; U+200E
       LTR mark, U+202A LTR embedding, U+202D LTR override, U+2066 LTR
       isolate)
     - Construcción de cadenas en el RDBMS con codificación numérica para
       lograr XSS → `(...) UNION SELECT
       CHAR(106,97,118,97,115,99,114,105,112,116)`

   - Algoritmos débiles de cifrado

   - POODLE (Padding Oracle On Downloaded Legacy Encryption) ⇒
     [CVE-2014-3566](https://www.cve.org/CVERecord?id=CVE-2014-3566)
	 - El cifrado orientado a bloques y los [_modos_ de operación del
       cifrado](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
   - [95% of HTTPS servers vulnerable to trivial MITM
     attacks](https://www.netcraft.com/blog/95-of-https-servers-vulnerable-to-trivial-mitm-attacks)
     (Netcraft, 2023)
   - [What's in a Downgrade? A Taxonomy of Downgrade Attacks in the TLS
     Protocol and Application Protocols Using
     TLS](https://arxiv.org/abs/1809.05681)
   
6. `2026.04.23`

   - _Ataques a la cadena de suministros_ (_“supply chain”_)
   
     - Ken Thompson, 1983: _«[Reflections on trusting
       trust](https://dl.acm.org/doi/pdf/10.1145/358198.358210)»_

	   - 20 años más tarde, el panorama... no es que hubiera mejorado:
         [Reflections on trusting trust
         revisited](https://dl.acm.org/doi/pdf/10.1145/777313.777347)
         (Spinellis, 2003)

       - Debería ser suficiente comparar el resultado de dos compiladores
         independientes... ¡Pero no! [A Mysterious Hacker Group Is On a
         Supply Chain Hijacking
         Spree](https://www.wired.com/story/barium-supply-chain-hackers/)
         (Greenberg, 2019)

	   - [Reflections on trusting distributed
         trust](https://dl.acm.org/doi/abs/10.1145/3563766.3564089)
         (Dauterman et al., 2022)

       - [PwnPilot: Reflections on Trusting Trust in the Age of Large
         Language Models and AI Code
         Assistants](https://ieeexplore.ieee.org/abstract/document/10487488)
         (PwnPilot: Reflections on Trusting Trust in the Age of Large
         Language Models and AI Code Assistants, 2023)

     - Primer ataque conocido: Suplantación de PKZIP en BBSes
       (1990.05.12). [Carta de aviso de
       PKWare](https://mirrors.apple2.org.za/www.textfiles.com/bbs/KEELYNET/UNCLASS/warning.asc).
       - Incluía suplantación de identidad contra la verificación de
         firmas: PKZIP Auto-Verification Feature..
       - Otro caso similar (1995):
         [Trojan.Win32.PKZ300b](https://threats.kaspersky.com/en/threat/Trojan.Win32.PKZ300b/)

     - Ataques a cajeros automáticos (ATMs): [Tyupkin: manipulating ATM
       machines with
       malware](https://securelist.com/tyupkin-manipulating-atm-machines-with-malware/66988/)
       (Kaspersky SecureList, 2014),
       [GreenDispenser](https://www.proofpoint.com/us/threat-insight/post/Meet-GreenDispenser)
       (Thoufique Haq, 2015)

7. `2026.04.28`

     - 2020: Filtrado de datos del gobierno de EUA con Solarwinds, mediante
       la consola de administración de red _“Orion“_
	   - [SolarWinds, Probably Hacked by Russia, Serves White House,
         Pentagon,
         NASA](https://www.newsweek.com/solar-winds-probably-hacked-russia-serves-white-house-pentagon-nasa-1554447)
         (Cristina Zhao, Newsweek, 2020)
       - [Scope of Russian Hacking Becomes Clear: Multiple U.S. Agencies
         Were
         Hit](https://www.nytimes.com/2020/12/14/us/politics/russia-hack-nsa-homeland-security-pentagon.html)
         (New York Times, 2020)
       - [Pompeo says Russia 'pretty clearly' behind cyberattack on US, but
         Trump casts doubts and downplays
         threat](https://www.usatoday.com/story/news/politics/2020/12/18/russian-cyber-attack-worst-may-yet-come-solarwinds-hacking/3956223001/)
       - [What is
         Solorigate](https://www.cybersecurity-insiders.com/what-is-solorigate/)
         (Naveen Goud, 2021)

     - _Typosquatting_ en NPM: [Massive npm Malware Campaign Leverages
       Ethereum Smart Contracts To Evade Detection and Maintain
       Control](https://socket.dev/blog/massive-npm-malware-campaign-leverages-ethereum-smart-contracts)
       (Pandya et al., 2024). [Algunos de los nombres utilizados en la
       campaña](https://gist.github.com/masteryoda101/d4e90eb8004804d062bc04cf1aec4bc0).

	 - [Shai Hulud y la “nueva ola” de ataques a
       NPM](https://unit42.paloaltonetworks.com/monitoring-npm-supply-chain-attacks/)

     - 2024: puerta trasera en _XZ Utils_

	   Uno de los primeros ataques con _sofisticación y planeación_ de
       varios años. _XZ_ es una biblioteca de compresión LZMA muy
       ampliamente utilizada en el software libre. Su (único) desarrollador
       activo, Lasse Collin, no respondía activamente a solicitudes
       relacionadas con el proyecto. Un desarrollador llamado _Jia Tan_ fue
       haciendo contribuciones menores entre 2021 y 2024, hasta ganar
       acceso de _commit_ al proyecto.

	   _Jia Tan_ introdujo una vulnerabilidad _oculta_, no en el código en
       Git, sino que en el _tarball_ con la distribución oficial. Permite,
       interactuando con _OpenSSH_, ganar acceso de root sin pasar por una
       etapa de autenticación.

	   El desarrollador de Microsoft y PostgreSQL Andres Freund detectó
       pequeñas desviaciones del tiempo normal en una serie de pruebas, lo
       que lo llevó a encontrar esta anomalía. La vulnerabilidad
       introducida estuvo presente sólo en las versiones 5.6.0 y 5.6.1, que
       no llegaron a ninguna distribución estable de Linux (aunque sí a la
       rama de desarrollo de varias distribuciones).
	   
	   Mis alumnos de licenciatura Isaac Jareth Campos y Alejandro Martínez
       hicieron una bastante buena presentación sobre el [ataque a la
       cadena de suministro con
       xz](https://www.youtube.com/watch?v=YtLjNY7TWfM). Los invito a
       verla.

     - 2026: eScan updates. La compañíá de antivirus _eScan_ fue
       comprometida; los atacantes se hicieron del control de servidores
       recionales de actualización, dando actualizaciones contaminadas a los
       clientes. El ataque se centró en Asia sud-oriental, y duró poco más
       de una hora. [Threat Bulletin: Critical eScan Supply Chain
       Compromise](https://www.morphisec.com/blog/critical-escan-threat-bulletin/)
       (Gorelik, 2026)
