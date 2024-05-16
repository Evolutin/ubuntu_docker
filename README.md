**1. Обновление ubuntu:**

```
apt update -y && apt upgrade -y
```

**2. Установка репозитория Docker:**

```
apt-get update
apt-get install ca-certificates curl
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
chmod a+r /etc/apt/keyrings/docker.asc
```


```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  tee /etc/apt/sources.list.d/docker.list > /dev/null
 apt-get update
```


**3. Установка Docker:**

```
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

**4. Создаем сеть для docker:**
```
docker network create lan
```

**5. Установить файлу _acme.json_ для traefik права на чтение 600**

<details><summary>Запуск docker-compose файла</summary>

```
docker compose up -d
```
</details>

<details><summary>Команды CrowdSec</summary>

```
docker exec crowdsec cscli metrics
```
```
docker exec crowdsec cscli decisions list
```
```
docker exec crowdsec cscli bouncers add bouncer-traefik
```
</details>
