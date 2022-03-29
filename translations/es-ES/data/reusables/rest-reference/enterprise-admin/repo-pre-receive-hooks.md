## Ganchos de pre-recepción del repositorio

La API de Ganchos de Pre-recepción para Repositorios te permite ver y modificar la imposición de los ganchos de pre-recepción que están disponibles para un repositorio.

### Atributos de objeto

| Nombre              | Tipo        | Descripción                                               |
| ------------------- | ----------- | --------------------------------------------------------- |
| `name (nombre)`     | `secuencia` | El nombre del gancho.                                     |
| `enforcement`       | `secuencia` | El estado de imposición del gancho en este repositorio.   |
| `configuration_url` | `secuencia` | URL para la terminal en donde se configuró la imposición. |

Los valores posibles para *enforcement* son `enabled`, `disabled` y `testing`. El valor `disabled` indica que el gancho de pre-recepción no se ejecutará. El valor `enabled` indica que se ejecutará y rechazará cualquier carga que resulte en un estado diferente a zero. El valor `testing` indica que el script va a ejecutarse pero no va a causar que se rechace ninguna carga.

`configuration_url` podría ser un enlace a este repositorio, al propietario de su organización o a su configuración global. La autorización para acceder a esta terminal en `configuration_url` se determina a nivel de administrador de sitio o de propietario.