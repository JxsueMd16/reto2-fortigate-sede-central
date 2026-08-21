# Informe — Reto 2: Sede Central Segmentada con FortiGate

**Curso:** Telecomunicaciones — UMG Cobán
**Docente:** Ing. Byron Figueroa
**Grupo:** 2 — Sede Central
**Integrante(s):** *(completar)*

## 1. Resumen del segmento

El Grupo 2 implementó la sede administrativa de la infraestructura empresarial integrada,
separando el tráfico de usuarios corporativos y de invitados mediante un FortiGate VM,
con políticas de seguridad verificables y restricción de administración.

## 2. Decisiones técnicas

- **Arquitectura de virtualización:** se utilizó GNS3 nativo en macOS (Apple Silicon M5)
  conectado a un servidor GNS3 VM (Ubuntu ARM64) sobre VMware Fusion. Se identificó
  que el appliance FortiGate VM (x86-64) no cuenta con aceleración por hardware en esta
  plataforma, por lo que corre bajo emulación de software (QEMU TCG), lo cual generó
  arranques lentos y una advertencia de inconsistencia de disco tras un apagón inesperado
  de la VM anfitriona por sobrecarga de CPU.
- **Límite de licencia trial:** la versión de evaluación de FortiGate permite un máximo de
  3 políticas de firewall activas (vdom-max=3). Se resolvió consolidando el acceso a
  Internet y al servicio del Grupo 4 en una sola política (`CORP-to-Internet`, destino "all"),
  liberando espacio para la política de bloqueo explícito invitados→corporativa.
- **Segmentación:** dos redes internas independientes (10.20.10.0/24 corporativa,
  10.20.20.0/24 invitados) con DHCP propio cada una, cumpliendo el principio de mínimo
  privilegio exigido por el reto.

## 3. Incidentes durante el desarrollo

- Apagado accidental de la VM de GNS3 mientras el FortiGate procesaba operaciones de
  disco, generando una advertencia de posible inconsistencia de sistema de archivos.
  Se optó por no forzar un escaneo completo (`execute disk scan`) por el riesgo de
  tiempos de espera excesivos bajo emulación, y se continuó monitoreando la estabilidad
  del sistema en los pasos siguientes sin observar comportamiento anómalo adicional.

## 4. Conclusiones

*(completar tras finalizar pruebas del sábado: qué funcionó, qué se tuvo que ajustar en
el ensamble, y una reflexión breve sobre la integración con los demás grupos)*