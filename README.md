# FastWay

Plataforma web para la gestión de solicitudes de transporte y movilidad, desarrollada en PHP con MySQL. Permite a los usuarios registrarse, iniciar sesión y administrar sus solicitudes de servicio desde un panel con estadísticas y control de estados.

## Características

- Registro e inicio de sesión de usuarios con contraseñas cifradas (`password_hash`)
- Dashboard con estadísticas en tiempo real: total de solicitudes, pendientes, en proceso y completadas
- Gestión completa (CRUD) de solicitudes: crear, editar, eliminar y listar
- Control de estados por solicitud (Pendiente, En proceso, Completado, Cancelado) actualizable al instante
- Validaciones en el cliente (JavaScript) y en el servidor (PHP)
- Confirmación antes de eliminar una solicitud
- Interfaz responsiva construida con Bootstrap 5

## Stack técnico

| Componente | Tecnología |
|---|---|
| Backend | PHP (PDO) |
| Base de datos | MySQL |
| Frontend | HTML, CSS, JavaScript |
| UI | Bootstrap 5, Bootstrap Icons |

## Arquitectura

```
FastWay/
├── includes/
│   ├── conexion.php        Conexión PDO a la base de datos y manejo de sesión
│   ├── auth.php             Función requireLogin() para proteger rutas privadas
│   ├── header.php           Navegación, alertas de sesión y apertura del layout
│   └── footer.php           Cierre del layout y scripts
├── css/
│   └── style.css            Estilos personalizados sobre Bootstrap
├── js/
│   └── script.js            Validaciones de formularios y confirmaciones
├── index.php                 Página de bienvenida
├── login.php                  Inicio de sesión
├── registro.php                Registro de nuevos usuarios
├── logout.php                   Cierre de sesión
├── dashboard.php                 Panel con estadísticas y solicitudes recientes
├── solicitudes.php                Listado de solicitudes con cambio de estado
├── crear_solicitud.php             Formulario de creación de solicitudes
├── editar_solicitud.php             Formulario de edición de solicitudes
├── eliminar_solicitud.php            Eliminación de solicitudes
└── database.sql                       Script de creación de la base de datos
```

## Modelo de datos

**usuarios**
- `id`, `nombre`, `correo` (único), `password` (hash), `creado_en`

**solicitudes**
- `id`, `id_usuario` (relación con `usuarios`), `tipo`, `origen`, `destino`, `descripcion`, `estado`, `fecha`, `creado_en`

Cada solicitud pertenece a un usuario (`id_usuario`), con eliminación en cascada si el usuario es eliminado.

## Requisitos previos

- PHP 8 o superior
- MySQL o MariaDB
- Servidor local tipo XAMPP, WAMP o similar (o PHP built-in server)

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.
