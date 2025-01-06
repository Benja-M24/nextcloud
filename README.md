# nextcloud
Next cloud container prepared to work on Ubuntu server with traefik-ServerManager

# To be executed in the server after nextcloud installation
1. BD IMPORVE MISSING INDICES
```
docker compose exec -u www-data nextcloud php occ db:add-missing-indices

```
2. ENABLE MANTAINENCE BACKGROUND JOBS - CRON
    - To set the maintenance window (6 am gmt-3), you'll need to run this command after the stack is up:
    docker compose exec -u www-data nextcloud php occ config:system:set maintenance_window_start --type=integer --value=9

    - To verify the cron setup is working correctly, run:
    docker compose exec -u www-data nextcloud php occ background:job:list

    - To ensure background jobs are set to use system cron:
    docker compose exec -u www-data nextcloud php occ background:cron

3. 