# Análisis Inicial del Sistema Legacy
 
## Resumen
 
Este documento recoge el análisis inicial del equipo utilizado para diseño gráfico profesional en un taller de serigrafía y las consideraciones técnicas previas a la migración hacia una arquitectura más segura basada en virtualización.
 
El objetivo de esta fase es identificar riesgos, limitaciones, dependencias y oportunidades de mejora antes de realizar cualquier modificación sobre el sistema.
 
---
 
## Contexto
 
El equipo es utilizado diariamente para tareas de diseño gráfico y producción documental.
 
Las aplicaciones y periféricos actualmente en uso son esenciales para la actividad profesional del usuario y deben mantenerse operativos durante y después de la migración.

El proyecto no persigue únicamente mejorar la postura de seguridad del sistema. También busca prolongar la vida útil de una plataforma que continúa siendo funcional para las necesidades del usuario, evitando la sustitución prematura del hardware mediante una combinación de virtualización, software libre y modernización progresiva del entorno de trabajo.
 
Adicionalmente, esta estrategia permite reducir la dependencia de nuevas adquisiciones de software propietario y de modelos de suscripción recurrente, favoreciendo una transición gradual hacia herramientas abiertas que puedan garantizar la continuidad operativa del negocio sin incrementar los costes de licenciamiento.
 
### Software crítico
 
- Adobe Photoshop
- Adobe Illustrator
 
### Hardware crítico
 
- Tableta gráfica Wacom CTL-460
- Escáner Canon MF3010
- Impresora HP LaserJet 5000N
 
### Perfil de usuario
 
- Usuario no técnico
- Dependencia diaria del equipo para su actividad profesional
- Necesidad de minimizar interrupciones del servicio
- Necesidad de no ampliar los costes en renovacion de licencias o nuevas subscripciones debido a su volumen de negocio
 
> [!TODO]
> Añadir captura de Photoshop instalado y operativo.
 
> [!TODO]
> Añadir captura de Illustrator instalado y operativo.
 
> [!TODO]
> Añadir fotografía de la Wacom CTL-460.
 
> [!TODO]
> Añadir fotografía de la Canon MF3010.
 
> [!TODO]
> Añadir fotografía de la HP LaserJet 5000N.
 
---
 
## Inventario de Hardware
 
### Equipo principal
 
El equipo fue diseñado, adquirido y ensamblado en 2012 específicamente para cubrir las necesidades de un entorno profesional de diseño gráfico.
 
La plataforma fue desplegada inicialmente con Windows 7 y concebida con un objetivo de larga duración, priorizando componentes fiables, fácilmente mantenibles y con una vida útil estimada superior a la habitual para un equipo de escritorio de la época.
 
Catorce años después de su puesta en servicio, el sistema continúa siendo funcional para las necesidades actuales del usuario y sigue permitiendo desarrollar la actividad profesional diaria sin limitaciones significativas de rendimiento.
 
La principal limitación identificada no está relacionada con el hardware sino con el ciclo de vida del software utilizado. La plataforma no cumple los requisitos exigidos por Microsoft para una actualización oficial a Windows 11, mientras que Windows 10 ha alcanzado el final de su ciclo de soporte.
 
Esta situación convierte la obsolescencia del sistema operativo en el principal factor de riesgo, a pesar de que el hardware continúa siendo plenamente utilizable.
 
#### Configuración principal
 
- CPU: Intel Core i5-3330
- Placa base: Gigabyte GA-Z77-DS3H
- Memoria RAM: 16 GB DDR3-1333
- Tarjeta gráfica: NVIDIA GeForce GT 630 2 GB
- Fuente de alimentación: Zalman ZM700-GT
- Disipador: Zalman CNPS9900A LED
- Chasis: Zalman Z9
 
#### Evaluación
 
A pesar de su antigüedad, la plataforma continúa ofreciendo recursos suficientes para:
 
- Ubuntu 26.04 LTS como sistema anfitrión.
- Virtualización de Windows 10 mediante VirtualBox.
- Ejecución de aplicaciones de diseño gráfico.
- Uso simultáneo de herramientas de productividad y navegación.
 
El análisis preliminar indica que no existe una necesidad inmediata de sustitución del hardware y que la migración tecnológica puede realizarse aprovechando la infraestructura actual.
 
La estrategia propuesta busca extender la vida útil operativa de la plataforma al menos una década adicional mediante virtualización, actualización del sistema anfitrión y reducción progresiva de dependencias de software propietario y sin soporte.
 
Considerando el estado actual del hardware y las necesidades reales del usuario, no se identifican limitaciones técnicas que obliguen a una sustitución inmediata de la plataforma.
 
> [!TODO]
> Añadir fotografía general del equipo antes de comenzar la migración.
 
> [!TODO]
> Añadir fotografía del interior del equipo antes de realizar modificaciones.
 
> [!TODO]
> Añadir captura de CPU-Z o herramienta equivalente mostrando la configuración actual del sistema.
 
> [!TODO]
> Añadir captura o evidencia documental del pedido original de componentes realizado en 2012.
 
### Almacenamiento actual
 
- Disco 1: 1 TB (actual sistema Windows 10)
- Disco 2: 1 TB
 
> [!TODO]
> Añadir captura de Administración de discos mostrando la configuración actual de almacenamiento.
 
### Componentes previstos para la migración
 
Se reutilizarán componentes procedentes de otros equipos para extender la vida útil de la plataforma actual y mejorar su rendimiento durante la transición.
 
Componentes a incorporar:
 
- SSD recuperado para alojar la máquina virtual de Windows 10.
- Tarjeta de red Wi-Fi interna para proporcionar conectividad al sistema anfitrión Ubuntu.
 
> [!TODO]
> Añadir fotografía del SSD recuperado.
 
> [!TODO]
> Añadir fotografía de la tarjeta Wi-Fi antes de la instalación.
 
---
 
## Situación Actual
 
### Sistema Operativo
 
El equipo utiliza actualmente Windows 10 como sistema operativo principal.
 
> [!TODO]
> Añadir captura de winver mostrando la versión actual de Windows 10.
 
### Riesgos identificados
 
- Dependencia de un sistema operativo sin soporte.
- Exposición a vulnerabilidades sin posibilidad de recibir actualizaciones de seguridad futuras.
- Dependencia de aplicaciones legacy para el desarrollo de la actividad profesional.
- Dependencia de periféricos con compatibilidad limitada fuera del entorno Windows.
 
### Limitaciones
 
La sustitución completa del entorno Windows no es viable actualmente debido a la dependencia de Adobe Photoshop, Adobe Illustrator y del ecosistema de periféricos utilizado en el taller.
 
---
## Evaluación de Compatibilidad de Periféricos
 
La viabilidad del proyecto depende en gran medida de la compatibilidad de los dispositivos utilizados diariamente por el usuario.
 
Antes de iniciar la migración se ha realizado una evaluación preliminar de los periféricos críticos y de su integración prevista en la arquitectura objetivo.
 
### Wacom CTL-460
 
**Uso:**
 
- Diseño gráfico.
- Ilustración.
- Edición mediante tableta gráfica.
 
**Estrategia prevista:**
 
- Compatibilidad nativa en Ubuntu mediante los controladores incluidos en Linux.
- Uso directo desde aplicaciones como GIMP e Inkscape.
- Utilización dentro de Windows 10 mediante USB Passthrough desde VirtualBox cuando sea necesario.
 
**Objetivo:**
 
Mantener la funcionalidad de la tableta gráfica tanto en el entorno Linux como en el entorno Windows durante el periodo de transición.
 
**Nivel de riesgo estimado:** Bajo
 
> [!TODO]
> Añadir fotografía de la Wacom CTL-460.
 
### Canon MF3010
 
**Uso:**
 
- Escaneo de documentos.
- Digitalización de material gráfico.
 
**Estrategia prevista:**
 
- Evaluar la compatibilidad nativa con Ubuntu.
- Validar tanto las funciones de impresión como las de escaneo.
- En caso necesario, utilizar USB Passthrough hacia Windows 10 Virtualizado para garantizar la continuidad operativa.
 
**Objetivo:**
 
Utilizar la Canon MF3010 directamente desde Ubuntu siempre que sea posible, reduciendo la dependencia del entorno Windows.
 
USB Passthrough se mantendrá como mecanismo de compatibilidad y contingencia.
 
**Observaciones:**
 
La compatibilidad con Linux no está garantizada para todas las funciones del dispositivo, especialmente las relacionadas con el escáner, por lo que deberán realizarse pruebas específicas durante la fase de implementación.
 
**Nivel de riesgo estimado:** Medio
 
> [!TODO]
> Añadir fotografía de la Canon MF3010.
 
### HP LaserJet 5000N
 
**Uso:**
 
- Impresión de documentos.
- Impresión de trabajos gráficos.
 
**Estrategia prevista:**
 
- Integración directa con Ubuntu.
- Recepción de documentos mediante carpeta compartida desde la máquina virtual.
- Gestión de impresión desde el sistema anfitrión.
 
**Objetivo:**
 
Gestionar toda la impresión desde Ubuntu para reducir la dependencia de Windows y simplificar el flujo de trabajo diario.
 
**Nivel de riesgo estimado:** Bajo
 
> [!TODO]
> Añadir fotografía de la HP LaserJet 5000N.
 
### Resultado Esperado
 
```text
Ubuntu
├── HP LaserJet 5000N
├── Canon MF3010
├── Wacom CTL-460
├── GIMP
├── Inkscape
└── Navegación y tareas sensibles
 
Windows 10 VM
├── Photoshop
└── Illustrator
```
 
La Wacom deberá funcionar tanto en Ubuntu como en Windows 10 virtualizado, permitiendo utilizar la tableta gráfica con aplicaciones nativas de Linux (GIMP e Inkscape) y con las aplicaciones Adobe que permanezcan dentro de la máquina virtual durante el periodo de transición.
 
El objetivo es que la mayor cantidad posible de hardware funcione directamente desde Ubuntu, reservando la máquina virtual únicamente para las aplicaciones Adobe que todavía resulten necesarias durante la transición.
 
## Problema Detectado Durante la Planificación
 
Como parte de la estrategia de migración se prevé crear una imagen completa del sistema Windows 10 mediante Macrium Reflect para posteriormente restaurarla dentro de una máquina virtual.
 
Durante la revisión inicial se detectó una limitación importante:
 
```text
El tamaño actual de la instalación de Windows es superior a la capacidad disponible en el SSD recuperado.
```
 
Esta situación impide restaurar directamente la imagen completa dentro del SSD destinado a alojar la futura máquina virtual.
 
> [!TODO]
> Añadir captura de las propiedades de las unidades mostrando el espacio utilizado.
 
> [!TODO]
> Añadir evidencia del tamaño actual de la instalación de Windows.
 
---
 
## Acción Correctiva Planificada
 
Antes de generar la imagen definitiva del sistema será necesario reducir el espacio ocupado por Windows.
 
### Estrategia
 
1. Identificar archivos no críticos almacenados en la unidad principal.
2. Mover documentos históricos y datos de gran tamaño al disco de 1 TB destinado a almacenamiento.
3. Mantener únicamente sistema operativo, aplicaciones y datos de trabajo necesarios para la operativa diaria.
4. Verificar el nuevo tamaño de la instalación.
5. Crear la imagen definitiva del sistema mediante Macrium Reflect.
 
### Resultado Esperado
 
```text
Windows 10 reducido a un tamaño compatible con el SSD disponible.
```
 
Esto permitirá:
 
- Generar una imagen más pequeña.
- Reducir tiempos de copia y restauración.
- Mejorar el rendimiento de la futura máquina virtual.
- Simplificar las tareas de mantenimiento y respaldo.
 
> [!TODO]
> Recordar obtener capturas del disco "ALMACÉN" antes de la transferencia de datos durante la fase de implementación.
 
> [!TODO]
> Recordar obtener capturas del proceso de reorganización de archivos durante la fase de implementación.
 
> [!TODO]
> Recordar obtener una captura final mostrando el espacio liberado tras la reorganización de datos.
 
---
 
## Estrategia de Transición Tecnológica
 
Además de mejorar la seguridad del entorno, el proyecto persigue reducir progresivamente la dependencia de software y servicios propietarios que condicionan la continuidad operativa del usuario.
 
La estrategia adoptada no busca reemplazar el flujo de trabajo actual de forma inmediata, sino facilitar una transición gradual hacia alternativas modernas y sostenibles.
 
### Objetivos
 
- Mantener la productividad actual sin interrupciones.
- Reducir la dependencia de Windows 10.
- Reducir progresivamente la dependencia del ecosistema Adobe.
- Introducir herramientas compatibles con Linux.
- Facilitar el aprendizaje progresivo de nuevas aplicaciones.
- Evitar cambios bruscos para un usuario no técnico.
 
### GIMP como alternativa a Photoshop
 
Aunque Photoshop continuará disponible dentro de la máquina virtual de Windows 10, se instalará GIMP en Ubuntu para favorecer una migración gradual hacia una herramienta nativa del sistema anfitrión.
 
La coexistencia de ambas aplicaciones permitirá:
 
- Comparar flujos de trabajo.
- Reducir la dependencia de Photoshop.
- Identificar tareas que puedan realizarse completamente desde Linux.
- Mejorar la autonomía tecnológica del usuario.
 
### Inkscape como alternativa a Illustrator
 
Además de Adobe Illustrator, el usuario utiliza herramientas de diseño vectorial como parte de su flujo de trabajo habitual dentro del taller.
 
Con el objetivo de reducir la dependencia de software propietario y facilitar una futura migración completa hacia Linux, se evaluará el uso de Inkscape como alternativa libre para trabajos de ilustración y diseño vectorial.
 
La coexistencia inicial de Illustrator e Inkscape permitirá:
 
- Comparar flujos de trabajo.
- Reducir progresivamente la dependencia de Illustrator.
- Mantener compatibilidad con formatos vectoriales estándar.
- Favorecer la adopción de herramientas nativas en Ubuntu.
- Mejorar la autonomía tecnológica del usuario.
 
### Estrategia de adopción
 
La transición no será inmediata.
 
Durante una fase inicial convivirán:
 
```text
Photoshop → GIMP
Illustrator → Inkscape
```
 
Esto permitirá al usuario familiarizarse con las nuevas herramientas sin afectar a la productividad diaria del negocio.
 
> [!TODO]
> Recordar obtener capturas de Inkscape instalado y configurado durante la fase de implementación.
 
> [!TODO]
> Recordar documentar ejemplos prácticos de migración Illustrator → Inkscape durante la fase de validación.
 
### Asistencia mediante Inteligencia Artificial
 
Se creará una cuenta de Proton para el usuario con acceso a las herramientas disponibles dentro del ecosistema Proton.
 
Como apoyo al proceso de aprendizaje se utilizará Lumo como asistente para:
 
- Resolver dudas sobre Ubuntu.
- Aprender funciones equivalentes entre Photoshop y GIMP.
- Aprender funciones equivalentes entre Illustrator e Inkscape.
- Guiar tareas básicas de configuración y administración.
- Reducir la curva de aprendizaje durante la transición.
 
### Resultado Esperado
 
#### Corto plazo
 
- Photoshop continúa funcionando dentro de la máquina virtual.
- Illustrator continúa funcionando dentro de la máquina virtual.
- El flujo de trabajo actual permanece operativo.
- No existe impacto significativo sobre la productividad.
 
#### Medio plazo
 
- GIMP comienza a utilizarse para tareas de edición de imagen.
- Inkscape comienza a utilizarse para tareas de diseño vectorial.
- El usuario adquiere familiaridad con Ubuntu.
- Se reduce progresivamente la dependencia diaria de Windows.
 
#### Largo plazo
 
- El usuario puede desempeñar gran parte de su actividad profesional desde Linux utilizando GIMP e Inkscape como alternativas principales a Photoshop e Illustrator.
- La dependencia de Windows 10 se reduce al mínimo o desaparece.
- Se elimina la necesidad de mantener software sin soporte como requisito operativo.
 
> [!TODO]
> Recordar obtener capturas de GIMP instalado y configurado durante la fase de implementación.
 
> [!TODO]
> Recordar obtener capturas de Inkscape instalado y configurado durante la fase de implementación.
 
> [!TODO]
> Recordar obtener capturas de la cuenta Proton configurada para el usuario.
 
> [!TODO]
> Recordar documentar ejemplos prácticos de migración Photoshop → GIMP durante la fase de validación.
 
> [!TODO]
> Recordar documentar ejemplos prácticos de migración Illustrator → Inkscape durante la fase de validación.
 
---
 
## Alternativas Evaluadas
 
### Sustitución completa del hardware
 
**Resultado:** Descartada.
 
**Motivo:**
 
- Incremento de costes.
- El hardware actual continúa siendo funcional para las necesidades del usuario.
 
### Migración completa a Linux
 
**Resultado:** Descartada.
 
**Motivo:**
 
- Dependencia directa de Photoshop e Illustrator.
- Posibles problemas de compatibilidad con periféricos específicos.
 
### Dual Boot
 
**Resultado:** Descartada.
 
**Motivo:**
 
- Windows seguiría ejecutándose directamente sobre hardware físico.
- No elimina los riesgos asociados a un sistema operativo legacy.
 
### Virtualización con aislamiento
 
**Resultado:** Seleccionada.
 
**Motivo:**
 
- Mantiene la funcionalidad requerida.
- Permite aislar completamente Windows 10.
- Reduce significativamente la superficie de ataque.
- Facilita copias de seguridad y recuperación mediante instantáneas.
 
---
 
## Arquitectura Objetivo
 
La solución prevista consiste en separar las funciones críticas del sistema mediante virtualización y segmentación del almacenamiento.
 
### Distribución de discos
 
```text
Disco 1 TB (actual sistema)
└── Ubuntu 26.04 LTS (Host)
 
SSD recuperado
└── Windows 10 Virtualizado (VirtualBox)
 
Disco 1 TB (ALMACÉN)
├── Datos históricos
├── Copias de seguridad
├── Archivos de trabajo
└── Carpeta compartida Host ↔ VM
```
 
> [!TODO]
> Añadir captura de la distribución final de discos o diagrama de almacenamiento.
 
### Ubuntu 26.04 LTS (host)
 
Instalado sobre el disco principal actualmente utilizado por Windows.
 
**Responsabilidades:**
 
- Navegación web.
- Correo electrónico.
- Banca electrónica.
- Trámites administrativos.
- Multimedia.
- Impresión.
- Aprendizaje progresivo con GIMP.
- Aprendizaje progresivo con Inkscape.
- Uso de herramientas de asistencia basadas en IA.
 
### Windows 10 Virtualizado
 
Instalado dentro de VirtualBox sobre el SSD recuperado.
 
**Responsabilidades:**
 
- Adobe Photoshop.
- Adobe Illustrator.
- Escaneo mediante Canon MF3010.
- Uso de la Wacom CTL-460.
- Trabajo gráfico profesional.
 
### Disco ALMACÉN
 
**Funciones:**
 
- Almacenamiento de archivos históricos.
- Copias de seguridad.
- Intercambio de información entre Ubuntu y la máquina virtual.
- Ubicación de la carpeta compartida utilizada por el usuario.
 
### Principio de seguridad
 
```text
Windows 10 permanecerá aislado de Internet.
```
 
Todo el acceso a red se realizará desde Ubuntu, reduciendo drásticamente la exposición del sistema legacy.
 
> [!TODO]
> Recordar crear e incluir el diagrama de arquitectura final.
 
> [!TODO]
> Recordar crear e incluir el diagrama del flujo Ubuntu → VirtualBox → Windows 10 VM.
 
---
 
## Próximos Pasos
 
1. Instalación del SSD recuperado.
2. Instalación de la tarjeta Wi-Fi interna.
3. Inventario de datos almacenados.
4. Limpieza y reorganización de archivos.
5. Creación de la imagen del sistema con Macrium Reflect.
6. Instalación de Ubuntu 26.04 LTS.
7. Instalación de GIMP e Inkscape y configuración inicial.
8. Creación de cuenta Proton para el usuario.
9. Implementación de VirtualBox.
10. Restauración de Windows 10 en entorno virtualizado.
11. Configuración del disco ALMACÉN como almacenamiento compartido.
12. Validación de periféricos y software crítico.
13. Aplicación de medidas de hardening sobre el sistema anfitrión.
 
> [!TODO]
> Recordar documentar todas las fases anteriores en implementation.md y validation.md.
 
---
 
## Conclusión
 
El análisis inicial confirma que el hardware actual continúa siendo válido para la actividad profesional del usuario. Sin embargo, la dependencia de Windows 10 y de aplicaciones legacy requiere una estrategia de aislamiento que permita mantener la operativa sin asumir los riesgos asociados al uso de un sistema operativo sin soporte.
 
La solución propuesta no se limita al aislamiento de un sistema legacy. También establece las bases para una transición tecnológica progresiva que permita reducir la dependencia de software sin soporte, fomentar el uso de herramientas abiertas como GIMP e Inkscape, y facilitar la adopción de nuevas tecnologías mediante asistencia guiada y aprendizaje continuo.
 
El objetivo final es prolongar la vida útil de la plataforma durante al menos una década adicional, preservando la continuidad operativa del negocio y maximizando el aprovechamiento de una infraestructura que, a pesar de su antigüedad, continúa siendo técnicamente válida para las necesidades actuales.

La adopción progresiva de soluciones basadas en software libre también contribuirá a reducir la dependencia de licencias propietarias y servicios de suscripción, mejorando la sostenibilidad económica del entorno de trabajo a largo plazo.