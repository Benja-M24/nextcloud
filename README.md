# nextcloud
Next cloud container prepared to work on Ubuntu server with traefik-ServerManager

# To be executed in the server after nextcloud installation

## Steps
1. Add Missing Database Indices
Command:

> docker compose exec -u www-data nextcloud php occ db:add-missing-indices

Purpose: This command adds any missing database indices, improving query performance.
Execution: Run this command in the terminal where your docker-compose.yml file is located.

2. Enable Maintenance Background Jobs - Cron
Set Maintenance Window:
Command:

> docker compose exec -u www-data nextcloud php occ config:system:set maintenance_window_start --type=integer --value=8

Purpose: Sets the maintenance window to 5 am GMT-3 (which corresponds to 8 am UTC).
Note: Ensure you understand the time conversion between your local time and UTC.

Verify Cron Setup:
Command:

> docker compose exec -u www-data nextcloud php occ background-job:list

Purpose: Lists background jobs to verify they are correctly configured.

Ensure Background Jobs Use System Cron:
Command:

> docker compose exec -u www-data nextcloud php occ background:cron

Purpose: Ensures background jobs are set to use the system cron for scheduling.