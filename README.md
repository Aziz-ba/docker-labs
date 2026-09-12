# 🐳 Docker Labs - from a single container to a multi-service stack

A progressive, hands-on journey through **Docker** and **Docker Compose**, building up step by step (`etape1` → `etape4`) from a single web server to a full **NGINX + PHP-FPM + MySQL** stack running a WordPress-style application.

Each stage is self-contained so you can see exactly what each new concept adds.

---

## 📶 The stages

| Stage | Focus | Highlights |
|-------|-------|-----------|
| **etape1** | NGINX basics | Serving static content, custom `nginx.conf` |
| **etape2** | Custom PHP image | `Dockerfile` on `php:7.4-fpm`, PDO/MySQL extensions |
| **etape3** | Web + app wiring | NGINX reverse-proxying to PHP-FPM |
| **etape4** | Full stack with Compose | 3 services (NGINX + PHP-FPM + MySQL 8) on a shared bridge network |

---

## 🧱 Stage 4 architecture

```
        :8080          internal            internal
 client ────▶ [ nginx ] ────▶ [ php-fpm ] ────▶ [ mysql:8.0 ]
               http            script            database_wp
                    └──────── wp-network (bridge) ────────┘
```

Defined in [`etape4/docker-compose.yml`](etape4/docker-compose.yml).

---

## 🚀 Run the full stack (etape4)

```bash
cd etape4
cp .env.example .env          # set your DB credentials
# place your PHP/WordPress app in ./app  (git-ignored)
docker compose up -d
# open http://localhost:8080
```

> The application source (`app/`) is git-ignored - drop in WordPress or any PHP app and Compose mounts it into the PHP-FPM and NGINX containers. Database credentials come from `.env`, never hard-coded.

---

## 🛠️ Tech Stack

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=flat-square&logo=docker&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

---

## 📄 License

Released under the [MIT License](LICENSE).
