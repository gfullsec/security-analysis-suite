# Implementación de la Migración del Sistema Legacy
 
## Resumen
 
Este documento registra el proceso de implementación de la arquitectura definida durante la fase de análisis del sistema legacy.
 
El objetivo es documentar de forma cronológica y reproducible las acciones realizadas para migrar el entorno actual basado en Windows 10 hacia una arquitectura en la que Ubuntu 26.04 LTS funcione como sistema anfitrión y Windows 10 permanezca disponible dentro de una máquina virtual aislada para ejecutar el software legacy necesario.
 
Durante la implementación se documentarán:
 
- Modificaciones de hardware.
- Preparación y reorganización del sistema Windows 10 original.
- Creación y verificación de la imagen de respaldo.
- Instalación y configuración de Ubuntu.
- Configuración del almacenamiento.
- Instalación de VirtualBox.
- Migración de Windows 10 al entorno virtual.
- Configuración del aislamiento de red.
- Configuración de periféricos.
- Instalación de GIMP e Inkscape.
- Configuración de servicios auxiliares.
- Medidas de hardening aplicadas.
- Incidencias y desviaciones respecto al diseño inicial.
- Evidencias técnicas de cada fase.
 
> [!IMPORTANT]
> Ninguna modificación irreversible sobre el sistema original deberá realizarse sin disponer previamente de una copia de seguridad verificada.
 
---
 
# 1. Estado Inicial de la Implementación
 
Antes de iniciar las modificaciones de hardware o la instalación del nuevo sistema anfitrión se verificará el estado actual del sistema y se recopilarán las evidencias necesarias para disponer de una referencia previa a la migración.
 
## 1.1 Estado del hardware
 
Configuración de partida:
 
- CPU: Intel Core i5-3330
- Placa base: Gigabyte GA-Z77-DS3H
- RAM: 16 GB DDR3-1333
- GPU: NVIDIA GeForce GT 630 2 GB
- Disco principal: 1 TB
- Disco secundario: 1 TB, identificado como `ALMACÉN`
 
### Evidencias
 
> [!TODO]
> Añadir fotografía general del equipo antes de modificar el hardware.
 
> [!TODO]
> Añadir fotografía del interior del equipo antes de instalar el SSD y la tarjeta Wi-Fi.
 
> [!TODO]
> Añadir captura de CPU-Z, HWiNFO o herramienta equivalente mostrando CPU, placa base y memoria.
 
> [!TODO]
> Añadir captura de Administración de discos mostrando todos los dispositivos de almacenamiento antes de comenzar la migración.
 
---
 
# 2. Preparación del Sistema Windows 10
 
## 2.1 Objetivo
 
Antes de crear la imagen definitiva del sistema Windows 10 es necesario reducir el espacio ocupado por la instalación para permitir su posterior migración al SSD recuperado destinado a almacenar la máquina virtual.
 
Durante la fase de análisis se había previsto trasladar archivos históricos y otros datos al disco `ALMACÉN` si fuera necesario.
 
Finalmente, esta operación no fue necesaria.
 
## 2.2 Limpieza del sistema
 
La reducción de espacio se realizó eliminando datos innecesarios generados por el propio sistema operativo.
 
Se eliminaron:
 
- Instalaciones anteriores de Windows.
- Archivos de actualización de Windows.
- Archivos temporales.
- Otros archivos del sistema identificados como prescindibles durante el proceso de limpieza.
 
No fue necesario trasladar archivos del usuario ni datos históricos al disco `ALMACÉN`.
 
## 2.3 Resultado
 
Después de realizar la limpieza, el espacio ocupado por la instalación de Windows 10 quedó reducido aproximadamente a:
 
```text
90 GB
``


## 2.4 Desviación respecto al plan inicial

El análisis inicial contemplaba:

```text
Windows
    ↓
Identificación de archivos de gran tamaño
    ↓
Traslado de datos a ALMACÉN
    ↓
Reducción del espacio ocupado
```

Durante la implementación se comprobó que el traslado de datos no resultaba necesario.

El procedimiento finalmente aplicado fue:

```text
Windows
    ↓
Limpieza de instalaciones anteriores
    ↓
Eliminación de archivos de actualización
    ↓
Eliminación de archivos temporales
    ↓
~90 GB utilizados
```

Esta modificación simplifica la migración al evitar cambios innecesarios en la ubicación de los archivos de trabajo del usuario.

### Evidencias

> [!TODO]
> Añadir captura del espacio utilizado por Windows antes de la limpieza, si se dispone de ella.

> [!TODO]
> Añadir captura de la herramienta utilizada para realizar la limpieza, si se dispone de ella.

> [!TODO]
> Añadir captura de Administración de discos después de la limpieza.

> [!TODO]
> Añadir captura de las propiedades de C: mostrando aproximadamente 90 GB utilizados.

> [!TODO]
> Añadir captura del contenido o propiedades del disco ALMACÉN para documentar que no fue necesario utilizarlo durante esta fase.

---

## 3. Instalación de Componentes de Hardware

### 3.1 SSD recuperado

#### Objetivo
Instalar físicamente el SSD que posteriormente almacenará los archivos correspondientes a la máquina virtual de Windows 10.

#### Procedimiento
> [!TODO]
> Documentar modelo, fabricante y capacidad exacta del SSD.

> [!TODO]
> Documentar instalación física.

> [!TODO]
> Verificar detección del SSD en BIOS/UEFI.

> [!TODO]
> Verificar detección desde el sistema operativo.

#### Evidencias necesarias
> [!TODO]
> Fotografía del SSD antes de instalarlo.

> [!TODO]
> Fotografía del SSD instalado en el equipo.

> [!TODO]
> Captura de BIOS/UEFI mostrando el SSD detectado.

> [!TODO]
> Captura de Administración de discos mostrando el nuevo SSD.

#### Resultado
**Estado:** Pendiente

---

### 3.2 Instalación de la tarjeta Wi-Fi

#### Objetivo
Incorporar la tarjeta Wi-Fi que proporcionará conectividad de red al futuro sistema anfitrión Ubuntu.

#### Procedimiento
> [!TODO]
> Identificar fabricante y modelo exacto de la tarjeta.

> [!TODO]
> Instalar físicamente la tarjeta Wi-Fi.

> [!TODO]
> Verificar su detección por el hardware.

> [!TODO]
> Comprobar posteriormente su compatibilidad con Ubuntu.

#### Evidencias necesarias
> [!TODO]
> Fotografía de la tarjeta Wi-Fi antes de la instalación.

> [!TODO]
> Fotografía de la tarjeta instalada.

> [!TODO]
> Captura o evidencia de detección del dispositivo.

#### Resultado
**Estado:** Pendiente

---

## 4. Creación de la Imagen de Windows 10

### 4.1 Objetivo
Crear una imagen completa y recuperable del entorno Windows 10 antes de sustituir el sistema operativo instalado físicamente.

La imagen tendrá dos funciones:
1. Copia de seguridad del sistema original.
2. Fuente para la posterior migración de Windows 10 al entorno virtual.

### 4.2 Comprobaciones previas
Antes de crear la imagen:
- Verificar integridad general del sistema.
- Comprobar espacio utilizado.
- Comprobar estructura de particiones.
- Verificar el destino de la copia.
- Confirmar que Photoshop e Illustrator funcionan correctamente.
- Comprobar los periféricos críticos.

#### Evidencias necesarias
> [!TODO]
> Captura de `winver`.

> [!TODO]
> Captura de Administración de discos mostrando las particiones del sistema.

> [!TODO]
> Captura de las propiedades de C: mostrando el espacio utilizado.

> [!TODO]
> Captura de Photoshop ejecutándose correctamente antes de la migración.

> [!TODO]
> Captura de Illustrator ejecutándose correctamente antes de la migración.

> [!TODO]
> Captura de Macrium Reflect mostrando los discos y particiones detectados.

### 4.3 Creación de la imagen
> [!TODO]
> Documentar versión de Macrium Reflect utilizada.

> [!TODO]
> Documentar las particiones incluidas en la imagen.

> [!TODO]
> Documentar ubicación utilizada para almacenar la imagen.

> [!TODO]
> Documentar tamaño final de la imagen.

#### Evidencias necesarias
> [!TODO]
> Captura de la configuración del backup antes de iniciarlo.

> [!TODO]
> Captura del proceso de creación de la imagen.

> [!TODO]
> Captura indicando que la creación de la imagen ha finalizado correctamente.

### 4.4 Verificación de la imagen
La existencia del archivo de imagen por sí sola no será considerada suficiente. La copia deberá verificarse antes de realizar modificaciones destructivas sobre la instalación física de Windows.

> [!TODO]
> Ejecutar la función de verificación disponible en Macrium Reflect.

> [!TODO]
> Registrar el resultado de la verificación.

#### Evidencias necesarias
> [!TODO]
> Captura de la verificación satisfactoria de la imagen.

> [!TODO]
> Captura mostrando el archivo de imagen generado y su tamaño.

#### Resultado
**Estado:** Pendiente

---

## 5. Instalación de Ubuntu 26.04 LTS

### 5.1 Preparación del medio de instalación
> [!TODO]
> Documentar versión exacta de la imagen ISO utilizada.

> [!TODO]
> Documentar origen de la ISO.

> [!TODO]
> Verificar la integridad de la ISO mediante checksum.

> [!TODO]
> Documentar herramienta utilizada para crear el USB de instalación.

#### Evidencias necesarias
> [!TODO]
> Captura de la descarga de Ubuntu.

> [!TODO]
> Captura de la verificación del checksum.

> [!TODO]
> Captura de la creación del USB de instalación.

### 5.2 Instalación
**Destino:**

```text
Disco principal 1 TB
└── Ubuntu 26.04 LTS
```

> [!TODO]
> Documentar las opciones seleccionadas durante la instalación.

> [!TODO]
> Documentar distribución definitiva de particiones.

> [!TODO]
> Documentar usuario creado.

> [!TODO]
> Documentar configuración relevante de seguridad.

#### Evidencias necesarias
> [!TODO]
> Captura del instalador de Ubuntu.

> [!TODO]
> Captura de la selección de disco/particionado.

> [!TODO]
> Captura de la instalación finalizada correctamente.

> [!TODO]
> Captura del primer arranque de Ubuntu.

---

## 6. Configuración Inicial de Ubuntu

### 6.1 Actualización del sistema

```bash
# Los comandos ejecutados durante la implementación
# se registrarán aquí.
```

> [!TODO]
> Documentar actualización inicial de paquetes.

> [!TODO]
> Documentar versión del kernel.

> [!TODO]
> Documentar dispositivos de almacenamiento detectados.

> [!TODO]
> Documentar interfaces de red detectadas.

#### Evidencias necesarias
> [!TODO]
> Captura de Información del sistema.

> [!TODO]
> Captura de las unidades detectadas.

> [!TODO]
> Captura de la conexión Wi-Fi funcionando.

---

## 7. Configuración del Disco ALMACÉN

### Objetivo
Utilizar el segundo disco de 1 TB para:

```text
ALMACÉN
├── Datos históricos
├── Copias de seguridad
├── Archivos de trabajo
└── Intercambio Host ↔ VM
```

> [!TODO]
> Documentar sistema de archivos actual.

> [!TODO]
> Documentar configuración de montaje.

> [!TODO]
> Documentar permisos.

> [!TODO]
> Crear estructura definitiva de directorios.

### Evidencias necesarias
> [!TODO]
> Captura de Ubuntu mostrando el disco.

> [!TODO]
> Captura de la estructura de directorios.

> [!TODO]
> Captura o salida de terminal mostrando punto de montaje y sistema de archivos.

---

## 8. Instalación de GIMP e Inkscape

### 8.1 GIMP
> [!TODO]
> Instalar GIMP.

> [!TODO]
> Configurar la Wacom CTL-460.

> [!TODO]
> Realizar una prueba básica de edición.

#### Evidencias
> [!TODO]
> Captura de GIMP instalado y ejecutándose.

> [!TODO]
> Captura de prueba utilizando la Wacom.

### 8.2 Inkscape
> [!TODO]
> Instalar Inkscape.

> [!TODO]
> Realizar una prueba básica de diseño vectorial.

#### Evidencias
> [!TODO]
> Captura de Inkscape instalado y ejecutándose.

> [!TODO]
> Captura de un documento vectorial de prueba.

---

## 9. Configuración de Proton y Lumo

> [!TODO]
> Crear la cuenta Proton destinada al usuario.

> [!TODO]
> Configurar los servicios necesarios.

> [!TODO]
> Verificar acceso a Lumo.

### Evidencias
> [!TODO]
> Captura de Proton configurado.

> [!TODO]
> Captura de acceso a Lumo.

> [!WARNING]
> Las capturas deberán ocultar direcciones de correo completas, credenciales, códigos de recuperación, tokens y cualquier otra información sensible.

---

## 10. Instalación y Configuración de VirtualBox

### 10.1 Instalación
> [!TODO]
> Documentar versión instalada.

> [!TODO]
> Documentar método de instalación.

> [!TODO]
> Verificar soporte de virtualización por hardware.

#### Evidencias
> [!TODO]
> Captura de VirtualBox instalado.

> [!TODO]
> Captura mostrando la versión instalada.

---

## 11. Migración de Windows 10 a la Máquina Virtual

### 11.1 Creación de la VM
> [!TODO]
> Documentar CPU virtual asignada.

> [!TODO]
> Documentar RAM asignada.

> [!TODO]
> Documentar configuración gráfica.

> [!TODO]
> Documentar almacenamiento virtual.

> [!TODO]
> Documentar ubicación de la VM en el SSD.

#### Evidencias
> [!TODO]
> Captura de la configuración general de la VM.

> [!TODO]
> Captura de CPU y RAM asignadas.

> [!TODO]
> Captura de almacenamiento virtual.

### 11.2 Restauración de Windows
> [!TODO]
> Documentar procedimiento utilizado para restaurar la imagen.

> [!TODO]
> Documentar cualquier ajuste realizado sobre las particiones.

> [!TODO]
> Documentar primer arranque correcto de Windows virtualizado.

#### Evidencias
> [!TODO]
> Captura de Macrium Reflect detectando la imagen.

> [!TODO]
> Captura del disco virtual de destino.

> [!TODO]
> Captura del proceso de restauración.

> [!TODO]
> Captura de Windows 10 arrancando dentro de VirtualBox.

> [!TODO]
> Captura de `winver` desde la máquina virtual.

---

## 12. Configuración de VirtualBox Guest Additions

Las Guest Additions de VirtualBox proporcionan, entre otras cosas, integración del puntero, carpetas compartidas y mejoras del soporte gráfico.

> [!TODO]
> Instalar Guest Additions.

> [!TODO]
> Verificar resolución gráfica.

> [!TODO]
> Verificar integración de ratón.

> [!TODO]
> Verificar carpeta compartida.

### Evidencias
> [!TODO]
> Captura de Guest Additions instalado.

> [!TODO]
> Captura del escritorio Windows correctamente dimensionado.

---

## 13. Aislamiento de Red de Windows 10

### Objetivo de seguridad
La máquina virtual Windows 10 no deberá utilizarse para acceder directamente a Internet.

Ubuntu será el entorno autorizado para:
- Navegación.
- Correo electrónico.
- Banca.
- Descargas.
- Servicios web.
- Trámites administrativos.

### Configuración
> [!TODO]
> Documentar configuración definitiva del adaptador de red virtual.

> [!TODO]
> Verificar que Windows no dispone de acceso directo a Internet.

> [!TODO]
> Verificar que la ausencia de Internet no afecta al funcionamiento de Photoshop e Illustrator.

#### Evidencias
> [!TODO]
> Captura de la configuración de red de VirtualBox.

> [!TODO]
> Captura de `ipconfig /all` dentro de Windows.

> [!TODO]
> Captura de prueba demostrando la ausencia de conectividad externa.

> [!TODO]
> Captura mostrando simultáneamente que Ubuntu mantiene conectividad.

### Resultado
**Estado:** Pendiente

---

## 14. Configuración de la Carpeta Compartida

### Objetivo
Permitir un intercambio controlado de archivos entre Ubuntu y Windows sin convertir Windows 10 en el entorno principal de acceso a red.

```text
Internet
   │
   ▼
Ubuntu
   │
   ├─── ALMACÉN
   │       │
   │       └── Carpeta compartida
   │                │
   │                ▼
   │          Windows 10 VM
   │
   └─── Periféricos
```

> [!TODO]
> Crear la carpeta destinada al intercambio.

> [!TODO]
> Configurar permisos.

> [!TODO]
> Configurar la carpeta en VirtualBox.

> [!TODO]
> Verificar lectura y escritura.

### Evidencias
> [!TODO]
> Captura de permisos desde Ubuntu.

> [!TODO]
> Captura de configuración de Shared Folders en VirtualBox.

> [!TODO]
> Captura de la carpeta accesible desde Windows.

> [!TODO]
> Captura de una prueba de transferencia Ubuntu → Windows.

> [!TODO]
> Captura de una prueba de transferencia Windows → Ubuntu.

---

## 15. Configuración de Periféricos

### 15.1 Wacom CTL-460
#### Ubuntu
> [!TODO]
> Verificar detección.

> [!TODO]
> Probar funcionamiento con GIMP.

> [!TODO]
> Probar funcionamiento con Inkscape.

#### Windows 10 VM
> [!TODO]
> Configurar USB Passthrough.

> [!TODO]
> Probar funcionamiento con Photoshop.

> [!TODO]
> Probar funcionamiento con Illustrator.

#### Evidencias
> [!TODO]
> Captura de detección en Ubuntu.

> [!TODO]
> Captura de Wacom funcionando con GIMP.

> [!TODO]
> Captura de configuración USB en VirtualBox.

> [!TODO]
> Captura de Wacom funcionando dentro de Photoshop.

### 15.2 Canon MF3010
#### Ubuntu
> [!TODO]
> Comprobar impresión.

> [!TODO]
> Comprobar escaneo.

#### Windows 10 VM
Si alguna función no puede realizarse correctamente desde Ubuntu:
> [!TODO]
> Configurar USB Passthrough.

> [!TODO]
> Comprobar funcionalidad desde Windows.

#### Evidencias
> [!TODO]
> Captura del dispositivo detectado en Ubuntu.

> [!TODO]
> Evidencia de prueba de impresión.

> [!TODO]
> Evidencia de prueba de escaneo.

> [!TODO]
> Captura de USB Passthrough si finalmente resulta necesario.

### 15.3 HP LaserJet 5000N
> [!TODO]
> Configurar la impresora en Ubuntu.

> [!TODO]
> Imprimir página de prueba.

> [!TODO]
> Probar impresión de un documento procedente de la VM mediante el flujo de intercambio diseñado.

#### Evidencias
> [!TODO]
> Captura de la impresora configurada en Ubuntu.

> [!TODO]
> Fotografía de la página de prueba.

> [!TODO]
> Evidencia de impresión satisfactoria de un documento generado desde Windows.

---

## 16. Validación del Software Legacy

### Photoshop
> [!TODO]
> Iniciar Photoshop.

> [!TODO]
> Abrir un proyecto existente.

> [!TODO]
> Editar el documento.

> [!TODO]
> Guardar el resultado.

> [!TODO]
> Probar Wacom.

#### Evidencias
> [!TODO]
> Captura de Photoshop ejecutándose dentro de Windows virtualizado.

> [!TODO]
> Captura de un proyecto abierto correctamente.

### Illustrator
> [!TODO]
> Iniciar Illustrator.

> [!TODO]
> Abrir un proyecto existente.

> [!TODO]
> Editar el documento.

> [!TODO]
> Guardar el resultado.

> [!TODO]
> Probar Wacom.

#### Evidencias
> [!TODO]
> Captura de Illustrator ejecutándose dentro de Windows virtualizado.

> [!TODO]
> Captura de un proyecto abierto correctamente.

---

## 17. Hardening de Ubuntu

Esta fase se realizará una vez comprobado que la arquitectura básica funciona correctamente.

### Áreas de trabajo
- Actualizaciones de seguridad.
- Configuración de usuarios.
- Privilegios administrativos.
- Firewall.
- Servicios habilitados.
- Permisos del almacenamiento.
- Configuración de red.
- Protección de las copias de seguridad.
- Revisión del software instalado.
- Configuración del acceso físico y bloqueo de sesión.

> [!TODO]
> Documentar individualmente cada control aplicado y su justificación.

### Evidencias
> [!TODO]
> Capturas del estado de actualizaciones.

> [!TODO]
> Evidencia de configuración del firewall.

> [!TODO]
> Evidencia de servicios activos.

> [!TODO]
> Evidencia de usuarios y grupos relevantes.

> [!TODO]
> Evidencia de permisos sobre ALMACÉN y carpeta compartida.

---

## 18. Copias de Seguridad y Recuperación

> [!TODO]
> Definir estrategia definitiva de backup.

> [!TODO]
> Crear copia de seguridad inicial de la VM funcional.

> [!TODO]
> Crear snapshot del estado estable de Windows.

> [!TODO]
> Realizar una prueba de recuperación.

### Evidencias
> [!TODO]
> Captura de snapshot inicial.

> [!TODO]
> Captura de ubicación de la copia de seguridad.

> [!TODO]
> Captura del proceso de restauración de prueba.

> [!TODO]
> Evidencia del arranque satisfactorio después de la prueba.

---

## 19. Arquitectura Implementada

Al finalizar la migración se documentará la arquitectura realmente implementada.

```text
                    INTERNET
                       │
                       ▼
              Ubuntu 26.04 LTS
                 HOST SEGURO
                       │
       ┌───────────────┼────────────────┐
       │               │                │
       ▼               ▼                ▼
    ALMACÉN       Periféricos       Aplicaciones
       │                              Linux
       │
       ▼
Carpeta compartida
       │
       ▼
 Windows 10 VM
   AISLADA
       │
       ├── Photoshop
       └── Illustrator
```

> [!TODO]
> Sustituir este esquema preliminar por el diagrama definitivo de arquitectura.

> [!TODO]
> Añadir diagrama del flujo de datos entre Ubuntu, ALMACÉN y Windows.

---

## 20. Incidencias y Desviaciones

### DEV-001 - Reducción de la instalación de Windows

- **Plan original:** Trasladar archivos de gran tamaño y datos históricos al disco ALMACÉN para reducir el tamaño de Windows.
- **Implementación real:** No fue necesario trasladar datos del usuario. La eliminación de instalaciones anteriores de Windows, archivos de actualización y archivos temporales permitió reducir la ocupación aproximadamente a 90 GB.
- **Impacto:** Positivo. Se simplificó el procedimiento y se evitó modificar innecesariamente la ubicación de los datos del usuario.
- **Estado:** Resuelto.

---

## 21. Estado de la Implementación

- [x] Análisis inicial.
- [x] Limpieza y reducción del sistema Windows 10.
- [ ] Instalación del SSD.
- [ ] Instalación de tarjeta Wi-Fi.
- [ ] Verificación del almacenamiento.
- [ ] Creación de imagen con Macrium Reflect.
- [ ] Verificación de la imagen.
- [ ] Instalación de Ubuntu 26.04 LTS.
- [ ] Configuración inicial del host.
- [ ] Configuración de ALMACÉN.
- [ ] Instalación de GIMP.
- [ ] Instalación de Inkscape.
- [ ] Configuración de Proton/Lumo.
- [ ] Instalación de VirtualBox.
- [ ] Restauración de Windows 10.
- [ ] Aislamiento de red de Windows.
- [ ] Configuración de carpeta compartida.
- [ ] Validación de Wacom CTL-460.
- [ ] Validación de Canon MF3010.
- [ ] Validación de HP LaserJet 5000N.
- [ ] Validación de Photoshop.
- [ ] Validación de Illustrator.
- [ ] Hardening de Ubuntu.
- [ ] Configuración de backup.
- [ ] Prueba de recuperación.
- [ ] Documentación de arquitectura final.

---

