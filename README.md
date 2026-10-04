# GPU visualisation (VPS)

Статическая 3D-страница (AMD Instinct MI355X), nginx в Docker.

## Деплой
Push в `main` -> GitHub Actions копирует файлы на VPS и делает `docker compose up -d --build`.

Секреты репозитория: `VPS_HOST`, `VPS_USER`, `VPS_SSH_KEY`.

## Подготовка VPS (один раз)
```
sudo apt update && sudo apt install -y docker.io docker-compose-v2
sudo usermod -aG docker $USER
sudo iptables -I INPUT -p tcp --dport 80 -j ACCEPT   # + порт 80/443 в firewall облачного провайдера
```

## Локально
`docker compose up --build` -> http://localhost

## GitHub Pages
Push в `main` -> workflow `pages.yml` публикует `site/` на https://olehhavrilko.github.io/gpu-visualisation/
Один раз включить: Settings -> Pages -> Source: **GitHub Actions**.
