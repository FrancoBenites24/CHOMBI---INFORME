# Chombi: Motor de Rutas para la Digitalización del Transporte Informal Urbano
## Caso de Aplicación en Piura, Perú

**Curso:** Innovación y Transformación Digital  
**Universidad:** Universidad Tecnológica del Perú — UTP Piura  
**Fecha:** Abril 2026...

---

### Resumen
El presente trabajo propone **Chombi**, una solución tecnológica orientada a resolver la invisibilidad digital del transporte informal urbano en ciudades intermedias del Perú. En Piura, al igual que en la gran mayoría de ciudades latinoamericanas, las combis —vehículos de transporte público con rutas fijas, pero no oficializadas— no tienen presencia en ningún sistema digital de navegación. Esto obliga a los usuarios a depender exclusivamente del conocimiento popular transmitido de forma oral para movilizarse.

Chombi modela la red de combis como un **grafo dirigido y ponderado**, aplicando el **algoritmo de búsqueda A*** para calcular itinerarios óptimos entre un punto de origen y un destino dado, incluyendo tramos peatonales y transbordos. El dataset de rutas se construye mediante recolección directa en campo con registros GPX, constituyendo un activo de datos propietario y replicable. La propuesta fue estructurada como un Product Foundation Document (PFD) que incluye modelo conceptual, arquitectura técnica, estrategia de datos, modelo de negocio y hoja de ruta de implementación.

Los resultados evidencian que la combinación de recolección de datos de campo, modelado en grafos y algoritmos de búsqueda heurística permite construir un motor de rutas funcional sin depender de fuentes oficiales de datos de transporte. Chombi representa una innovación tecnológica con alto potencial de impacto social y escalabilidad a otras ciudades con sistemas de transporte informal.

**Palabras clave:** transporte informal, digitalización urbana, algoritmo A*, grafo dirigido, innovación tecnológica, Piura.

---

## 1. Introducción
El transporte urbano es uno de los pilares fundamentales de la vida cotidiana en las ciudades. Sin embargo, en el contexto peruano y latinoamericano, gran parte de los desplazamientos urbanos ocurren a través de sistemas informales que operan al margen de cualquier registro digital. Según estimaciones del sector, el transporte informal representa entre el 60% y el 85% de los viajes urbanos en ciudades intermedias del Perú, siendo Piura —con aproximadamente 500,000 habitantes— un caso representativo de esta realidad.

Las combis son el vehículo central de este sistema: unidades de transporte con rutas más o menos definidas, paraderos no señalizados oficialmente y sin ningún tipo de digitalización ni registro en plataformas de navegación como Google Maps. Esta ausencia digital no es un problema menor; representa una barrera de acceso a la movilidad eficiente para miles de usuarios diarios que dependen de este servicio.

Por ello, se propone **Chombi**, un motor de rutas diseñado específicamente para operar sobre datos de transporte informal, prescindiendo de fuentes oficiales inexistentes y construyendo en su lugar un dataset propietario a partir de trabajo de campo. La solución aplica conceptos de transformación digital, innovación en modelos de datos y algoritmos de búsqueda en grafos para resolver un problema con impacto directo en la calidad de vida de la población.

## 2. Objetivo General
Diseñar y estructurar Chombi como una solución tecnológica escalable para la digitalización del transporte informal urbano en Piura, mediante la construcción de un dataset propietario de rutas de combis y el desarrollo de un motor de rutas basado en el algoritmo A* sobre grafos dirigidos y ponderados, que permita a los usuarios obtener itinerarios paso a paso entre un punto de origen y un destino.

## 3. Objetivos Específicos
*   Recolectar y procesar datos de rutas de combis en la ciudad de Piura mediante recorridos en campo con registros GPS en formato GPX, construyendo el dataset inicial del sistema.
*   Modelar la red de transporte informal de Piura como un grafo dirigido y ponderado, con nodos representando paraderos y aristas representando segmentos de ruta y conexiones peatonales.
*   Implementar el algoritmo de búsqueda A* sobre el grafo construido para calcular rutas óptimas entre dos puntos arbitrarios, considerando múltiples criterios de optimización: tiempo, transbordos y distancia a pie.
*   Definir la arquitectura técnica del sistema, incluyendo las capas de datos, lógica de routing, API y frontend, con decisiones justificadas para la fase de Producto Mínimo Viable (MVP).
*   Identificar y analizar los huecos estratégicos del proyecto —monetización, protección del dataset, actualización del dato y riesgo de formalización— para orientar la toma de decisiones en fases posteriores.
*   Elaborar una hoja de ruta de producto que establezca fases, criterios de avance y métricas de éxito para guiar el desarrollo e implementación de Chombi.

## 4. Caso de Estudio: Problemática e Idea Innovadora

### 4.1. Contexto del problema
Piura es una ciudad intermedia del norte del Perú con aproximadamente 500,000 habitantes. Su sistema de transporte urbano opera predominantemente bajo el modelo de combis: vehículos que siguen rutas más o menos definidas, con paraderos informales y sin presencia en ningún sistema digital de información.

La invisibilidad digital del sistema de combis genera cuatro ausencias críticas:
1.  Las rutas no están digitalizadas.
2.  Los paraderos no tienen nombre ni ubicación oficial.
3.  No existe información sobre posibilidades de transbordo.
4.  La ausencia de tiempos estimados impide la planificación.

### 4.2. Por qué Google Maps no resuelve este problema
Google Maps depende del formato **GTFS** (General Transit Feed Specification), datos que deben ser provistos por operadores o municipalidades. En Piura, la informalidad no es un "bug", es la estructura permanente, lo que hace inviable la solución convencional.

### 4.3. La idea innovadora: Chombi
Chombi es un motor de rutas diseñado específicamente para operar sobre el transporte informal. Su propuesta de valor: *Google Maps no sabe que tu combi existe. Chombi sí.*

La innovación reside en tres dimensiones:
*   **Estrategia de datos:** Dataset propietario mediante registros GPX.
*   **Modelo técnico:** Modelado como grafo dirigido y algoritmo A*.
*   **Replicabilidad:** Diseñado para ser reproducido en cualquier ciudad similar.

## 5. Descripción del Problema

### 5.1. El grafo como modelo del problema
El sistema de combis de Piura se representa como un grafo dirigido $G = (V, E)$, donde:
*   **$V$ (Vértices):** Paraderos identificados.
*   **$E$ (Aristas):** Conexiones de ruta (tiempo de recorrido), peatonales (caminata) y de transbordo (penalización de espera).

El algoritmo **A*** resuelve la navegación encontrando el camino de menor costo mediante una heurística admisible basada en la distancia de Haversine.

### 5.2. Las cuatro ausencias críticas
El problema se resume en la falta de digitalización, identificación de paraderos, información de transbordos y estimaciones temporales.

### 5.3. El problema del dataset
El reto técnico principal no es el algoritmo, sino el dato. La solución es la recolección directa en campo con dispositivos GPS. A la fecha, se han mapeado 3 empresas de transporte, validando la metodología.

## 6. Resultados

### 6.1. Modelo conceptual y arquitectura técnica definidos
Se ha completado el **Product Foundation Document (PFD) v1.0**. La arquitectura consta de:
1.  **Capa de datos:** SQLite (con SpatiaLite) migrando a PostgreSQL.
2.  **Lógica de routing:** Python con NetworkX y algoritmo A*.
3.  **Capa de API:** FastAPI (REST).
4.  **Frontend:** PWA con Leaflet y bot de WhatsApp.

### 6.2. Dataset inicial y validación de metodología
Validación de la metodología con 3 empresas iniciales, confirmando que la recolección es viable y el costo controlable.

### 6.3. Modelo de negocio mapeado con huecos identificados
Se identificaron flujos de ingreso: freemium B2C, venta de datos B2B a transportistas, GTFS para municipalidades, y licenciamiento de API. La prioridad es validar el modelo B2B.

### 6.4. Hoja de ruta de cuatro fases
*   **Fase 0 (Sem 1-4):** Mapeo completo y prueba A* en consola.
*   **Fase 1 (Mes 2-3):** API funcional y bot de WhatsApp (50 usuarios beta).
*   **Fase 2 (Mes 3-5):** Frontend PWA y primer cliente B2B.
*   **Fase 3 (Mes 6-9):** Crowdsourcing, ingresos reales y playbook de expansión.

### 6.5. Huecos estratégicos documentados
Se identificaron retos en: validación de monetización, protección del dataset (abierto vs propietario), escalabilidad de recolección, actualización de datos y gestión del riesgo de formalización.

## 7. Conclusiones
Chombi demuestra que es posible digitalizar el transporte informal sin datos oficiales. El activo diferencial es el **dataset propietario**. La transformación digital aquí requiere primero resolver el problema del dato (trabajo de campo) y luego aplicar la tecnología. La escalabilidad es alta, con un potencial de expansión de 4 a 8 semanas por ciudad hacia Trujillo, Chiclayo, Arequipa y más allá.

## 8. Referencias
*   Behrens, R., McCormick, D., & Mfinanga, D. (Eds.). (2016). *Paratransit in African Cities: Operations, Regulation and Reform*. Routledge.
*   Cervero, R. (2000). *Informal Transport in the Developing World*. UNCHS.
*   Dekel, G., & Levy, N. (2012). *OpenTripPlanner: An open-source multimodal routing platform*. SOTM.
*   Goodall, W., et al. (2017). The rise of mobility as a service. *Deloitte Review*.
*   Hart, P. E., et al. (1968). A formal basis for the heuristic determination of minimum cost paths. *IEEE*.
*   Klopp, J. M., & Cavoli, C. (2019). Mapping minibuses in Maputo and Nairobi. *Transport Reviews*.
*   Quiñones Huaynalaya, E. (2020). Transporte urbano informal en ciudades intermedias del Perú. *Revista de Urbanismo y Planificación*.
*   Williams, S., et al. (2015). The Digital Matatus Project. *Journal of Transport Geography*.
