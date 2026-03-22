# Informe Técnico del Taller

## Nombre del Taller
_Taller 4 - Mapa de Infraestructura y Diagnóstico Técnico_

## Integrantes del equipo
| Nombre | Correo Electrónico |
|---|---|
| Valentina Alejandra López Romero | valentinalopro@unisabana.edu.co |
| Mariana Valle Moreno | marianavamo@unisabana.edu.co |
| Laura Camila Rodriguez Leon | laurarodleo@unisabana.edu.co |

## Descripción general del trabajo
El objetivo del taller fue construir el mapa lógico y físico de la infraestructura tecnológica del sistema base, con el fin de identificar debilidades, cuellos de botella y oportunidades de mejora en el proceso de aplicación de encuestas de autoevaluación institucional.

La actividad se basó en analizar el proceso del cliente, identificando actores, herramientas y flujo de información. Con esto, se elaboró un diagrama de infraestructura que muestra la interacción con el sistema, el procesamiento de solicitudes y el almacenamiento de datos. Finalmente, se realizó un diagnóstico técnico para detectar riesgos y oportunidades de mejora.

## Proceso de desarrollo
Se inició analizando el proceso actual del cliente, enfocandonos así en cómo se gestionan los cronogramas, la aplicación de encuestas y la consolidación de resultados. A partir de esto, se tomaron las siguientes decisiones:

- Representar la arquitectura en capas: acceso, aplicación, datos y servicios.
- Diferenciar claramente entre usuarios (actores) y componentes tecnológicos.
- Modelar los módulos funcionales (cronogramas, aplicación y resultados) como servicios ejecutados sobre infraestructura.
- Incluir elementos de seguridad como firewall y acceso mediante red institucional.

Se utilizó draw.io como herramienta principal para el diseño del diagrama, apoyandonos en iconografía tipo AWS para representar los componentes de infraestructura.

## Análisis del modelo propuesto

El modelo se divide en cuatro capas principales:
- Acceso: donde interactúan los usuarios (decano, docente, PAT y encuestados) a través de la red universitaria y un firewall.
- Aplicación: donde se encuentran los servicios principales del sistema, incluyendo la API de encuestas y los módulos de gestión.
- Datos: donde se almacenan la información estructurada (base de datos) y los resultados de las encuestas.
- Servicios: que soportan el sistema mediante notificaciones y monitoreo.

Con esta estructura es posible lograr separar las responsabilidad y facilitar la comprensión del flujo de información. En cuanto a las necesidades del cliente, se considera que representa el proceso de construcción del cronograma, modela la aplicación de las encuestas mediante los estudiantes PAT y permit visualizar cómo se puede centralizar la información en una base de datos. Además, el modelo evidencia la interacción entre múltiples actores y la dependencia de herramientas tecnológicas para coordinar el proceso.

Para la construcción del modelo se asumió que:

- La información se almacena en una base de datos central.
- El sistema utiliza servicios institucionales para notificaciones (correo).
- Se cuenta con algún nivel de monitoreo y generación de reportes, aunque no esté completamente automatizado.

## Diagrama final entregado

![Mapa final](https://github.com/user-attachments/assets/27c7b426-36c6-4f12-9c4a-4db1fdf78ccc)


## 📋 Tabla de actores, entidades o componentes (si aplica)

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Decano | Actor | Define y diligencia el cronograma de encuestas (Plan A y Plan B) | Facultad |
| Docente | Actor | Permite el acceso a sus clases para la aplicación de encuestas | Programa |
| PAT (Estudiante aplicador) | Actor | Aplica las encuestas en aula según el cronograma | Coordinación logística |
| Encuestado | Actor | Estudiante que responde la encuesta | Institucional |
| Servidor Web | Componente | Permite el acceso al sistema de encuestas | Área de TI |
| API Encuesta | Componente | Gestiona las solicitudes del sistema y la comunicación entre módulos | Área de TI |
| Gestión de Cronogramas | Componente | Administra la planificación de las encuestas | Coordinación logística |
| Gestión de Aplicación de Encuestas | Componente | Controla la ejecución de encuestas en aula | Coordinación logística |
| Gestión de Resultados | Componente | Procesa y consolida los resultados obtenidos | Coordinación logística |
| Base de Datos Central | Componente | Almacena la información estructurada del sistema | Área de TI |
| Repositorio de Resultados | Componente | Guarda los resultados de las encuestas aplicadas | Área de TI |
| Notificaciones / Correo institucional | Servicio | Envía comunicaciones a los actores del proceso | Área de TI |
| Monitoreo y Reportes | Servicio | Permite el seguimiento y análisis del proceso | Área de TI |



## Investigación complementaria
### Tema investigado: Buenas prácticas de arquitectura en nube, híbrida y on-premise

Las arquitecturas de TI han evolucionado hacia modelos más flexibles que combinan entornos en la nube, híbridos y on-premise, con el fin de responder a necesidades empresariales como escalabilidad, rendimiento, seguridad y optimización de costos. En este contexto, las buenas prácticas de arquitectura buscan garantizar soluciones alineadas al negocio, eficientes y sostenibles en el tiempo.

Una arquitectura en la nube permite escalar recursos bajo demanda y reducir inversiones iniciales, mientras que los entornos on-premise ofrecen mayor control sobre datos críticos y cumplimiento normativo. La arquitectura híbrida integra ambos modelos, permitiendo a las organizaciones modernizar sus sistemas de manera progresiva y aprovechar lo mejor de cada entorno.

Entre las principales buenas prácticas identificadas se encuentran:

- **Alinear la arquitectura con los objetivos del negocio:**
El diseño arquitectónico debe responder a las necesidades estratégicas de la organización, considerando factores como costos, seguridad, cumplimiento y crecimiento. Esto implica definir qué cargas de trabajo deben mantenerse on-premise y cuáles migrar a la nube según su valor y criticidad [1][2].

- **Evaluar y clasificar las cargas de trabajo:**
Es fundamental analizar las aplicaciones y datos para determinar su ubicación óptima. Los sistemas críticos o regulados suelen permanecer en infraestructura local, mientras que cargas de trabajo variables o intensivas en recursos pueden beneficiarse de la nube [2].

- **Adoptar arquitecturas flexibles y evitar dependencia de proveedores:**
Se recomienda diseñar soluciones que permitan portabilidad y adaptación futura, evitando el vendor lock-in. Estrategias como multicloud o el uso de contenedores facilitan la interoperabilidad entre entornos [1].

- **Garantizar seguridad integrada:**
La protección de datos debe aplicarse de manera consistente en todos los entornos, incluyendo cifrado en tránsito y en reposo, autenticación robusta y monitoreo continuo. En arquitecturas híbridas, esto es especialmente relevante debido a la interacción entre sistemas [2].

- **Implementar monitoreo y observabilidad:**
El uso de herramientas de monitoreo permite identificar problemas de rendimiento, latencia y disponibilidad. Esto es clave en entornos híbridos, donde la comunicación entre nube y on-premise puede impactar la experiencia del usuario [2].

- **Optimizar costos y recursos:**
Aunque la nube reduce inversiones iniciales, es necesario controlar el consumo para evitar costos innecesarios. Una correcta planificación permite equilibrar el uso de recursos entre nube y on-premise [1][2].

- **Diseñar para escalabilidad y modernización gradual:**
Las arquitecturas deben permitir crecer de forma progresiva, facilitando la migración de sistemas legacy hacia la nube sin afectar la operación actual [1][2].

- **Gestionar la latencia y el rendimiento:¨¨
En entornos híbridos, es importante optimizar la comunicación entre sistemas para evitar retrasos que afecten aplicaciones críticas o en tiempo real [2].

La aplicación de estas buenas prácticas es clave para diseñar arquitecturas eficientes en entornos empresariales. En el contexto del proyecto de Logística de Aplicación de la encuesta institucional, estas prácticas permiten identificar oportunidades de mejora en la gestión de información, integración de sistemas y optimización de procesos, especialmente en escenarios donde se combinan herramientas locales (como Excel o Microsoft Suite) con posibles soluciones en la nube .La correcta adopción de estos principios demuestra que la arquitectura no solo es una decisión tecnológica, sino un habilitador estratégico que permite mejorar la eficiencia operativa, reducir reprocesos y facilitar la toma de decisiones basada en datos.

### Resumen:
Las buenas prácticas en arquitecturas de nube, híbridas y on-premise establecen que las soluciones deben estar alineadas con los objetivos del negocio, evaluar adecuadamente las cargas de trabajo y garantizar seguridad, monitoreo y optimización de costos [1][2]. Asimismo, se recomienda diseñar arquitecturas flexibles, evitar dependencia de proveedores y permitir una modernización progresiva de los sistemas [1].

En el contexto del proyecto de Logística de Aplicación, estas prácticas permiten estructurar mejor la gestión de la información, reducir la carga operativa manual y sentar bases para una posible evolución hacia soluciones más automatizadas y escalables. La correcta aplicación de estos principios contribuye a mejorar la eficiencia del proceso y fortalecer la capacidad institucional de adaptación tecnológica

## Referencias
- [1] Google Cloud, Hybrid and Multicloud Patterns, 2024. [En línea]. Disponible en: https://docs.cloud.google.com/architecture/hybrid-multicloud-patterns?hl=es
- [2] O. Hernández, “Implementación de Arquitecturas Híbridas: Nube y On-Premises”, 2024. [En línea]. Disponible en: https://www.linkedin.com/pulse/implementaci%C3%B3n-de-arquitecturas-h%C3%ADbridas-nube-y-hernandez-sarmiento-y5j5c/

---

_Este documento hace parte de la entrega del taller 4 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
