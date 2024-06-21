# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

### Principales Aprendizajes Logrados

#### 1. **Comprensión de los Tipos de Volúmenes en Docker**
   Antes de realizar la práctica, tenía un conocimiento teórico básico sobre los volúmenes en Docker, pero la práctica me permitió entender profundamente las diferencias entre los volúmenes nombrados, los volúmenes anónimos y los volúmenes tipo host. Ahora puedo decidir cuándo usar cada tipo según las necesidades específicas de persistencia de datos y manejo de configuraciones.

#### 2. **Manejo de Volúmenes Tipo Host**
   Aprendí cómo montar un directorio del host en un contenedor y cómo este puede ser útil para compartir datos entre el host y los contenedores. Comprendí también cómo los permisos del sistema de archivos del host pueden afectar la funcionalidad dentro del contenedor y cómo solucionarlo.

#### 3. **Uso de Volúmenes Nombrados**
   Descubrí cómo los volúmenes nombrados facilitan la gestión y persistencia de datos en Docker, permitiendo almacenar datos de manera más organizada y accesible. Aprendí a crear, inspeccionar y eliminar volúmenes nombrados, y entendí el concepto de mountpoints y su estructura en el sistema de archivos del host.
   

### Documentación de Solución de Problemas

#### Problema: Permisos en Drupal

Durante la instalación de Drupal, me encontré con un problema relacionado con los permisos del directorio `sites/default/files`, que impedía la creación automática del directorio necesario.

**Solución:**
1. Accedí al contenedor de Drupal:
   ```sh
   docker exec -it server-drupal /bin/bash
   ```

2. Creé el directorio `files` manualmente si no existía:
   ```sh
   mkdir -p /var/www/html/sites/default/files
   ```

3. Cambié los permisos del directorio para asegurarse de que el servidor web (usuario `www-data`) tuviera acceso:
   ```sh
   chown -R www-data:www-data /var/www/html/sites/default/files
   chmod -R 755 /var/www/html/sites/default/files
   ```

4. Salí del contenedor y continué con la instalación de Drupal.

Esta solución me enseñó la importancia de entender y gestionar los permisos en contenedores, y cómo estas habilidades son esenciales para asegurar el correcto funcionamiento de aplicaciones en entornos Docker.

### Conclusión

Esta práctica me proporcionó un entendimiento profundo y práctico de la gestión de volúmenes y redes en Docker, y me enseñó a configurar y solucionar problemas en aplicaciones multi-contenedor. Estas habilidades son fundamentales para mi desarrollo profesional, ya que Docker es una herramienta crucial en el desarrollo y despliegue de aplicaciones modernas.
