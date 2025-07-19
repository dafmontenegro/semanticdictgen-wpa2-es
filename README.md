# semanticdictgen-wpa2-es

Análisis y Generación de Diccionarios Semánticos para la Criptoanálisis de Contraseñas WPA2 en Lengua Española

**Universidad Nacional de Colombia**  
Introducción a la Criptografía y Seguridad  
Julio 2025 - Bogotá

## Descripción

Este proyecto explora y desarrolla un método alternativo al enfoque tradicional de ataque por fuerza bruta para romper claves de WPA2 mediante el uso de contraseñas semánticas en el contexto del lenguaje español. Tradicionalmente, las contraseñas de redes Wi-Fi, como las de WPA2, son seleccionadas de manera que pueden ser fáciles de recordar para los usuarios pero, en muchos casos, son relativamente débiles cuando se consideran a través de un enfoque semántico.

En lugar de realizar ataques por fuerza bruta a través de todas las combinaciones posibles (que puede llevar años debido a la vastedad de combinaciones de caracteres), nuestro enfoque se centra en un ataque semántico que emplea el conocimiento del lenguaje y las frecuencias estadísticas de las palabras para generar diccionarios de contraseñas más efectivas y eficientes.

## Planteamiento del Problema

En el contexto de WPA2, una contraseña típica está limitada a 63 caracteres. Para contraseñas en formato ASCII, la cantidad de combinaciones posibles crece exponencialmente con la longitud de la contraseña. Por ejemplo, una contraseña de longitud 10 tiene un espacio de búsqueda de aproximadamente 256⁸ + 256⁹ + 256¹⁰ ≈ 1.21 · 10²⁷ combinaciones, lo que hace que un ataque de fuerza bruta sea computacionalmente costoso, a menudo inviable.

Sin embargo, las contraseñas semánticas, aunque más cortas y más fáciles de recordar, son más susceptibles a un enfoque de análisis semántico que utilice patrones estadísticos y lingüísticos.

## Objetivos

El proyecto tiene como objetivo desarrollar un sistema semántico de generación de diccionarios de contraseñas basado en el análisis de un corpus en español, como el CREA de la Real Academia Española (RAE), con el fin de optimizar los ataques a contraseñas de WPA2.

### Objetivos Específicos

1. **Extracción de Frecuencias del Corpus**: Utilizar el CREA u otros corpus representativos del lenguaje en español para obtener las frecuencias de aparición de las palabras y símbolos más comunes.

2. **Generación de Diccionarios Semánticos**: Utilizar técnicas avanzadas de embedding de palabras, como los modelos RAG o Word2Vec, para vectorizar términos y encontrar palabras semánticamente relacionadas entre sí.

3. **Permutaciones de Términos**: Crear diccionarios que no solo incluyan palabras con alta frecuencia en el corpus, sino también sus variantes semánticas y estructurales, como combinaciones de nombres, números y caracteres especiales.

4. **Evaluación de Rendimiento**: Evaluar la eficiencia de los diccionarios generados a través de pruebas de laboratorio, utilizando herramientas como Hashcat.

## Metodología

### Extracción de Datos del Corpus

Se utilizará el CREA (Corpus de Referencia del Español Actual) de la RAE u otros recursos lingüísticos para obtener un conjunto representativo de palabras en español. La frecuencia de cada término en el corpus será calculada, y los términos más comunes se extraerán como punto de partida para la construcción del diccionario.

### Técnicas de Embedding Semántico

Para generar un diccionario con términos que no sólo sean frecuentes sino también semánticamente relevantes, se emplearán modelos de embeddings de palabras como RAG (Retrieval-Augmented Generation) o nomic. Estos modelos permitirán:

- Vectorizar las palabras del corpus para obtener su representación semántica
- Establecer relaciones de cercanía entre términos, permitiendo encontrar palabras sinónimas, relacionadas o de contexto similar
- Crear diccionarios de términos que, además de ser frecuentes, sean semánticamente afines

### Generación del Diccionario

A partir de la lista de palabras más frecuentes y sus embeddings, se generarán diccionarios semánticos que incluirán:

- **Palabras frecuentes**: Basadas en las posiciones más altas de la lista de frecuencia
- **Palabras relacionadas semánticamente**: Utilizando las relaciones de proximidad entre los términos extraídos del modelo de embeddings
- **Combinaciones de palabras**: Se explorarán combinaciones que incluyan nombres, números y signos de puntuación

### Evaluación de la Eficiencia

Una vez generado el diccionario, se llevará a cabo una prueba de laboratorio en la que se capturará un handshake WPA2 encriptado, de preferencia con una contraseña conocida, para evaluar la efectividad del diccionario.

- Se utilizará Hashcat para realizar el ataque, comparando el tiempo que tardaría en romper la contraseña utilizando el diccionario semántico frente a un ataque tradicional de fuerza bruta
- El tiempo estimado de ejecución permitirá hacer una comparación entre ambos métodos y determinar la viabilidad del enfoque semántico

## Resultados Esperados

Se espera que el diccionario semántico sea significativamente más eficiente que un ataque de fuerza bruta tradicional. En particular, se anticipa que:

- Las contraseñas basadas en combinaciones semánticas, como nombres comunes seguidos de números o caracteres especiales, sean mucho más fáciles de romper utilizando el enfoque semántico
- La comparación de tiempos entre los dos enfoques permitirá visualizar el ahorro en recursos computacionales y tiempo, que podría ser considerable

## Trabajo Futuro

Futuras líneas de trabajo podrían incluir:

- Ampliar el análisis a otros idiomas y corpus más amplios
- Incorporar métodos de aprendizaje profundo para mejorar las predicciones semánticas
- Desarrollar herramientas automáticas para la generación de diccionarios de contraseñas semánticas adaptados a diferentes lenguas y contextos

## Referencias

- [Real Academia Española - CREA](https://www.rae.es/banco-de-datos/crea): Corpus de Referencia del Español Actual
- [LangChain RAG](https://python.langchain.com/docs/concepts/rag/): Retrieval Augmented Generation
- [Hashcat](https://hashcat.net/hashcat/): Advanced password recovery
- [Nomic AI](https://www.nomic.ai/blog/posts/nomic-embed-text-v1): Nomic Embed - Truly Open Embedding Model

---

⚠️ **Nota Ética**: Este proyecto tiene fines educativos y de investigación en ciberseguridad. Su uso debe cumplir con todas las leyes y regulaciones locales aplicables.