# pgadmin4 ssh connection sample

## Setup log

```ps1
### Build image and run docker container
> docker compose -f server-compose.yml up -d

### Check default storage permission
> docker exec --user root pgadmin_pga ls -al /var/lib/pgadmin/storage/postgres_example.com/
drwx------    3 pgadmin  root          4096 Apr  1 05:47 ..
-rw-r--r--    1 pgadmin  root           419 Apr  1 06:20 pg-test

### Change shared-storage permission as same as default personal storage
> docker exec --user root pgadmin_pga chown -R pgadmin:root /var/lib/pgadmin/storage
> docker exec --user root pgadmin_pga chmod -R 644 /var/lib/pgadmin/storage/postgres_example.com
> docker exec --user root pgadmin_pga chmod 700 /var/lib/pgadmin/storage/postgres_example.com
> docker exec --user root pgadmin_pga ls -al /var/lib/pgadmin/storage/postgres_example.com
drwx------    3 pgadmin  root          4096 Apr  1 05:47 ..
-rw-r--r--    1 pgadmin  root           419 Apr  1 06:20 pg-test
```
