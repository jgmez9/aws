1. ¿Qué diferencia hay entre la política de confianza y la política de permisos? ¿Qué pasaría si el rol tuviera solo una de las dos?

La política de confianza (Trust Policy) define quién puede asumir el rol, por ejemplo, una instancia EC2. La política de permisos (Permissions Policy) define qué acciones puede realizar el rol sobre los recursos de AWS.

Si el rol tuviera solamente la política de confianza, la instancia podría asumir el rol, pero no tendría permisos para acceder al bucket S3. Si tuviera solamente la política de permisos, no podría asumir el rol porque no existiría una política que autorizara a la instancia a utilizarlo.

2. ¿Por qué es más seguro que la instancia use un rol en vez de guardar una llave de acceso con aws configure?

Es más seguro porque el rol proporciona credenciales temporales que AWS renueva automáticamente. No es necesario guardar claves de acceso permanentes en la instancia, lo que reduce el riesgo de que sean robadas o expuestas. Además, permite administrar los permisos desde IAM y aplicar el principio de menor privilegio.

3. Con la política leer-reportes, ¿la instancia podrá listar el contenido del bucket? ¿Y borrar reporte.txt? Explica por qué.

La instancia podrá listar el contenido del bucket si la política incluye el permiso s3:ListBucket sobre el ARN del bucket.

No podrá borrar reporte.txt porque la política de lectura no incluye el permiso s3:DeleteObject. Para eliminar un archivo se necesita ese permiso sobre el ARN del objeto correspondiente.

4. En el error del paso 20, ¿qué le falta por hacer antes de poder borrar el rol?

Antes de eliminar el rol, es necesario desvincularlo de la instancia EC2 y eliminar las políticas asociadas al rol. AWS no permite eliminar un rol que todavía esté siendo utilizado o que tenga políticas administradas o en línea asociadas.

5. Si mañana la instancia también necesita subir archivos al bucket, ¿qué cambiarías y en cuál de los dos archivos?

Modificaría el archivo de la política de permisos para agregar la acción s3:PutObject sobre los objetos del bucket.

No cambiaría la política de confianza, porque la instancia ya está autorizada a asumir el rol. Solo se deben ampliar los permisos necesarios para permitir la carga de archivos.