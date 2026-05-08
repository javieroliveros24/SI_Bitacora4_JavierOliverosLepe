# [cite_start]Bitácora Técnica IV: Laboratorio de Teletransportación Digital (SSH y RDP) [cite: 4, 5]

[cite_start]Este proyecto documenta la administración de un clúster de servidores remotos mediante el uso de contenedores Docker, aplicando técnicas de conexión segura (SSH) y entornos gráficos

---

## 🛠️ 1. Preparación del Entorno

[cite_start]Se ha utilizado **Docker Compose** para levantar una infraestructura idéntica en segundos, evitando errores de kernel comunes en máquinas virtuales tradicionales. 

* **Comando de despliegue:** `docker-compose up -d`
* **Servicios levantados:** Un servidor de consola (SSH) y uno gráfico (Webtop/RDP). 

<div align="center">
  <img src="conexion_al_contenedor.jpg.png" alt="Conexión Inicial SSH" width="80%">
  <p><i>Captura 1: Verificación de la conexión inicial al contenedor vía SSH.</i></p>
</div>

---

## 🔑 2. SSH: Configuración de Clave Pública

[cite_start]Siguiendo los criterios de evaluación sobre protección de recursos, se ha eliminado el acceso por contraseña para usar criptografía de clave pública. 

### Paso A: Generación de llaves
[cite_start]Se generó un par de llaves usando el algoritmo **ed25519** en la máquina anfitriona. 

<div align="center">
  <img src="pasoB.png" alt="Generación de Llaves" width="80%">
</div>

### Paso B: Transferencia y Hardening
[cite_start]Se copió la llave pública al servidor mediante `ssh-copy-id` para permitir el acceso directo y seguro. 

<div align="center">
  <img src="pasoC.png" alt="Transferencia de Llave" width="80%">
</div>

---

## 🖥️ 3. RDP: Escritorio Remoto

[cite_start]Se ha configurado el acceso gráfico para tareas que requieren interfaz visual. 

* [cite_start]**Protocolo:** RDP sobre el puerto **3389**.
* [cite_start]**Alternativa Web:** Puerto **3000** mediante Apache Guacamole. 

### Resolución de Incidencias
[cite_start]Se identificó un "error de protocolo/sesión" al intentar duplicar conexiones, lo cual se resolvió gestionando correctamente las sesiones activas en el servidor. 

<div align="center">
  <img src="escritorio_remotoFALLO.png" alt="Error de Sesión RDP" width="60%">
</div>

### Evidencia de Éxito
[cite_start]Se creó el archivo `PRUEBA_LOGRADA.txt` en el escritorio del contenedor como prueba de acceso y manipulación remota. 

<div align="center">
  <img src="pruebalograda.png" alt="Archivo de prueba en escritorio" width="80%">
</div>

---

## 📝 4. Reflexión Final

[cite_start]**¿Por qué SSH es más utilizado en servidores de producción que RDP?** 

SSH es la herramienta preferida en entornos profesionales porque es extremadamente **ligera y segura**. A diferencia de RDP, no consume ciclos de CPU ni memoria RAM en renderizar una interfaz gráfica que el servidor no necesita. [cite_start]Además, permite gestionar miles de servidores simultáneamente mediante scripts de automatización, algo mucho más complejo de lograr con interfaces visuales. 
---
[cite_start]**Autor:** Javier Oliveros 
[cite_start]**Fecha de entrega:** 08/05/2026 