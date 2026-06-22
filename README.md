# analisis-sentimiento-mvp
Fase 1: Pipeline nativo de procesamiento de texto y análisis léxico local en KNIME para titulares financieros.

# Sistema Léxico de Interpretación de Lenguaje Natural (NLP) para Riesgo Financiero

Este repositorio contiene la **Fase 1 (MVP)** del proyecto final para la Diplomatura. El objetivo del sistema es automatizar el monitoreo reputacional y la gestión de riesgo temprano mediante el análisis de sentimiento de titulares de noticias financieras.

## ¿Qué hace el proyecto?
El proyecto toma un listado estático de titulares de noticias de prensa escrita relacionados con entidades bancarias y, de manera 100% automatizada y local, determina si el impacto de la noticia es **Positivo** o **Negativo**.

## ¿Para qué sirve?
Sirve como una herramienta de soporte para la toma de decisiones y mitigación de riesgos operativos/reputacionales en el sector financiero. Al clasificar automáticamente grandes volúmenes de texto, reduce el tiempo de lectura manual de los analistas y permite identificar alertas tempranas (como hackeos, multas o variaciones de morosidad) de forma sistemática y sin sesgos humanos.

## Arquitectura del MVP (Procesamiento Nativo)
Esta primera versión funciona de manera nativa utilizando un **enfoque léxico basado en diccionarios locales** dentro de **KNIME Analytics Platform 5**.

El flujo de trabajo realiza los siguientes pasos:
1. **Ingesta y Aislamiento:** Carga de datos mediante `Excel Reader` y ocultamiento del "Ground Truth" para garantizar la objetividad del análisis.
2. **Tokenización:** Descomposicion de oraciones en palabras individuales (`Cell Splitter` y `Ungroup`).
3. **Clasificación Léxica:** Contraste de palabras contra un diccionario local (`Table Creator` y `String Replacer`).
4. **Consolidación:** Votación estadística por **Moda** (`GroupBy`) para definir el veredicto final de la noticia completa.

## ¿Cómo se usa?
1. Descarga el archivo `Pipeline_NLP_Nativo_Base.knwf` y el archivo de datos de muestra presentados en este repositorio.
2. Abre KNIME Analytics Platform (Versión 5 o superior).
3. Ve a `File` -> `Import KNIME Workflow...` y selecciona el archivo `.knwf`.
4. Abre la configuración del primer nodo (`Excel Reader`) y actualiza la ruta apuntando al archivo Excel de noticias en tu computadora.
5. Haz clic derecho sobre el último nodo (`GroupBy`) y selecciona **Execute** para ver la tabla de resultados procesada.

---
*Nota de Evolución del Proyecto: Esta versión constituye la línea de base analítica (Baseline). La Fase 2 del desarrollo será alojada en un repositorio independiente para contrastar el rendimiento de estas reglas locales frente a una integración avanzada con Modelos de Lenguaje Masivos (LLMs) vía API.*
