# Vision y business case - Registro horario de empleados

## Resumen ejecutivo
El proyecto busca un sistema sencillo y confiable para registrar entradas y salidas de empleados, con trazabilidad y reportes basicos. El objetivo es reducir errores manuales, mejorar el cumplimiento laboral y disponer de informacion historica para auditorias y nomina.

## Objetivos
- Registrar entrada y salida en menos de 10 segundos.
- Centralizar historico de horas y ajustes.
- Reducir errores de captura y hojas manuales.
- Proveer reportes basicos para RH y supervisores.

## Alcance (propuesto)
Incluye:
- Registro de entrada y salida (web/movil responsivo).
- Autenticacion y roles (empleado, supervisor, admin).
- Correccion de registros con aprobacion.
- Reportes basicos por periodo y empleado.
- Exportacion CSV/XLS.

Fuera de alcance (por ahora):
- Calculo automatico de nomina.
- Control de acceso fisico (biometria, torniquetes).
- Geolocalizacion obligatoria.

## Stakeholders
- Empleados (registro diario).
- Supervisores (validacion y ajustes).
- RH/Administracion (reportes y auditoria).
- TI (operacion y soporte).

## Metricas de exito
- 95% de registros sin correccion manual.
- Tiempo promedio de registro < 10 s.
- Reportes mensuales generados en < 1 min.

## Caso de negocio (propuesto)
- Beneficio: menos horas administrativas, menos conflictos por horas, mejor visibilidad.
- Costo estimado (muy aproximado): 4 a 8 semanas de trabajo, 1 a 3 personas. Rango amplio: USD 8k a 40k, segun integraciones y controles.
- Factibilidad: alta, tecnologia estandar, riesgo principal en adopcion y procesos internos.

## Modelo de casos de uso (lista)
- UC01 Registrar entrada y salida (detallado)
- UC02 Consultar historial de horas (detallado)
- UC03 Solicitar ajuste de registro
- UC04 Aprobar/rechazar ajustes
- UC05 Gestionar empleados y roles
- UC06 Configurar horarios/turnos
- UC07 Generar reportes y exportar
- UC08 Auditoria de cambios

## Requisitos no funcionales clave (borrador)
- Seguridad: autenticacion, roles y trazabilidad de cambios.
- Disponibilidad: 99% en horario laboral.
- Rendimiento: confirmacion de registro < 2 s.
- Usabilidad: movil primero, accesible en pantalla pequena.
- Integridad: no permitir registros duplicados del mismo tipo sin cierre.

## Riesgos iniciales
- Resistencia al cambio por parte de empleados.
- Datos historicos incompletos si se migra desde hojas.
- Cambios en reglas internas de RH.
- Falta de dispositivo o conectividad para registro.

## Glosario
- Registro: marca de entrada o salida.
- Ajuste: correccion solicitada a un registro.
- Turno: bloque horario asignado a un empleado.
- Auditoria: historial de cambios y quien los hizo.

## Preguntas abiertas
- Identidad: se usara correo, numero de empleado, o ambos?
- Reglas de horas extra: se registran o solo se reportan?
- Se requiere integracion con nomina o ERP?
- Se necesita modo offline o kiosko compartido?
