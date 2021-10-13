# Wordpress + NGINX + MySQL + Certbot Compose Files
*Last update: 13/10/21*
_WIP_

## Dev
1. Create `db_password.txt` and `db_user.txt`.
2. Run:
```sh
docker compose -f docker-compose.dev.yml up -d
```
## Production
1. Set up docker secrets:
Random password:
```sh
 openssl rand -base64 20 | docker secret create db_root_password -
 openssl rand -base64 20 | docker secret create db_password -
```
Existing password:
```sh
 docker secret create db_root_password EXISTING_PASSWORD
 docker secret create db_password EXISTING_PASSWORD
```
2. Run:
```sh
docker stack deploy --compose-file docker-compose.yml teststack
```

