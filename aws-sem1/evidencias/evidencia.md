1. ¿Qué podía hacer el usuario justo después de crearlo, antes de adjuntarle una política? ¿Por qué?

El usuario no podía realizar acciones sobre los servicios de AWS porque inicialmente no tenía permisos asignados. Esto ocurre porque AWS IAM aplica el principio de mínimo privilegio, según el cual un usuario debe recibir únicamente los permisos necesarios para realizar sus funciones.

2. En el error del paso 13, ¿qué tres datos te dice el mensaje?

El error AccessDenied permite identificar:
1. La identidad que intenta realizar la acción: el usuario lector-juan.
2. La acción que intenta ejecutar: iam:ListUsers.
3. El motivo del rechazo: el usuario no tiene una política que le permita realizar esa operación.
3. ¿Por qué cambió el ARN al renombrar el usuario?

Porque el ARN identifica al recurso dentro de AWS e incluye el nombre del usuario. Al cambiar dev-juan por lector-juan, AWS actualizó el ARN para reflejar el nuevo nombre.

4. ¿Por qué AWS obliga a borrar las llaves antes de borrar el usuario?

Porque las llaves de acceso son credenciales asociadas al usuario IAM. AWS exige eliminar primero los elementos asociados, como las llaves y las políticas, para evitar que queden credenciales o configuraciones vinculadas a una identidad que se quiere eliminar.

5. ¿Qué pasaría si le hubieras dado AdministratorAccess en vez de solo lectura? ¿En qué caso real estaría justificado?

Si hubiera asignado AdministratorAccess, el usuario tendría permisos administrativos amplios para gestionar los servicios y recursos de AWS, incluyendo crear, modificar y eliminar recursos.

Estaría justificado en casos específicos, como un administrador responsable de gestionar toda la infraestructura de una cuenta AWS, siempre que exista una necesidad real y controles de seguridad adecuados. No sería recomendable para un desarrollador que únicamente necesita consultar información de EC2.