# Crear imagen personalizada
## 1. Título  
 Despliegue backend con base datos local

## 2. Tiempo de duración  
40 minutos.  

## 3. Fundamentos  

La práctica se basa en Docker y contenedores para desplegar aplicaciones de manera aislada y reproducible. Permite levantar un backend Java, una base de datos PostgreSQL y PGAdmin como herramienta de administración, todo en un entorno controlado, sin afectar el sistema operativo local.

Los contenedores garantizan portabilidad, consistencia en el ambiente de desarrollo y facilitan el aprendizaje de la administración de bases de datos y servicios web.

## 4. Conocimientos previos  

Conceptos básicos de bases de datos y SQL.

Conceptos de contenedores y Docker: imágenes, contenedores, volúmenes y Docker Compose.

Fundamentos de APIs REST y backend Java (Spring Boot u otra tecnología usada).

## 5. Objetivos a alcanzar  

Comprender el uso de Docker Compose para levantar múltiples servicios interconectados.

Desplegar y probar un backend que se comunique con una base de datos PostgreSQL.

Configurar y administrar la base de datos con PGAdmin.

Familiarizarse con volúmenes de Docker para persistencia de datos.

Validar la correcta comunicación entre servicios en contenedores y el entorno local.
  
## 6. Equipo necesario  

Docker Desktop instalado y funcionando.

Editor de texto (Notepad, VS Code, Sublime Text, etc.).


## 7. Material de apoyo  

Proyecto base: https://github.com/maguaman2/tendencias-mar22-security.git

Tutoriales en youtube

Documentación oficial de Docker: https://docs.docker.com/

Tutoriales de APIs REST con Java.
## 8. Procedimiento  
Clonar el repositorio del proyecto ingresando al siguiente link :https://github.com/maguaman2/tendencias-mar22-security

<img width="1893" height="945" alt="image" src="https://github.com/user-attachments/assets/2ba5ff3b-ede3-4a17-bfb8-99523dcf989f" />

clic en code y opne en github desktop para que se nos clone 

<img width="456" height="392" alt="image" src="https://github.com/user-attachments/assets/408a2487-918f-472f-a927-d17e2b084b6a" />

una vez clonado ingresamod desde el cmd al proyecto clonado y se vera de esta manera 


<img width="712" height="47" alt="image" src="https://github.com/user-attachments/assets/4924f574-b5c5-457a-b4f0-3fb04243c003" />

Ahora creamos las siguientes carpetas : 

<img width="1067" height="180" alt="image" src="https://github.com/user-attachments/assets/95d8be1b-b2c5-490a-8530-8eaa4ee55430" />

ingresamos el siguiente comando para editar docker-compose.yml

<img width="1213" height="57" alt="image" src="https://github.com/user-attachments/assets/d1839439-1f4e-4d78-af85-33e828f1434f" />

Se habrira un bloc de notas donde tendremos que poner lo siguiente 

<img width="763" height="828" alt="image" src="https://github.com/user-attachments/assets/518a393f-0d8c-4bab-8098-86cf62e998bb" />

Construir y levantar los contenedores

con el siguiente comando 

<img width="1462" height="37" alt="image" src="https://github.com/user-attachments/assets/0014252d-9e47-47c3-a4a6-f768d564effa" />

Esto construye las imágenes y levanta los contenedores:

backend_app → aplicación Java

postgres_db → base de datos PostgreSQL

pgadmin_panel → interfaz de administración de PostgreSQL

Verificar que estén levantados:

docker compose ps

<img width="1468" height="312" alt="image" src="https://github.com/user-attachments/assets/01cff418-40b4-4f05-a856-97c693c1d707" />

Verificar que el backend está funcionando

<img width="1230" height="62" alt="image" src="https://github.com/user-attachments/assets/6e9a1b26-3d28-4bb8-bc94-638c987d2440" />

Verificar los endpoints

<img width="1201" height="52" alt="image" src="https://github.com/user-attachments/assets/cb6f764d-411c-4a70-a6cc-1e266e3d651a" />

Acceder a pgAdmin
Abrir navegador → http://localhost:5050

Email: admin@admin.com

Password: admin

Configurar conexión a PostgreSQL:

Host: postgres_db

Puerto: 5432

Usuario: postgres

Contraseña: 1234

<img width="1917" height="932" alt="image" src="https://github.com/user-attachments/assets/a4c1f4d5-3381-485f-b0a9-db25a4c30246" />


no olvidar crear el .env en el proeycto y definir lo siguiente : 

<img width="1907" height="988" alt="image" src="https://github.com/user-attachments/assets/9c60180c-81f3-487d-b22f-fc5cad01c5cf" />

en cuanto al Multi-stage se aplico en el dockerfile

<img width="710" height="646" alt="image" src="https://github.com/user-attachments/assets/29aab8db-0d9c-4d77-a0a6-4ca580ab4a00" />

Primera etapa (build): usa Maven + JDK para compilar el proyecto y generar el JAR.

Segunda etapa (runtime): usa solo JRE, copia el JAR de la etapa anterior y lo ejecuta.

Beneficio: imagen final más pequeña y limpia, sin herramientas de compilación.


## 9. Resultados esperados:

Tener levantados tres contenedores: backend, PostgreSQL y PGAdmin.

Acceder a la API del backend mediante curl o navegador y recibir respuestas correctas.

Acceder a PGAdmin y conectar con la base de datos PostgreSQL correctamente.

Observar persistencia de datos en los volúmenes locales de Docker.

## 10. Bibliografías
Merkel, D. (2014). Docker: Up & Running. O’Reilly Media.

Introducción completa a Docker, contenedores, imágenes y docker-compose.

Hightower, K., Burns, B., & Beda, J. (2017). Kubernetes: Up & Running. O’Reilly Media.

Explica conceptos de contenedores y cómo se integran en entornos productivos, útil para entender multi-stage builds y despliegues.

