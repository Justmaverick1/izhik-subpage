# Страница подписки Izhik

Этот `index.html` подменяет только внешний вид. Контейнер Remnawave по-прежнему отдаёт подписку приложениям.

На сервере, в папке с `docker-compose.yml` страницы подписки (часто `/opt/remnawave/subscription`):

```bash
curl -fsSL -o izhik-index.html https://raw.githubusercontent.com/Justmaverick1/izhik-subpage/refs/heads/main/index.html
```

В сервис `remnawave-subscription-page` добавьте volume:

```yaml
volumes:
  - ./izhik-index.html:/opt/app/frontend/index.html:ro
```

Пересоздайте контейнер:

```bash
docker compose up -d --force-recreate remnawave-subscription-page
```

Цвета, логотип и кнопки берутся из этого файла. Список приложений и ссылки по-прежнему приходят из панели.
