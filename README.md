# docker-infra

Infraestructura como código con Docker Compose. Levanta un stack completo
con una app Node.js, base de datos MySQL y Nginx como reverse proxy —
todo reproducible con un solo comando.

> Laboratorio personal para practicar Docker, contenedores y la base
> sobre la que luego corro mis pipelines de CI/CD y pruebas E2E.

---

## Stack

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

---

## Servicios

| Servicio | Imagen            | Puerto | Descripción                           |
| -------- | ----------------- | ------ | -------------------------------------- |
| `app`    | Node.js 20 Alpine | 3000   | API REST con healthcheck               |
| `db`     | MySQL 8.0         | 3306   | Base de datos con volumen persistente  |
| `nginx`  | Nginx Alpine      | 80     | Reverse proxy hacia la app             |

---

## Estructura
docker-infra/

├── app/

│   ├── index.js        # API Node.js

│   ├── package.json

│   └── Dockerfile

├── nginx/

│   └── nginx.conf      # Configuración del reverse proxy

├── docker-compose.yml

├── .env.example

├── .gitignore

└── LICENSE

---

## Instalación

```bash
git clone https://github.com/tu-usuario/docker-infra.git
cd docker-infra
cp .env.example .env
```

Edita `.env` con tus valores:
MYSQL_ROOT_PASSWORD=rootpassword

MYSQL_DATABASE=appdb

MYSQL_USER=appuser

MYSQL_PASSWORD=apppassword

## Levantar el stack

```bash
docker-compose up -d
```

Servicios disponibles:

- App vía Nginx: `http://localhost`
- Healthcheck: `http://localhost/health`

## Detener

```bash
docker-compose down
```

Para eliminar también los volúmenes:

```bash
docker-compose down -v
```

---

## Próximos pasos

Este stack es la base de mi laboratorio DevSecOps. Los siguientes repos
de mi perfil se conectan con este:

- [`cypress-e2e-suite`](https://github.com/tu-usuario/cypress-e2e-suite) — pruebas E2E contra la API levantada aquí.
- [`jenkins-devsecops-pipeline`](https://github.com/tu-usuario/jenkins-devsecops-pipeline) — pipeline que construye, escanea y prueba este stack.

---

## Contacto




