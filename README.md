## INTEGRANTES.
| Nombre | Cargo | URL GitHub |
|---|:---:|---:|
| Daniel Alquinga | :technologist: Desarrollador | https://github.com/superdavi/Practica1_Grupo2.git |
| Daniel Baldeon | :technologist: Desarrollador | https://github.com/debpdhs/Practica1_Grupo2 |
| Bryan Miño | :technologist: Desarrollador |https://github.com/bmiomi/tareadocker |
| Wilson Segovia | :technologist: Desarrollador | https://github.com/segoviawilson/Practica1_Grupo2.git|
| Leonardo Tuguminago | :technologist: Desarrollador | https://github.com/ltuguminago/fastapi-app.git |

# 1. Análisis de vulnerabilidades con docker scout mediante un flujo de github actions

Con base en el laboratorio de fastapi-app, deberan subir la imagen que le corresponde a su grupo y las aplicaciones a su repositorio de github. Construir la imagen, subir a docker hub y realizar el análisis de vulnerabilidades con docker scout mediante un flujo de github actions.

# 2. Configuración e Instalación

### PASO 1: 📂 Estructura de Archivos

```bash
    Proyecto Vehículos
    |
    |____ .env
    |____ README.md
    |____ despliegues.txt
    |____ init.sql
```
### PASO 2: Iniciar sessión en DockerHub y crear repositorio

<img width="946" height="553" alt="Crear repositorio DockerHub" src="https://github.com/user-attachments/assets/38ceed27-051c-4595-9506-e0a57ea78ddf" />

### PASO 3: En la termina, iniciar sessión con las credenciales de DockerHub

```bash
docker login -u ltuguminago
```

**Salida Esperada**

<img width="740" height="178" alt="Iniciar session en terminal DockerHub" src="https://github.com/user-attachments/assets/ae2b8967-a48c-4e87-ba05-63ef1d185a2d" />

### PASO 4: Construir imagen de Docker MultiStage

```bash
docker build -t hello-multistage -f Dockerfile-multistage
```

**Salida Esperada**

<img width="1236" height="475" alt="Construccion imagen multi-stage" src="https://github.com/user-attachments/assets/0ccd88dc-5adc-4e90-a61d-82aff8a19829" />

### PASO 5: Revisamos la imagen construida

```bash
docker images
```

**Salida Esperada**

<img width="547" height="58" alt="images" src="https://github.com/user-attachments/assets/d277c838-60b0-40a9-8d57-48fa83a9fe12" />

### PASO 6: Tagear la imagen "usuario_DockerHub/repositorio"

```bash
docker tag hello-multistage:latest ltuguminago/fastapi-app:v1
```

**Salida Esperada**

<img width="812" height="176" alt="Tager imagen" src="https://github.com/user-attachments/assets/e0156856-66c7-4d47-8304-3d0b9b8264de" />

### PASO 7: Subir imagen al DockerHub

```bash
docker push ltuguminago/fastapi-app:v1
```

**Salida Esperada**

<img width="786" height="231" alt="subir imagen al dockerHub" src="https://github.com/user-attachments/assets/f133972b-e90d-42d7-94b5-0585c47829d4" />

### PASO 8: Revizar la imagen subida en el repositorio de DockerHub

<img width="924" height="681" alt="revisamos imagen subida en el dockerhub" src="https://github.com/user-attachments/assets/8ba65d1e-c85d-47f0-a5b7-266be99fd76f" />

### PASO 9: Iniciar sessión en GitHub y crear repositorio

<img width="909" height="791" alt="Crear repositorio GitHub" src="https://github.com/user-attachments/assets/c3251ee3-1a85-4bab-b553-c938fcc098c1" />

### PASO 9: El repositorio debe contener los siguientes archivos

<img width="222" height="185" alt="structura fastapi" src="https://github.com/user-attachments/assets/1613fcad-19fd-4b3a-adfe-088c9fec9182" />

### PASO 10: Ingresar al siguiente directorio

- Setting/secrets and variables/Actions

### PASO 11. Crear las variables con las credenciales deL DockerHub

```bash
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

**Salida Esperada**

<img width="1197" height="774" alt="secrets and varibles" src="https://github.com/user-attachments/assets/ed654656-0c58-458f-a643-62bb0fca9e69" />

### PASO 12: Ingresar al siguiente directorio

- Action/Docker image/ Configure

**Salida Esperada**

<img width="1170" height="558" alt="Docker images configure" src="https://github.com/user-attachments/assets/5517d68b-5aae-416e-ac3e-4457281e8391" />

### PASO 13: Ingresar al siguiente directorio



### Configuración Adicional



**Archivo .env**

```env
MYSQL_ROOT_PASSWORD=admin123
MYSQL_DATABASE=dbVehiculos
MYSQL_USER=usuario
MYSQL_PASSWORD=clave123
```

### Comandos Útiles

```bash
# Ver contenedores en ejecución
docker ps

# Ver logs de un contenedor
docker logs db-mysql-vehiculos

# Conectar a MySQL directamente
docker exec -it db-mysql-vehiculos mysql -u root -p

# Detener todos los contenedores
docker stop db-mysql-vehiculos web_phpmyadmin_vehiculos

# Eliminar contenedores
docker rm db-mysql-vehiculos web_phpmyadmin_vehiculos

# Eliminar red
docker network rm netw-vehiculos
```


# 3. Conclusiones

**Logros Alcanzados**

- Implementación Exitosa: Se logró configurar un sistema distribuido utilizando Docker, separando la base de datos (MySQL) de la interfaz de administración (phpMyAdmin) en contenedores independientes.
- Gestión Eficiente de Redes: La creación de la red personalizada netw-vehiculos, permitió la comunicación segura entre contenedores, eliminando la necesidad de exponer servicios innecesarios al host.
- Persistencia de Datos Garantizada: El uso de volúmenes Docker (mysql_data), asegura que la información de propietarios y vehículos se mantenga intacta entre reinicios del sistema.
- Automatización de Inicialización: El script init.sql, automatiza la creación de tablas y datos de prueba, reduciendo errores manuales y garantizando consistencia en diferentes entornos.
- Separación de Configuración: El archivo .env, centraliza las variables sensibles, mejorando la seguridad y facilitando el despliegue en diferentes ambientes.

**Beneficios Obtenidos**

- Portabilidad: El sistema puede ejecutarse en cualquier máquina con Docker instalado
- Escalabilidad: Fácil agregar nuevos servicios o réplicas de contenedores
- Mantenibilidad: Cada servicio se actualiza independientemente
- Aislamiento: Los fallos en un contenedor no afectan a otros servicios
- Reproducibilidad: El entorno se puede recrear exactamente en cualquier momento


# 4. Recomendaciones.

 - Es necesario crear primero la red Docker y luego el contenedor, ya que este inconveniente se presento al momento de ejecutar la tarea. 
 - Se debe validar que la versión de MySQL sea compatible con phpMyAdmin, ya que una incompatibilidad entre ambas versiones podría causar errores al intentar levantar el contenedor.
