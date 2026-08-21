# Tabla de Pruebas — Reto 2: Sede Central Segmentada

| # | Prueba | Resultado esperado | Resultado obtenido | Evidencia |
|---|--------|--------------------|--------------------|-----------|
| 1 | Cliente corporativo obtiene IP por DHCP | IP en rango 10.20.10.100-200 | *(completar)* | evidencias/dhcp-corp.png |
| 2 | Cliente invitado obtiene IP por DHCP | IP en rango 10.20.20.100-200 | *(completar)* | evidencias/dhcp-guest.png |
| 3 | Cliente corporativo accede a Internet | Conectividad exitosa | *(completar)* | evidencias/corp-internet.png |
| 4 | Cliente corporativo accede al servicio del Grupo 4 (10.255.0.40) | Conectividad exitosa | *(completar, requiere integración con Grupo 4)* | evidencias/corp-dmz.png |
| 5 | Cliente invitado accede a Internet | Conectividad exitosa | *(completar)* | evidencias/guest-internet.png |
| 6 | Cliente invitado intenta acceder a red corporativa (10.20.10.0/24) | Bloqueado | *(completar)* | evidencias/bloqueo-guest-corp.png |
| 7 | Intento bloqueado aparece en logs de FortiGate | Log visible con política DENY-GUEST-to-CORP | *(completar)* | evidencias/log-bloqueo.png |
| 8 | Administración HTTPS/SSH solo desde red corporativa | Acceso denegado desde otras redes | *(completar)* | evidencias/admin-restringido.png |
| 9 | Envío de logs al NOC/SOC (Grupo 5) | Eventos recibidos en 10.50.10.10 | *(completar, requiere integración con Grupo 5)* | evidencias/syslog-noc.png |

## Notas
- Las pruebas 4 y 9 dependen de la integración con otros grupos, se completarán en el ensamble del sábado.
- Las pruebas 1-3, 5-8 se pueden validar de forma aislada en el laboratorio local antes del ensamble.