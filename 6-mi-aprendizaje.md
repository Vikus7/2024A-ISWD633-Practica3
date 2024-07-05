_Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar._

# Mi aprendizaje

## Por Victor Rodriguez

El dominio de los volúmenes en Docker es crucial para gestionar eficazmente la *persistencia de datos entre contenedores* y el sistema operativo host, permitiendo almacenar y compartir datos. En conjunto con la comprension de volumen-host, volumenes nombrados y volumenes anónimos, son fundamentales para mi formación. <br> 
Los volúmenes anónimos, por ejemplo, son útiles para almacenar datos temporales o no críticos sin necesidad de gestionarlos explícitamente, mientras que los volumenes nombrados proporcionan persistencia y flexibilidad al permitir su reutilización entre múltiples contenedores. Ademas los volúmenes de tipo host ofrecen la capacidad de acceder directamente a archivos del sistema operativo anfitrion, lo cual es vital para integraciones específicas con el entorno de producción. El ejercicio y la configuración de drupal aclararon este aprndizaje, destacando que entender la diferencia entre los tipos de volúmenes y cómo aplicarlos correctamente es crucial para diseñar arquitecturas robustas y escalables.

## Problemas presentados

En la sección 4-volumen-nombrado en el paso 3 ocurrió un error que indica "Drupal no puede escribir en el directorio sites/default/files" porque no tiene permisos adecuados para crearlo automáticamente durante la instalación.

Para su solución fue necesario:

1. Ingresar al contenedor
   ```
   docker exec -it server-drupal bash
   ```
   
2. Crear o navegar al directorio
   ```
   mkdir -p /var/www/html/sites/default/files
   ```
   
3. Modificar los permisos
   ```
   chmod -R 777 /var/www/html/sites/default/files
   ```

4. Reintentar la instalacion. En caso de exito pasara al paso 4.
   En el paso 4, asegurarse de que en Opciones Avanzadas el Host sea `server-postgres`. De establece una conexion exitosa, pasara a Intalarse.
