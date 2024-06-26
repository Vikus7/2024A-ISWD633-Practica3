# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

Los principales aprendizajes logrados al trabajar con volúmenes en Docker, incluyendo volumen-host, volumenes nombrados y volumenes anónimos, son fundamentales para mi formación. Primero, entender la diferencia entre estos tipos de volúmenes y cómo aplicarlos correctamente es crucial para diseñar arquitecturas robustas y escalables. Los volúmenes anónimos, por ejemplo, son útiles para almacenar datos temporales o no críticos sin necesidad de gestionarlos explícitamente, mientras que los volumenes nombrados proporcionan persistencia y flexibilidad al permitir su reutilización entre múltiples contenedores. Ademas los volúmenes de tipo host ofrecen la capacidad de acceder directamente a archivos del sistema operativo subyacente, lo cual es vital para integraciones específicas con el entorno de producción. 

En el paso 3 ocurrio un error que indica "Drupal no puede escribir en el directorio sites/default/files" porque no tiene permisos adecuados para crearlo automáticamente durante la instalación.

Para su solucion fue necesario:
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
