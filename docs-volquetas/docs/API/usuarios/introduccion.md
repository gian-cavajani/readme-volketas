# Introduccion

## Endpoint `/api/usuarios`

Esta API permite la gestión de usuarios en un sistema. Incluye la creación de nuevos usuarios, autenticación, activación de usuarios y la obtención de la lista de usuarios.

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
