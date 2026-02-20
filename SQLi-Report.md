# Reporte de Auditoría: SQL Injection Manual y Automatizado
**Fecha:** 19 de Febrero, 2026
**Autor:** Cristian-Lopez-A
**Objetivo:** testphp.vulnweb.com

---

## 1. Resumen Ejecutivo
Se ha identificado una vulnerabilidad crítica de **Inyección SQL (SQLi)** en el parámetro `cat` de la aplicación web. Esta vulnerabilidad permite a un atacante no autenticado extraer información sensible de la base de datos, incluyendo nombres de usuario, contraseñas y datos de la aplicación.

## 2. Fase de Reconocimiento
Mediante el uso de **Nmap**, se identificó que el servidor corre sobre:
- **Puerto 80:** HTTP (Apache)
- **Tecnología:** PHP

## 3. Análisis de Vulnerabilidad
Al realizar una prueba manual añadiendo una comilla simple (`'`) al parámetro `cat`:
`http://testphp.vulnweb.com/listproducts.php?cat=1'`

**Resultado:** El servidor devolvió un error de sintaxis de MySQL, confirmando que la entrada del usuario no está siendo filtrada correctamente.

## 4. Explotación (Prueba de Concepto)
Para demostrar el impacto, se utilizó la herramienta **sqlmap** con el siguiente comando:
```bash
sqlmap -u "[http://testphp.vulnweb.com/listproducts.php?cat=1](http://testphp.vulnweb.com/listproducts.php?cat=1)" --batch --dbs
