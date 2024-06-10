# Introduccion

## Endpoint `/api/usuarios`

El endpoint de usuarios permite gestionar usuarios en el sistema. Proporciona funcionalidades para registrar nuevos usuarios, iniciar sesión, obtener información del usuario actual y administrar usuarios existentes, como cambiar contraseñas y desactivar cuentas.

### Usuarios

| Método                         | Descripción                | Tipo de Token |
| ------------------------------ | -------------------------- | ------------- |
| `GET` /api/usuarios            | Obtener Usuarios           | Admin         |
| `GET` /api/usuarios/:id        | Obtener Usuario            | Admin         |
| `GET` /api/usuarios/inactivos  | Obtener Usuarios inactivos | Admin         |
| `POST` /api/usuarios           | Nuevo Usuario              | Sin Token     |
| `POST` /api/usuarios/login     | Login Usuario              | Sin Token     |
| `POST` /api/usuarios/confirmar | Confirmar Usuario          | Admin         |
| `PUT` /api/usuarios/:id        | Modificar Usuario          | Admin         |
| `DELETE` /api/usuarios/:id     | Borrar Usuario             | Admin         |
