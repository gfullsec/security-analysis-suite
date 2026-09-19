# Evaluación de Vulnerabilidades – Linksys WRT54G

## 1. Resumen General

**Objetivo:** Linksys WRT54G (router SOHO legado)  
**Dirección IP:** `192.168.1.250`  
**Tipo de evaluación:** Revisión autenticada de la interfaz web + escaneo de vulnerabilidades en red  
**Herramientas:** OpenVAS (Greenbone Community Edition), Nmap (opcional), revisión manual  

Este análisis se centra en un dispositivo Linksys WRT54G aún presente en la red doméstica, evaluando su exposición, debilidades de configuración y vulnerabilidades conocidas.

---

## 2. Alcance y Objetivos

**Alcance:**

- Interfaz de administración web (`http://192.168.1.250/`)
- Servicios de red expuestos por el dispositivo
- Versión de firmware y CVEs asociados
- Estado de endurecimiento y configuración

**Objetivos:**

- Identificar servicios expuestos y superficie de ataque  
- Detectar vulnerabilidades conocidas (CVEs) mediante OpenVAS  
- Evaluar debilidades de configuración (credenciales por defecto, firmware obsoleto, protocolos inseguros)  
- Proponer medidas de mitigación y recomendaciones de retirada  

---

## 3. Metodología

**Paso 1 – Descubrimiento**

- Identificación de la IP mediante tabla DHCP / escaneo ARP  
- Confirmación del modelo y fabricante mediante la interfaz web y banners  

**Paso 2 – Enumeración de Puertos y Servicios**

- Escaneo TCP/UDP (opcional, almacenado en raw/nmap/)  
- Confirmación de servicios accesibles desde la LAN  

**Paso 3 – Escaneo con OpenVAS**

- Creación de un objetivo dedicado para 192.168.1.250  
- Uso de la configuración de escaneo Full and fast  
- Ejecución del escaneo y exportación de resultados (PDF/XML/JSON en reports/ y raw/openvas/)  

**Paso 4 – Revisión Manual**

- Acceso a la interfaz web del dispositivo  
- Revisión de:  
  - versión de firmware  
  - configuración de seguridad Wi‑Fi  
  - política de credenciales de administración  
  - opciones de gestión remota  
  - UPnP, WPS y otras funciones heredadas  

**Paso 5 – Análisis y Documentación**

- Correlación de hallazgos de OpenVAS con observaciones manuales  
- Clasificación de problemas por severidad e impacto  
- Documentación de mitigaciones y recomendaciones a largo plazo  

---

## 4. Hallazgos Principales

> Nota: Esta sección debe actualizarse con los resultados reales del informe de OpenVAS y la revisión manual.

**Ejemplo de estructura:**

- **Hallazgo 1 – Firmware obsoleto con vulnerabilidades conocidas**  
  - Severidad: Alta  
  - Descripción: El dispositivo ejecuta una versión de firmware sin soporte con múltiples CVEs públicas.  
  - Impacto: Riesgo elevado de compromiso remoto o local.  
  - Evidencia: Informe OpenVAS (ver reports/), avisos del fabricante.  
  - Recomendación: Actualizar firmware si es posible; de lo contrario, planificar la retirada.  

- **Hallazgo 2 – Credenciales administrativas débiles o por defecto**  
  - Severidad: Crítica  
  - Descripción: La interfaz de administración es accesible con credenciales débiles o por defecto.  
  - Impacto: Control total del router y posible pivot hacia otros sistemas de la red.  
  - Recomendación: Establecer una contraseña fuerte y única; desactivar gestión remota; restringir acceso.  

- **Hallazgo 3 – Protocolos de gestión inseguros**  
  - Severidad: Media  
  - Descripción: La interfaz de administración solo está disponible mediante HTTP.  
  - Impacto: Las credenciales pueden ser interceptadas.  
  - Recomendación: Activar HTTPS si es posible; de lo contrario, limitar acceso y considerar sustitución.  

---

## 5. Evaluación de Riesgo

- Nivel de riesgo global: Alto  
- Contexto: Dispositivo legado que sigue siendo un punto de pivote en la red doméstica.  
- Modelo de amenazas:  
  - Atacante local en la LAN  
  - Dispositivo IoT comprometido que pivota a través del router  
  - Exposición involuntaria por mala configuración  

---

## 6. Plan de Mitigación

**Corto plazo:**

- Cambiar credenciales administrativas  
- Desactivar gestión remota  
- Restringir acceso a hosts de confianza  

**Medio plazo:**

- Actualizar firmware  
- Revisar seguridad Wi‑Fi  
- Desactivar funciones heredadas  

**Largo plazo:**

- Planificar la retirada del WRT54G  
- Sustituir por un router/firewall moderno  
- Integrar el nuevo dispositivo en ciclos regulares de evaluación  

---

## 7. Estructura del Repositorio

openvas/wrt54g/  
├── reports/          – Informes exportados de OpenVAS (PDF, XML, JSON)  
├── raw/              – Datos crudos (Nmap, JSON, capturas)  
├── notes/            – Metodología, observaciones, mitigación  
├── assets/           – Diagramas, fotos, topología  
└── README.md         – Este documento  

---

## 8. Referencias

- Serie Linksys WRT54G – Información técnica y variantes  
  https://en.wikipedia.org/wiki/Linksys_WRT54G_series

- Base de datos CVE – Vulnerabilidades asociadas al WRT54G  
  https://www.cve.org  
  (Buscar: “Linksys WRT54G”, “WRT54G firmware”)

- Documentación de OpenVAS / Greenbone  
  https://docs.greenbone.net/

