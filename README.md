# GPU visualisation (Oracle VPS)

Статическая 3D-страница (AMD Instinct MI355X), nginx в Docker.

## Деплой
Push в `main` -> GitHub Actions копирует файлы на VPS и делает `docker compose up -d --build`.

Секреты репозитория: `VPS_HOST`, `VPS_USER`, `VPS_SSH_KEY`.

## Подготовка VPS (один раз)
```
sudo apt update && sudo apt install -y docker.io docker-compose-v2
sudo usermod -aG docker $USER
sudo iptables -I INPUT -p tcp --dport 80 -j ACCEPT   # + порт 80/443 в Security List Oracle
```

## Локально
`docker compose up --build` -> http://localhost
