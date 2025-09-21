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

<img width="222" height="185" alt="structura fastapi" src="https://github.com/user-attachments/assets/9e959e1b-bfc3-4a77-b489-b578ade1ac24" />


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


### PASO 13: Reemplazar el contenido del workflows actual por el contenido del archivo fastapi.ylm

- Modificar el parametro IMAGE_NAME con el usuario del DockerHub + el nombre del repositorio.

```bash
IMAGE_NAME: ltuguminago/fastapi-app
```

- Modificar el parametro push con el valor de true, para que la imagen suba al DockerHub

```bash
push: true
```

- Guardar el archivo con el nombre "fastapi.ylm

<img width="893" height="1070" alt="workflows" src="https://github.com/user-attachments/assets/b983d468-f1e5-4488-b8ed-f765a9a69fe8" />

### PASO 14: Ingresar al siguiente directorio

- Action

****

# 3. Conclusiones

**Logros Alcanzados**

- 

**Beneficios Obtenidos**

- 


# 4. Recomendaciones.

 - 
