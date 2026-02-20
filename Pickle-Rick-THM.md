# Reporte de Auditoría: SQL Injection Manual y Automatizado
**Fecha:** 19 de Febrero, 2026
**Autor:** Cristian-Lopez-A
**Objetivo:** Pickle Rick --- TryHackMe

# Vulnerabilidad encontrada: 
Misconfiguration in Sudo Permissions .

#Cómo se encontraron:
Command sudo -l showed NOPASSWD: ALL.

#Cómo las explote: 
Executed commands as root to read sensitive files in /root.

#Recomendación profesional: 
Remove NOPASSWD entries from the /etc/sudoers file and follow the principle of least privilege.

