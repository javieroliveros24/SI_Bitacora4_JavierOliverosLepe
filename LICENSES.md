# LICENSES.md — Licencias del Software Utilizado

Este archivo recoge las licencias de todo el software que forma parte de la infraestructura montada en la Bitácora 4. El objetivo es dejar claro que todo lo que se ha usado es legal y que se conoce bajo qué condiciones se puede utilizar en un entorno profesional.

---

## 1. Apache Guacamole

| Campo | Detalle |
|---|---|
| **Nombre** | Apache Guacamole |
| **Licencia** | Apache License 2.0 |
| **Tipo** | Open Source — licencia permisiva |
| **Uso comercial** | Sí permitido |
| **Fuente oficial** | https://guacamole.apache.org |
| **Texto de la licencia** | https://www.apache.org/licenses/LICENSE-2.0 |

Guacamole es la pasarela web que permite acceder a escritorios remotos desde el navegador, sin necesidad de instalar ningún cliente. En este proyecto se usó para acceder al contenedor con entorno gráfico (webtop) a través del puerto 3000.

---

## 2. OpenSSH

| Campo | Detalle |
|---|---|
| **Nombre** | OpenSSH |
| **Licencia** | Licencia BSD modificada (estilo OpenBSD) |
| **Tipo** | Open Source — licencia permisiva |
| **Uso comercial** | Sí permitido |
| **Fuente oficial** | https://www.openssh.com/portable.html |
| **Texto de la licencia** | https://cvsweb.openbsd.org/src/usr.bin/ssh/LICENCE?rev=HEAD |

Es el software que gestiona las conexiones SSH. En el proyecto se desplegó a través de la imagen `linuxserver/openssh-server`, exponiendo el puerto 2222 para las conexiones remotas seguras.

---

## 3. Docker Engine (Community Edition)

| Campo | Detalle |
|---|---|
| **Nombre** | Docker Engine CE |
| **Licencia** | Apache License 2.0 |
| **Tipo** | Open Source — licencia permisiva |
| **Uso comercial** | Sí permitido |
| **Fuente oficial** | https://docs.docker.com/engine/ |
| **Texto de la licencia** | https://github.com/moby/moby/blob/master/LICENSE |

Motor de contenedores usado para levantar toda la infraestructura del laboratorio mediante `docker-compose up -d`.

---

## 4. Docker Compose

| Campo | Detalle |
|---|---|
| **Nombre** | Docker Compose v2 |
| **Licencia** | Apache License 2.0 |
| **Tipo** | Open Source — licencia permisiva |
| **Uso comercial** | Sí permitido |
| **Fuente oficial** | https://docs.docker.com/compose/ |
| **Texto de la licencia** | https://github.com/docker/compose/blob/main/LICENSE |

Herramienta que permite definir y arrancar los dos contenedores del proyecto (SSH y escritorio remoto) con un solo archivo `docker-compose.yml`.

---

## 5. LinuxServer/openssh-server (imagen Docker)

| Campo | Detalle |
|---|---|
| **Nombre** | linuxserver/openssh-server |
| **Licencia** | GPL v3 |
| **Tipo** | Open Source — licencia copyleft |
| **Uso comercial** | Sí permitido (con condiciones de distribución) |
| **Fuente oficial** | https://docs.linuxserver.io/images/docker-openssh-server/ |
| **Código fuente** | https://github.com/linuxserver/docker-openssh-server |

Imagen oficial de LinuxServer.io usada como servidor SSH en el laboratorio. Fue la base del contenedor `lab_ssh_servidor`.

---

## 6. LinuxServer/webtop (imagen Docker)

| Campo | Detalle |
|---|---|
| **Nombre** | linuxserver/webtop:ubuntu-xfce |
| **Licencia** | GPL v3 |
| **Tipo** | Open Source — licencia copyleft |
| **Uso comercial** | Sí permitido (con condiciones de distribución) |
| **Fuente oficial** | https://docs.linuxserver.io/images/docker-webtop/ |
| **Código fuente** | https://github.com/linuxserver/docker-webtop |

Imagen usada para el contenedor con entorno gráfico XFCE accesible por RDP (puerto 3389) y navegador web (puerto 3000). Fue la base del contenedor `lab_rdp_servidor`.

---

## Resumen

| Software | Licencia | Coste |
|---|---|---|
| Apache Guacamole | Apache 2.0 | Gratuito |
| OpenSSH | BSD modificada | Gratuito |
| Docker Engine CE | Apache 2.0 | Gratuito |
| Docker Compose | Apache 2.0 | Gratuito |
| linuxserver/openssh-server | GPL v3 | Gratuito |
| linuxserver/webtop | GPL v3 | Gratuito |

Todo el software utilizado en este proyecto es de código abierto y gratuito, lo que significa que puede usarse en entornos empresariales sin coste de licencia, siempre que se respeten los términos de cada licencia (básicamente, mantener el aviso de autoría y, en el caso de la GPL, compartir el código fuente si se redistribuye el software modificado).
