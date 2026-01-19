# DevOps Demo Project

Учебный pet-проект для Junior DevOps инженера. Проект демонстрирует базовый DevOps-пайплайн: **Docker → CI (GitHub Actions) → docker-compose → мониторинг (Prometheus + Grafana)**.

---

##  Что реализовано

* Dockerized Python (Flask) приложение
* Health-check endpoint (`/health`)
* CI pipeline на GitHub Actions
* Сборка Docker-образа в CI
* Запуск контейнера и проверка работоспособности
* docker-compose для локального запуска нескольких сервисов
* Мониторинг: Prometheus + Grafana

---

##  Структура проекта

```
.
├── app/                    # Приложение
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── monitoring/             # Мониторинг
│   ├── prometheus.yml
│
├── nginx/ # Reverse proxy
│   ├── nginx.conf
│   └── Dockerfile
│
├── docker-compose.yml      # Локальная инфраструктура
├── .github/
│   └── workflows/
│       └── ci.yml          # CI pipeline
├── .gitignore
└── README.md
```

---

##  Docker

### Сборка образа вручную

```bash
docker build -t devops-demo-app ./app
```

### Запуск контейнера

```bash
docker run -d -p 5000:5000 devops-demo-app
```

### Проверка приложения

```bash
curl http://localhost:5000/health
```

Ожидаемый ответ:

```json
{"status": "ok"}
```

---

##  Docker Compose

Для локального запуска всей системы:

```bash
docker-compose up -d
```

Что поднимается:

* Flask приложение
* Prometheus
* Grafana

Остановка:

```bash
docker-compose down
```

---

##  Мониторинг

### Prometheus

* URL: [http://localhost:9090](http://localhost:9090)
* Сбор метрик с приложения

### Grafana

* URL: [http://localhost:3000](http://localhost:3000)
* Логин: `admin`
* Пароль: `admin`

---

##  CI / GitHub Actions

CI pipeline запускается автоматически при:

* push в ветки `main`, `develop`

### Что делает CI:

1. Checkout репозитория
2. Сборка Docker-образа
3. Запуск контейнера
4. Health-check (`/health`)
5. Очистка контейнера


---

##  Цель проекта

Проект создан для:

* обучения DevOps инструментам
* практики CI/CD
* демонстрации навыков 

---

##  Что можно улучшить

* Добавить тесты
* Добавить CD (деплой)
* Добавить secrets и environments
* Добавить alerting в Grafana
* Перейти на Kubernetes

---

##  Автор

**GeorgyGar**

---

