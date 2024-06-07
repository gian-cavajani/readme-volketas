## Usuarios

#### Campos del Modelo

- `id` (INTEGER): Clave primaria autoincremental.
- `empleadoId` (INTEGER): ID del empleado asociado al usuario. Este campo es obligatorio y único.
- `rol` (ENUM): Rol del usuario, que puede ser 'admin' o 'normal'. Este campo es obligatorio.
- `email` (STRING): Correo electrónico del usuario. Este campo es obligatorio y único.
- `password` (STRING): Contraseña del usuario. Este campo es obligatorio.
- `activo` (BOOLEAN): Estado de activación del usuario. Por defecto, es `false`.

#### Relaciones

- Empleados - Usuarios
  - Relación uno a uno (1:1) donde un usuario tiene un empleado asociado.
