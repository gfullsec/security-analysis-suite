# Red Completa – Evaluación de Vulnerabilidades con OpenVAS

Este directorio contiene la evaluación completa de vulnerabilidades realizada contra toda la red doméstica utilizando **OpenVAS (Greenbone Community Edition)**.  
El objetivo de este módulo es proporcionar una visión de referencia del estado de seguridad de todos los hosts activos, identificar servicios expuestos y resaltar posibles debilidades en la red.

---

## 🔎 Resumen de la Evaluación

**Tarea:** Full Network Scan – Complete Network  
**Fecha:** 19 de septiembre de 2026  
**Duración del escaneo:** 16:34 UTC → 17:38 UTC  
**Total de hosts analizados:** 12  
**Resultados totales (tras filtrar QoD ≥ 70):**  
- **Medio:** 3  
- **Bajo:** 8  
- **Crítico/Alto:** 0  

Este escaneo de referencia proporciona una instantánea inicial del estado de seguridad de la red.  
Los futuros escaneos pueden compararse con esta referencia para seguir mejoras o detectar regresiones.

---

## 🧩 Hallazgos Clave

### ✔ Severidad Media  
Detectado en el host **192.168.1.135** (Smart TV):

- **Vulnerabilidad MITM en renegociación SSL/TLS (CVE‑2009‑3555)**  
- **Vulnerabilidad DoS en renegociación SSL/TLS (CVE‑2011‑1473 / CVE‑2011‑5094)**  
- **Protocolos obsoletos TLSv1.0 / TLSv1.1 habilitados**

Estos problemas son comunes en dispositivos embebidos como televisores inteligentes, que suelen depender de pilas SSL/TLS antiguas.

### ✔ Severidad Baja (Múltiples Hosts)
- **ICMP Timestamp Reply Information Disclosure**  
- **TCP Timestamp Information Disclosure**

Estos hallazgos son informativos y generalmente de bajo riesgo, pero pueden mitigarse mediante reglas de firewall o configuración a nivel de sistema operativo.

---

## 🗂 Estructura del Directorio

- **reports/** → Informes exportados de OpenVAS (PDF, XML, JSON)  
- **raw/** → Datos sin procesar del escaneo, logs y salidas auxiliares  
- **notes/** → Notas del analista, observaciones y acciones de seguimiento  
- **assets/** → Diagramas, capturas de pantalla y material visual de apoyo  
- **README-es.md** → Este documento  

---

## 🎯 Propósito de Este Módulo

Este módulo sirve como base para:

- Establecer una **postura de seguridad de referencia** de toda la red  
- Identificar dispositivos con protocolos obsoletos o inseguros  
- Seguir cambios a lo largo de futuros escaneos  
- Apoyar la documentación del portfolio a través de GitHub Pages  

Esta evaluación forma parte de la **Security Analysis Suite**, que incluye análisis a nivel de host, red y evaluaciones basadas en OSINT.
