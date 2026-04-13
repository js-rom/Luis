# UC01 Registrar entrada y salida

## Objetivo
Permitir que un empleado registre su entrada o salida de manera rapida y confiable.

## Actores
- Empleado (principal)
- Sistema

## Precondiciones
- El empleado esta autenticado.
- Existe un turno o jornada activa (o se permite registro libre).

## Disparador
El empleado selecciona "Registrar entrada" o "Registrar salida".

## Flujo basico
1. El empleado abre la pantalla de registro.
2. El sistema muestra el ultimo estado (sin registro, entrada registrada, salida registrada).
3. El empleado elige la accion disponible (entrada o salida).
4. El sistema valida que la accion es consistente con el ultimo estado.
5. El sistema registra la marca con fecha y hora.
6. El sistema confirma el registro y muestra el resumen del dia.

## Flujos alternos
A1. Accion no permitida
- En el paso 4, el sistema detecta una accion invalida.
- El sistema muestra el motivo y no registra cambios.

A2. Error de red
- En el paso 5, falla la comunicacion.
- El sistema guarda el intento localmente y solicita reintentar.

## Postcondiciones
- Se crea un registro con timestamp y usuario.
- Se actualiza el estado del empleado para el dia.

## Reglas de negocio
- No se permite doble entrada sin salida intermedia.
- Todo cambio queda en auditoria.
