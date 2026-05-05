# Material cursado durante el mes de mayo

# Unidad 3: Tipos de ataque

1. `2026.05.05`

   - **¿Y qué hay de los LLMs?**

     En el transcurso de esta unidad vimos varias maneras de atacar
     software de distintos tipos, mayormente bajo arquitecturas
     cliente-servidor. Ante el actual auge y aparente omnipresencia de los
     _modelos grandes de lenguaje_ (LLMs), también tenemos que abordar el
     tema.
	 
	 Algunos textos para iniciar la exploración:

     - [OWASP Top 10 forLLM Applications
       2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-v2025.pdf)
       (OWASP, 2025) presenta una muy buena taxonomía de los tipos de
       ataque que pueden montarse a un modelo LLM, desde los más sencillos
       (_“ignora las instrucciones anteriores y...”_) hasta los más
       complejos y –al momento de la publicación– recientes. Para cada
       clase de ataque incluye descripción, ejemplos comunes, estrategias
       de prevención y mitigación, y escenarios posibles de ataque.

     - [Not What You’ve Signed Up For: Compromising Real-World
       LLM-Integrated Applications with Indirect Prompt
       Injection](https://dl.acm.org/doi/epdf/10.1145/3605764.3623985)
       (Greshake, Abdelnabi et al. 2004) presenta el razonamiento y varios
       esquemas mediante los cuales un sistema automatizado puede explotar
       la integridad de un sistema basado en LLMs.

	 - [Unique Security and Privacy Threats of Large Language Models: A
       Comprehensive Survey](https://dl.acm.org/doi/full/10.1145/3764113)
       (Wang, Zhu et al. 2025) realiza una revisión del campo de los
       modelos de amenazas tocantes a privacidad y seguridad en entornos
       relacionados con LLMs, clasificando los artículos referidos sobre
       ejes relativos a las distintas etapas operativas de dichos sistemas.

     - Temas a abordar propuestos... por un LLM:
       - **Prompt Injection** - La Inyección del Siglo XXI
	     - **Direct prompt injection**: "Ignora instrucciones previas y haz
           X"
         - **Indirect prompt injection**: Datos maliciosos en fuentes que
           el LLM consume (web scraping, emails, documentos)
         - **Jailbreaking**: Técnicas como "Do Anything Now" (DAN),
           "Role-playing", "Base64 encoding", "Translation attacks"
       - **Data Poisoning** - Envenenamiento del Modelo
         - **Envenenamiento de datos de entrenamiento** (compromiso de
           cadena de suministro del modelo)
         - **Backdoor attacks**: Insertar comportamientos específicos
           activables por triggers
         - **Inyección de información falsa en RAG** (Retrieval-Augmented
           Generation)
       - **Model Inversion y Extracción de Datos**
         - **Extracción de datos de entrenamiento sensibles** (PII,
           secretos, código propietario)
         - **Reconstrucción de ejemplos de entrenamiento** mediante queries
           específicas
         - **Inferencia** de arquitectura y parámetros del modelo
       - **Adversarial Attacks**
         - **Suffix attacks**: Añadir sufijos aparentemente sin sentido que
           rompen el alignment
         - **Token manipulation**: Modificaciones mínimas en input que
           causan salidas dañinas
         - **Gradient-based attacks**: Uso de accesos a logits o gradientes
           para construir adversarial examples
       - **Denegación de Servicio y Abuso Económico**
         - **Prompt flooding**: Consumo masivo de tokens para agotar cuotas
           y recursos
         - **Recursive prompts**: Bucles de auto-invocación que nunca
           terminan
         - **Cost exhaustion attacks**: Forzar procesamiento de contextos
           extremadamente largos
       - **Model Theft** y Extracción por API
         - **Extracción de capacidades** del modelo mediante consultas
           repetidas
         - **Entrenamiento de modelos "estudiantes"** que imitan al modelo
           objetivo
         - **Reverse engineering de prompts del sistema** mediante
           interacción
