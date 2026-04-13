# UC02 Consultar historial de horas

## Objetivo
Permitir que un empleado o supervisor consulte el historial de registros por periodo.

## Actores
- Empleado (principal)
- Supervisor (secundario)
- Sistema

## Precondiciones
- El usuario esta autenticado.
- Tiene permisos para el empleado consultado.

## Disparador
El usuario selecciona "Historial" y define un periodo.

## Flujo basico
1. El usuario elige el rango de fechas.
2. El sistema valida el rango.
3. El sistema recupera los registros del periodo.
4. El sistema muestra lista y totales por dia.
5. El usuario puede exportar a CSV/XLS.

## Flujos alternos
A1. Rango demasiado amplio
- En el paso 2, el sistema solicita reducir el rango.

## Postcondiciones
- No se modifican datos.

## Reglas de negocio
- El usuario solo puede ver datos permitidos por su rol.
