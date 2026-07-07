# Sistema Inteligente de Análisis de Sentimiento e Impacto Financiero

## Arquitectura de Datos Automatizada con ETL en KNIME e Inferencia de Modelos de Lenguaje (IA)

Este repositorio contiene la solución avanzada y definitiva del sistema automatizado de monitoreo reputacional y gestión de riesgo temprano. La solución integra un pipeline de datos dinámico que extrae información de mercados financieros en tiempo real, la procesa mediante técnicas de Inteligencia Artificial (LLMs) y despliega los resultados analíticos en un dashboard interactivo en la nube de forma centralizada.

---

## 🚀 ¿Qué hace el proyecto?

El sistema automatiza el flujo completo de toma de decisiones financieras a través de tres fases integradas:
1. **Ingesta Dinámica:** Captura titulares de noticias y alertas de mercado actualizadas desde **Yahoo Finance** consolidadas en **Google Sheets**.
2. **Procesamiento de Lenguaje Natural (NLP con IA):** Analiza sintácticamente y extrae de forma simultánea el **Sentimiento** (Positivo, Neutral, Negativo), el nivel de **Impacto/Riesgo** (Alto, Medio, Bajo) y la **Entidad Corporativa clave** afectada, utilizando modelos de lenguaje masivos (LLMs) a través de API.
3. **Visualización Ejecutiva:** Exporta y despliega las métricas en un Dashboard interactivo (Vercel) con capacidades de filtrado cruzado en vivo para analistas de riesgo.

---

## 🎯 ¿Para qué sirve?

Actúa como una herramienta de soporte crítico para la mitigación de riesgos operativos, de mercado y reputacionales en el sector corporativo y financiero. Al reemplazar los diccionarios locales estáticos por inferencia cognitiva de IA, la solución:
* Identifica alertas tempranas críticas (ej. variaciones de mercado, reportes de ganancias, hackeos o multas) eliminando el sesgo humano.
* Categoriza con precisión matices de lenguaje que herramientas tradicionales no pueden interpretar.
* Permite a los analistas filtrar visualmente el universo de noticias haciendo clic directo en gráficos dinámicos para aislar amenazas urgentes en segundos.

---

## 🛠️ Arquitectura de la Solución (Pipeline Avanzado)

A diferencia de las versiones iniciales de desarrollo (MVP), esta solución despliega una infraestructura robusta, integrada y escalable construida sobre **KNIME Analytics Platform 5** que ejecuta las siguientes etapas:

1. **Conexión API e Ingesta:** Lectura automatizada de la base de noticias desde Google Sheets conectada a Yahoo Finance.
2. **Orquestación del Prompt y Request:** Construcción de prompts estructurados y parametrizados para forzar respuestas estrictamente en formato de datos intercambiables (JSON).
3. **Consumo del Motor de IA vía OpenRouter:** Envío y recepción de peticiones HTTP POST centralizadas a través del agregador de inferencia **OpenRouter**, utilizando el modelo **DEEPSEEK** como motor de Inteligencia Artificial principal para garantizar baja latencia y alta precisión contextual.
4. **Sanitización de Markdown y Extracción Estructurada:** Procesamiento inteligente del texto mediante manipulación de cadenas de caracteres para limpiar los bloques de código y parseo nativo con nodos `JSON Path`, aislando las variables de negocio en columnas independientes sin necesidad de desestructuraciones manuales.
5. **Mapeo de Alertas Visuales:** Inyección de reglas de negocio cromáticas basadas en criticidad (Semáforos de Impacto) mediante el nodo `Color Manager`.
6. **Pipeline de Producción Unificado (Continuous Deployment):** Consolidación de datos orientada a un único arreglo JSON (`Table to JSON`) y persistencia automatizada (`JSON Writer`) dentro del mismo repositorio del proyecto. Al realizar un único `git push`, GitHub centraliza los artefactos del backend (workflow de KNIME) y del frontend (`index.html`), provocando que Vercel actualice el Dashboard en producción de forma inmediata al leer el JSON de manera local.

** Acceso a la fuente de datos en vivo:** Podés auditar la estructura de ingesta y las alertas capturadas de Yahoo Finance directamente en este Enlace al Google Sheets de Monitoreo.

https://docs.google.com/spreadsheets/d/1O5MLwNmcJ-I7LjdA-XVGH-y_xB7dCinfSN46SjoI5uE/edit?usp=sharing

**Links a los repositorios de GitHub**

https://github.com/veledaandres-ai/analisis-sentimiento-AI
https://github.com/veledaandres-ai/analisis-sentimiento-dashboard

---

## 💻 Requisitos e Instalación

Para replicar, auditar o ejecutar el workflow de datos localmente:

1. **Descarga el Workflow:** Descarga el archivo de flujo de trabajo disponible en este repositorio.
2. **Prepara KNIME:** Abre **KNIME Analytics Platform** (Versión 5.x o superior).
3. **Importa el Proyecto:** Ve a `File` -> `Import KNIME Workflow...` y selecciona el archivo descargado.
4. **Configura tus Credenciales:** Abre el nodo de conexión HTTP/API e ingresa tu API Key de **OpenRouter** correspondiente para habilitar las llamadas de inferencia del modelo configurado.
5. **Ejecuta el Pipeline:** Haz clic en **Execute All** para procesar la ingesta actual de Google Sheets, correr la inferencia y exportar el archivo actualizado `noticias.json`.

---

## 📊 Visualización de Resultados

El entregable final cuenta con un frontend moderno desplegado en **Vercel** que lee directamente la salida estructurada de este repositorio:
* **KPIs en tiempo real:** Contadores automáticos de volumen y polaridad del mercado sin desajustes de idioma.
* **Filtros cruzados interactivos:** Al presionar sobre el gráfico de distribución de sentimientos (Barras) o de proporción de impacto (Dona), la tabla de monitoreo inferior se filtra instantáneamente en caliente.
* **Semáforos de riesgo:** Bordes de fila codificados por colores (Rojo para Impacto Alto, Amarillo para Medio, Verde para Bajo) imitando el diseño analítico del *Table View* corporativo de KNIME.

**Link al dashboard deployado en Vercel**
https://analisis-sentimiento-dashboard.vercel.app/

---
*Este desarrollo representa la consolidación final de la solución en un repositorio único integrado, demostrando el potencial de acoplar plataformas ETL visuales con capacidades modernas de Inteligencia Artificial y despliegue continuo (CI/CD) para el análisis de mercados financieros.*