# CrossfitBuddy Devops

Вся инфраструктура здесь (Nginx, docker-compose)

# Docker Compose
Используется как для бекенда так и для прода.

# Профили

| Профиль | Сервисы | Для кого |
|---|---|---|
| `dev` | `postgres`, `mailpit`, будет дополняться | Бэкенд |
| `prod` | все сервисы `dev` + `backend`, `frontend`, `nginx` | Сервер |

# Бэкенд
Нужны только два файла из этого репо. Не надо клонировать этот репо.

```bash
curl -fsSL -O https://raw.githubusercontent.com/CrossfitBuddy/crossfit-buddy-devops/master/docker-compose.yml
curl -fsSL -O https://raw.githubusercontent.com/CrossfitBuddy/crossfit-buddy-devops/master/.env.example
cp .env.example compose.env
docker compose --profile dev --env-file compose.env up -d
```

# Продакшн

```bash
git clone https://github.com/CrossfitBuddy/crossfit-buddy-devops.git /opt/crossfitbuddy
cd /opt/crossfitbuddy
cp .env.example .env
vi .env          # пишем реальные секреты
docker compose --profile prod up -d
```
# Github Actions 
- Автоматическое обновление компоуз файла и обновление контейнеров на сервере: `.github/workflows/update-compose.yml`
- Авто деплой при изменении мейна фронта или бэкенда: `.github/workflows/deploy.yml`
