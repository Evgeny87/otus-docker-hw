# OTUS Docker & Git Homework

Репозиторий содержит конфигурационные файлы веб-серверов Apache и Nginx, настроенных в рамках учебного задания.

## Что было сделано:
1. **Балансировка Apache**: Настроен конфиг `balancer.conf` для работы на трех портах (8080, 8081, 8082).
2. **Nginx в Docker**: Запущен контейнер Nginx, выполняющий роль Load Balancer для Apache.
3. **Настройка Git**:
   - Инициализирован локальный репозиторий.
   - Настроен `.gitignore` для исключения логов и системных файлов.
   - Настроена авторизация на GitHub через **SSH-ключ**.

## Запуск Nginx в Docker
Для запуска контейнера с пробросом конфигурационного файла использовалась команда:
```bash
docker run -d --name nginx-otus-bridge -p 80:80 -v ~/otus-docker/nginx/conf.d/default.conf:/etc/nginx/conf.d/default.conf:ro nginx:1.28.2
```
Команда монтирует локальный конфиг `default.conf` внутрь контейнера в режиме "только чтение" (`:ro`).

## Структура проекта:
- `apache/balancer.conf` — конфигурация VirtualHosts для Apache.
- `nginx/conf.d/default.conf` — конфигурация upstream балансировщика.
