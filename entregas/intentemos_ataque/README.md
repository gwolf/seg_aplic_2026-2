## Actividad práctica: ¡Intentemos un ataque! (a uno mismo)

**Entrega:** 2026.03.09 (jueves)

En el transcurso del último mes, hemos pasado de hablar de _los atributos
generales_ de la seguridad en cómputo y de _modelos de riesgos/ataques_ que
pueden aplicarse en cualquier entorno no-computacional para ir
_aterrizando_ nuestro conocimiento. Comenzamos a analizar técnicas
específicas de explotación de vulnerabilidades.

### Objetivo

Que cada quien experimente —en carne propia, pero en un entorno controlado—
el ciclo completo de una vulnerabilidad real: desde encontrarla en las
bases de conocimiento que vimos (CVE, CWE), pasando por entender _qué tipo
de fallo_ la hace posible, hasta intentar explotarla uno mismo.

La idea es que dejemos de lado la visión puramente defensiva por un momento
y nos pongamos el sombrero del atacante (con todas las precauciones éticas,
claro: como ya lo hemos platicado en clase, y viene bien contar con la
experiencia de primera mano de un perito forense, no podemos darnos el lujo
de atacar a terceros). Así, lo que vimos en los modelos de ataque (Cyber
Kill Chain, STRIDE, MITRE ATT&CK) cobra sentido _en la práctica_, no solo
en el papel.

## Instrucciones generales

### 1. Selección del CVE

Cada quien va a elegir **un CVE publicado en los últimos cinco años**
(2021–2026). El criterio de selección es libre, pero les sugiero que
consideren:

- Que el software afectado sea _instalable_ en su equipo o en una VM sin
  volverse locos 🤓
- Que haya documentación técnica suficiente para entender qué está pasando
  (no todos los CVE son igual de amigables), pero no excesiva a fines del
  ejercicio (¡no seleccionen CVEs que incluyan directamente una
  demostración del ataque!)
- _Preferentemente_, que toque alguno de los temas que ya vimos:
  - Inyecciones (SQL, Javascript → XSS)
  - Desbordamientos (de buffer, stack, enteros o algún otro tipo de dato)
  - Aunque puede resultar un poco más complicado, _se vale_ que elijan
    algún que otro tipo de vulnerabilidad que les parezca interesante
    aunque no lo hayamos abordado en clase.

### 2. Análisis documental

Investiguen y escriban (a manera de bitácora):

- **El dato duro**: Número CVE, software afectado, versiones vulnerables.
- **El CWE asociado**: ¿A qué _clase de fallo_ corresponde esto? (Ojo: no
  todos los CVE tienen un mapeo directo a CWE, pero casi siempre hay uno
  implícito).
- **Descripción técnica** (con sus palabras): ¿En qué consiste la
  vulnerabilidad? ¿Qué condiciones tienen que darse para que sea
  explotable? ¿Qué impacto tiene (confidencialidad, integridad,
  disponibilidad, o combinaciones)?
- **Mapeo a modelos de ataque**: Ubiquen su CVE dentro de **al menos dos**
  de los modelos que vimos. Por ejemplo:
  - ¿En qué fase de _Cyber Kill Chain_ estaría la explotación?
  - ¿A qué categorías de _STRIDE_ corresponde esta amenaza?
  - ¿Qué tácticas y técnicas de _MITRE ATT&CK_ estarían involucradas? (Si
    el CVE ya tiene mapeo público en ATT&CK, mejor; si no, busquen técnicas
    que apliquen)

### 3. Configuración del entorno de pruebas

No vamos a hacer esto en nuestra máquina _de diario_, ¿no? Mejor:

- Usen una máquina virtual, un contenedor, o —si tienen confianza— una
  máquina dedicada que puedan aislar. La regla de oro: **si algo sale mal,
  que solo se rompa el entorno de pruebas**.
- Instalen la versión vulnerable del software. Documenten el proceso (a
  veces conseguir versiones viejas es más complicado de lo que parece — si
  encuentran _workarounds_, anótenlos).

### 4. Explotación controlada

Ahora sí: reproduzcan el ataque.

Pueden usar herramientas variadas:

- *`gdb`* para desbordamientos, aunque requerirá que tengan acceso al
  código fuente y compilen con los símbolos de depuración (`-g`)
- alguna herramienta como _Metasploit_ para automatizar inyecciones SQL,
  etc.
- Scripts a medida que encuentren vinculados con el ataque


**Ojo:** si usan algo que no escribieron ustedes, asegúrense de *entender
qué hace*. Documenten la fuente de donde lo obtuvieron.

**Manténganse únicamente como _sus propios_ adversarios**: Si la
vulnerabilidad implica afectar otros sistemas (por ejemplo, un ataque de
red), aíslenlo bien — la idea es atacarse _a uno mismo_, no al vecino.

### 5. Documentación de la evidencia

Aquí no vale decir "sí funcionó" y ya. Queremos verlo. Incluyan:

- Pantallazos del estado _antes_ del ataque (todo normal).
- Pantallazos _durante_ la explotación (ese momento en que algo se rompe —
  o se abre — como no debería).
- Pantallazos _después_ del ataque (ejecución de comandos no autorizados,
  acceso a información restringida, denegación de servicio, lo que
  aplique).
- Si usaron comandos o scripts, incluyan un registro (o al menos los
  comandos clave).

## Entregables

El informe puede ser en PDF, Markdown, o el formato que prefieran, pero
debe incluir:

1. **Resumen ejecutivo** (una o dos cuartillas máximo): ¿qué CVE eligieron,
   por qué, y qué pasó?
2. **Desarrollo** con los puntos 2, 3, 4 y 5 de las instrucciones.
3. **Análisis de mitigaciones**: Con lo que ya saben — ¿cómo se habría
   prevenido esto? Propongan **al menos dos estrategias de defensa**,
   vinculándolas con conceptos del curso: principio de menor privilegio,
   saneamiento de entradas, segmentación, etc.
   - **¿Podrían corregirlo?** No es un punto obligatorio, pero sí deseable:
     Si eligieron un CVE reciente, se trata de software libre (con
     disponibilidad de código fuente), y la versión “viva” del software no
     incluye la corrección aún... ¿Podrían apuntar a una solución?
   - ¿Podrían _contribuir un parche_ con la solución al proyecto desarrollado?
4. **Reflexión personal** (esto es importante): ¿Qué les dejó el ejercicio?
   ¿Qué diferencia hay entre leer sobre un ataque y ejecutarlo? ¿Algo les
   sorprendió?

## Consideraciones éticas y de seguridad

Esto no debería ni siquiera tener que decirlo, pero por si acaso:

- Este ejercicio se hace **únicamente en entornos propios y controlados**.
- **No** se intenta explotar sistemas ajenos sin autorización expresa.
- Si descargan scripts o herramientas, dense una vuelta por el código antes
  de ejecutarlo (nunca está de más).
- Si la vulnerabilidad requiere conectividad de red, aíslenla — una red
  virtual entre VMs es suficiente.

## Criterios de evaluación

| Criterio                                                           | Ponderación |
|--------------------------------------------------------------------|-------------|
| Selección del CVE y documentación técnica (punto 2)                | 20%         |
| Mapeo a modelos de ataque (Cyber Kill Chain, STRIDE, ATT&CK, etc.) | 20%         |
| Configuración del entorno y reproducción del ataque (puntos 3 y 4) | 20%         |
| Evidencia clara de explotación (punto 5)                           | 20%         |
| Análisis de mitigaciones y reflexión personal                      | 20%         |

---

**Nota final (importante)**: No todos los CVE son igual de fáciles de
explotar en un entorno doméstico. Algunos requieren configuraciones muy
específicas, hardware especial, o dependencias complicadas. Mi
recomendación: dediquen un rato a _explorar_ antes de comprometerse con
uno. Si ven que el CVE que eligieron está resultando más problemático de lo
esperado, avísenme con tiempo y vemos alternativas — el objetivo es que
aprendan, no que se atoren una semana con dependencias rotas.
