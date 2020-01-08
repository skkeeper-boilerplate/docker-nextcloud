# nextcloud-docker

## Backup


```bash
docker run --rm --volumes-from nextcloud_db -v c:/tmp/backup:/backup ubuntu bash -c "cd /var/lib/postgresql/data && tar cvf /backup/db.tar ."

docker run --rm --volumes-from nextcloud -v c:/tmp/backup:/backup ubuntu bash -c "cd /var/www/html && tar cvf /backup/instance.tar ."
```

## Restore

```bash
docker run --rm -v nextcloud_db:/db -v nextcloud_data:/ndata -v c:/tmp/backup:/backup ubuntu bash -c "tar -xvf /backup/db.tar -C /db"


docker run --rm -v nextcloud_db:/db -v nextcloud_data:/ndata -v c:/tmp/backup:/backup ubuntu bash -c "tar -xvf /backup/instance.tar -C /ndata"
```


## References

https://medium.com/@mannycodes/create-an-nginx-reverse-proxy-with-docker-a1c0aa9078f1