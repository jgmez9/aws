
1. ¿Por qué el nombre de tu bucket tuvo que ser distinto al de tus compañeros si cada uno tiene su propia cuenta?

Porque los nombres de los buckets de Amazon S3 deben ser únicos globalmente dentro de una partición de AWS, no solamente dentro de una cuenta.

2. El usuario del paso 21 pudo leer un archivo, pero en el paso 22 no pudo ver la lista. ¿Qué acción le faltaba en la política?

Le faltaba la acción s3:ListBucket, que permite listar los objetos almacenados dentro de un bucket. La acción s3:GetObject únicamente permite leer o descargar objetos específicos.

3. En la política, ¿qué significa el `/*` al final del `Resource`? ¿Qué pasaría si se quitara?

El /* representa todos los objetos que se encuentran dentro del bucket.

Por ejemplo, arn:aws:s3:::mi-bucket/* permite aplicar permisos sobre los archivos del bucket. Si se quitara, el recurso haría referencia únicamente al bucket y no a sus objetos, por lo que el permiso s3:GetObject no funcionaría correctamente.


4. ¿En qué se diferencia compartir un archivo con un enlace temporal de hacer público el bucket?

Un enlace temporal, como una URL prefirmada, permite acceder a un archivo específico durante un tiempo limitado, sin hacer público el bucket. En cambio, hacer público el bucket puede permitir que cualquier persona acceda a los objetos autorizados públicamente, mientras esa configuración permanezca activa.


5. Según el modelo de responsabilidad compartida, si alguien deja un bucket público con datos de clientes, ¿de quién es la responsabilidad?

La responsabilidad recae principalmente en el cliente o administrador de la cuenta AWS que configuró incorrectamente el bucket. Según el modelo de responsabilidad compartida, AWS protege la infraestructura de la nube, mientras que el cliente es responsable de configurar correctamente los permisos y proteger sus datos.