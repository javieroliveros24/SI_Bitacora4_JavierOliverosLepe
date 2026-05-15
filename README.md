<img width="1080" height="484" alt="conexion_al_contenedor jpg" src="https://github.com/user-attachments/assets/17c2f7c7-762c-4c67-b5d3-c7a59775699d" />
# [cite_start]Bitácora Técnica IV: Laboratorio de Teletransportación Digital (SSH y RDP) [cite: 4, 5]

Este proyecto documenta la administración de un clúster de servidores remotos mediante el uso de contenedores Docker, aplicando técnicas de conexión segura (SSH) y entornos gráficos

---

## 🛠️ 1. Preparación del Entorno

Se ha utilizado **Docker Compose** para levantar una infraestructura idéntica en segundos, evitando errores de kernel comunes en máquinas virtuales tradicionales. 

* **Comando de despliegue:** `docker-compose up -d`
* **Servicios levantados:** Un servidor de consola (SSH) y uno gráfico (Webtop/RDP). 

<div align="center">
  <img src="conexion_al_contenedor.jpg.png" alt="Conexión Inicial SSH" width="80%">
  <p><i>Captura 1: Verificación de la conexión inicial al contenedor vía SSH.</i></p>
</div>

<img width="1080" height="484" alt="conexion_al_contenedor jpg" src="https://github.com/user-attachments/assets/badb6d32-ba06-416b-8ae4-f37d802aa313" />

---

## 🔑 2. SSH: Configuración de Clave Pública

Siguiendo los criterios de evaluación sobre protección de recursos, se ha eliminado el acceso por contraseña para usar criptografía de clave pública. 

### Paso A: Generación de llaves
Se generó un par de llaves usando el algoritmo **ed25519** en la máquina anfitriona. 



### Paso B: Transferencia y Hardening
Se copió la llave pública al servidor mediante `ssh-copy-id` para permitir el acceso directo y seguro. 

<img width="837" height="480" alt="pasoB" src="https://github.com/user-attachments/assets/f2371bcb-0a66-4611-949e-61ed88724f66" />

Paso c:

<img width="973" height="312" alt="pasoC" src="https://github.com/user-attachments/assets/8b1da214-4352-414c-a780-1cdbcf493552" />

---

## 🖥️ 3. RDP: Escritorio Remoto

Se ha configurado el acceso gráfico para tareas que requieren interfaz visual. 

**Protocolo:** RDP sobre el puerto **3389**.**Alternativa Web:** Puerto **3000** mediante Apache Guacamole. 

### Resolución de Incidencias
Se identificó un "error de protocolo/sesión" al intentar duplicar conexiones, lo cual se resolvió gestionando correctamente las sesiones activas en el servidor. 

<img width="403" height="241" alt="conexion_esc_remoto" src="https://github.com/user-attachments/assets/446313c8-a9f5-49c1-b659-444639917e3f" />


<img width="952" height="1071" alt="ServidorInstalado" src="https://github.com/user-attachments/assets/63722483-dbe6-4d43-b824-04e1d019eab2" />


### Evidencia de Éxito
[cite_start]Se creó el archivo `PRUEBA_LOGRADA.txt` en el escritorio del contenedor como prueba de acceso y manipulación remota. 

<div align="center">
  <img src="pruebalograda.png" alt="Archivo de prueba en escritorio" width="80%">
</div>

<img width="912" height="722" alt="pruebalograda" src="https://github.com/user-attachments/assets/9b578943-7c75-4a89-86b8-b7b71b497893" />

FALLO SOLCIONADO

<img width="555" height="132" alt="escritorio_remotoFALLO" src="https://github.com/user-attachments/assets/2dfe5838-dadc-4b3b-8987-4bdce2db6c9f" />


---

## 📝 4. Reflexión Final

SSH es la herramienta preferida en entornos profesionales porque es extremadamente **ligera y segura**. A diferencia de RDP, no consume ciclos de CPU ni memoria RAM en renderizar una interfaz gráfica que el servidor no necesita. [cite_start]Además, permite gestionar miles de servidores simultáneamente mediante scripts de automatización, algo mucho más complejo de lograr con interfaces visuales. 
