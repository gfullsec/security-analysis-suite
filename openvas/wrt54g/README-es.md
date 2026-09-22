# Evaluación de Vulnerabilidades – Linksys WRT54G

## 1. Descripción General

**Objetivo:** Linksys WRT54G (router SOHO legado, aislado en laboratorio)  
**Dirección IP:** `192.168.1.250`  
**Tipo de evaluación:** Revisión autenticada de la interfaz web + escaneo de vulnerabilidades  
**Herramientas:** OpenVAS (Greenbone Community Edition), Nmap (opcional), inspección manual  

Esta evaluación se centra en un dispositivo Linksys WRT54G de tipo legado que fue **aislado intencionadamente en un entorno de laboratorio**, conectado a un puerto Ethernet dedicado y separado de la red Wi‑Fi doméstica.  
El objetivo es evaluar su exposición, debilidades de configuración y vulnerabilidades conocidas sin afectar a la red de producción.

---

## 2. Alcance y Objetivos

## 2. Alcance y Objetivos

**Alcance:**

- Interfaz de administración web (`http://192.168.1.250/`) en un segmento aislado de laboratorio  
- Servicios de red expuestos por el dispositivo  
- Versión de firmware y CVEs conocidos  
- Estado de configuración y endurecimiento  

**Objetivos:**

- Identificar servicios expuestos y superficie de ataque  
- Detectar vulnerabilidades conocidas (CVEs) mediante OpenVAS  
- Evaluar debilidades de configuración (credenciales por defecto, firmware obsoleto, protocolos inseguros)  
- Proporcionar pasos de remediación y recomendaciones para un uso seguro (laboratorio, segmento IoT) o para su retirada  

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

**Estructura de ejemplo:**

- **Hallazgo 1 – Configuración por defecto insegura en contexto de laboratorio**  
  - **Severidad:** Crítica  
  - **Descripción:** El dispositivo opera con ajustes casi por defecto, incluyendo credenciales débiles o por defecto y exposición insegura de la interfaz de administración.  
  - **Impacto:** Control total de la configuración del router y posible pivotaje dentro de cualquier segmento de red donde se despliegue.  
  - **Recomendación:** Establecer credenciales fuertes y únicas; endurecer la configuración; restringir el acceso a hosts de confianza; evitar su uso como router principal.

- **Hallazgo 2 – Protocolos de administración inseguros (solo HTTP)**  
  - **Severidad:** Media  
  - **Descripción:** La interfaz de administración solo está disponible mediante HTTP en claro.  
  - **Impacto:** Las credenciales pueden ser interceptadas por un atacante con acceso al mismo segmento de red.  
  - **Recomendación:** Activar HTTPS si es posible; de lo contrario, limitar estrictamente el acceso y considerar su sustitución o uso únicamente en entornos aislados (laboratorio/IoT).

- **Hallazgo 3 – Firmware legado y soporte del fabricante limitado**  
  - **Severidad:** Media  
  - **Descripción:** El dispositivo utiliza firmware antiguo con soporte limitado o inexistente por parte del fabricante.  
  - **Impacto:** Riesgo a largo plazo debido a vulnerabilidades sin parchear y ausencia de actualizaciones de seguridad.  
  - **Recomendación:** Actualizar al firmware más reciente disponible si es posible; de lo contrario, restringir su uso a entornos de laboratorio o roles no críticos y planificar su retirada.

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

