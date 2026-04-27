# Material cursado durante el mes de marzo

## _Unidad 2_: El panorama de la seguridad informática hoy

1. `2026.03.03`

   - Evaluación de los modelos de riesgo FMEA / OCTAVE Allegro realizados
     por los alumnos

   **Otros temas:**

   _Ligeramente_ vinculado con el tema visto anteriormente (modelos de
   riesgo): Matthew Garrett publicó un texto acerca de la [confianza sobre
   los _blobs_
   binarios](https://codon.org.uk/~mjg59/blog/p/to-update-blobs-or-not-to-update-blobs/)
   que se distribuyen, típicamente para ejecutar en procesadores
   _no-primarios_ de nuestro equipo de cómputo (simplificando
   fuertemente). Esto se conecta con una [discusión al respecto que se está
   teniendo](https://lists.debian.org/debian-devel/2026/02/threads.html#00297)
   (...otra vez 🙄) en Debian. Considero que es un tema interesante para el
   grupo actual para dedicarle un poco de plática 🙂

2. `2026.03.05`

	**Modelos de ataque**

	Los modelos de riesgo que vimos en las clases anteriores sirven para
    identificar nuestros _principales activos_ y las _amenazas_ que puede
    haber sobre ellos — _qué queremos o requerimos proteger_.

	En contraste, los modelos de ataque catalogan y describen _Tácticas,
    Técnicas y Procedimientos_ que utilizan nuestros adversarios para
    comprometer nuestra información. Consisten _conocimiento especializado
    y estructurado_, ya específico al área de seguridad informática, sobre
    el _comportamiento real_ y desde una _perspectiva adversarial_,
    permitiéndonos avanzar de una _defensa reactiva_ (corregir
    vulnerabilidades detectadas) a una _defensa proactiva_ (anticipar y
    detectar campañas de ataque).

    - [Lockheed Martin Cyber Kill
      Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
      (_Cadena de Ataque Cibernético_) desarrollado como parte del modelo
      _Intelligence Driven Defense_ para identificar y prevenir actividad
      de intrusiones (2011). Identifica los pasos que un adversario debe
      seguir para montar un reto APT (/Advanced Persistent Threat/), para
      ayudar al defensor a _romper la cadena_:

	  1. Reconocimiento
	  2. Armamento o _armificación_ (_weaponization_)
	  3. Entrega
	  4. Explotación
	  5. Instalación
	  6. Control y Comando (C2)
	  7. Acción sobre los objetivos

	  Ojo: Hay críticas importantes al modelo:

	  1. Es un modelo muy _lineal y secuencial_
      2. Se enfoca demasiado en APTs, omite muchos otros tipos de amenaza,
         incluyendo ataques internos o robos de identidad
      3. Falta de contexto post-explotación

    - [Microsoft
      STRIDE](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats#stride)
      ayuda a modelar y clasificar amenazas y ataques para tenerlos
      presentes de forma preventiva, enfocado a aplicarlo conforme se
      **desarrolla** un sistema (y no cuando éste ya está
      **desplegado**). STRIDE toma su nombre de _**S**poofing,
      **T**ampering, **R**epudiation, **I**nformation disclosure,
      **D**enial of service, **E**levation of privileges_, las seis
      categorías de amenazas que un desarrollador debe considerar al
      desarrollar cualquier componente.

	  Para aplicar STRIDE es necesario seguir una metodología de desarrollo
      con un componente visual, como lo hace la [Herramienta de Modelado de
      Amenazas](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-getting-started),
      en que cada uno de los tipos de objeto representados _responde_ a
      determinadas categorías de amenazas (Procesos (Círculos) ⇒ T,R,I,D,E;
      Flujos de Datos (Flechas) ⇒ T,I,D; Almacenes de Datos (Líneas) ⇒
      T,R,I y a veces D; Entidades Externas (Rectángulos) ⇒ S).

    - [MITRE ATT&CK](https://attack.mitre.org/) _Adversarial Tactics,
      Techniques, and Common Knowledge_ (2013–, actualización bianual)
      detalla técnicas para distintos entornos, describiendo el _cómo_ y
      _por qué_ de _cada paso_ en el ciclo de vida de un ataque.

	  Surge de cierta manera reaccionando ante el _Cyber Kill Chain_,
      describiendo el modelo de ataque ya no como una _cadena_, sino como
      un _laberinto_, con múltiples posibilidades a cada paso. Si Cyber
      Kill Chain da las 7 fases de un crimen (vigilar, entrar, robar,
      huir...), ATT&CK es el manual que usan los detectives, lleno de
      huellas dactilares, _modus operandi_ de cada ladrón, las herramientas
      que usan para forzar cerraduras y cómo se mueven dentro de la casa
      una vez que han entrado, etc.

	  Se ha convertido en el estándar de facto para describir el
      comportamiento de los atacantes después de la intrusión inicial. Es
      una matriz detallada de tácticas (el "por qué") y técnicas (el
      "cómo") que los adversarios utilizan.

3. `2026.03.10`

	**Modelos de ataque** (continúa)

    - [MITRE D3FEND](https://d3fend.mitre.org/) siguiente paso natural de
      ATT&CK: «gráfica de conocimiento de contramedidas de ciberseguridad»

	  D3FEND parte de una matriz similar a la de ATT&CK, pero los
      encabezados de primer nivel van relacionados a las necesidades de
      defensa (modelar, fortalecer, detectar, aislar, engañar, eliminar,
      restaurar). Genera además un modelo gráfico y navegable de
      _relaciones inferidas_ entre acciones defensivas, acciones ofensivas
	  y objetos de sistema, y para cada categoría vincula a fuentes de
      información (artículos académicos, patentes, artículos en Web,
      lineamientos, referencias técnicas etc.) relacionados.

	- [_Common Vulnerabilities Enumeration_ (CVE)](https://www.cve.org) es
      una base de datos de vulnerabilidades específicas, en software
      específico (y en _versiones_ específicas), que se elabora [desde
      1999](https://www.cve.org/Resources/General/Towards-a-Common-Enumeration-of-Vulnerabilities.pdf)
      y es gestionado (¡también!) por MITRE. Busca dar una _nomenclatura
      consistente_ a las vulnerabilidades reportadas, mantener una base de
      datos de _vulnerabilidades similares_, atender _múltiples
      perspectivas sobre la evolución_ de cada vulnerabilidad, y proveer un
      mapeo entre bases de datos del campo.

	  Al día de hoy, CVE es un estándar donde desarrolladores y usuarios de
      software y de infraestructura dan seguimiento a los reportes sobre
      sus productos; hay un [proceso para la publicación y
      seguimiento](https://www.cve.org/About/Process) de estos reportes.

	- [CWE](https://cwe.mitre.org/) (_Common Weaknessses Enumeration_) es
      otra base de datos mantenida por MITRE, enumerando la _clase de
      fallos_ que permite cada una de las vulnerabilidades detalladas por
      CVE. Presentan una taxonomía jerárquica de vulnerabilidades.

	  Los ejemplos de CWE frecuentemente incluyen código mínimo
      demostrativo. Me parece interesante que presenta _notas de mapeo de
      vulnerabilidad_, para referencias cruzadas con otras bases de datos;
      uno de los vectores de clasificación es si el uso para mapeo es
      _permitido_ (si es suficientemente específico) o _prohibido_ (si es
      demasiado general,
      p.ej. [CWE-1076](https://cwe.mitre.org/data/definitions/1076.html),
      [CWE-1101](https://cwe.mitre.org/data/definitions/1101.html)).

## Unidad 3: Tipos de ataque

1. `2026.03.12`

   **Tipos de ataque**

	Comenzamos a desarrollar este tema siguiendo el material que tengo en
    el repositorio de Inv. Económicas: [Tipos de
    ataque](https://ru.iiec.unam.mx/4047/1/tipos_de_ataque.pdf)
	
	En esta sesión hablamos de diferentes aspectos de las **negaciones de
    servicio** (DoS):
	- Directo (saturación de ancho de banda)
	- Abuso de la pila de red (_SYN flood_)
	- Saturación de aplicación por solicitudes simples
	- Amplificación y reflexión
    - Negaciones de servicio distribuidas (DDoS) → _botnets_ y otros
      mecanismos de _Command and Control_
    - Negación de servicio a puntos únicos de fallo (SPoF) en
      infraestructuras compuestas

2. `2026.03.17`

	Nos adentramos un poco en el mágico mundo de los _desbordamientos_:

	- ¿Qué es un desbordamiento de _buffer_? (caso específico: de _cadenas_
      - ¿Qué es una cadena en C?
	- Estructura básica de los procesos: Texto, datos, _heap_ y _stack_
    - Uso del depurador (`gdb`) para inspeccionar la memoria de un proceso
      _vivo_ y diseccionar un _ataque de desbordamiento de buffer_
    - Desbordamientos de pila: En los 1990s (saltar ejecutando hacia
      adentro del buffer) y hoy (sobreescritura de variables adyacentes,
      control _muy limitado_ del flujo de ejecución
      - Concepto de _return oriented programming_ (ROP)
    - Desbordamientos de enteros

3. `2026.03.19`

    - Desbordamientos de otros tipos de datos: Tiempo (Y2K, Y2K38...)

	Pasamos a hablar de las _inyecciones_

	- Buscar las _costuras_ entre distintos _materiales_ 😉
    - Inyecciones de SQL (y algunas mitigaciones)
      - Escapar las cadenas
	  - Cadenas preparadas

4. `2026.03.24`

    - Inyecciones de SQL (y algunas mitigaciones)
	  - Cadenas preparadas
	  - Mapeadores objeto-relacionales (ORMs)
    - Otras inyecciones
	  - Inyección de JavaScript, CSS en elementos HTML (_primera
        probadita_)

5. `2026.03.26`

    - Ingeniería social como _inyección_ de tipo de contenido
	  - ¿Cómo se determina el _tipo_ de un archivo?
	  - Ejemplos en que se oculta el verdadero tipo de un archivo al
        usuario (en nombre de la usabilidad)
    - Otras inyecciones
	  - Inyecciones de objetos → serialización — `pickle`,
        `Data::Dumper`. 
      - Alternativas (imperfectas): `JSON`, `YAML`
    - Planteamiento del ejercicio práctico: [¡Intentemos un
      ataque!](../../entregas/intentemos_ataque/README.md)
