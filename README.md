#### RUN
docker-compose up -d

#### STOP
docker-compose down -v


#####
find . -type d -exec chmod 0755 {} \;
find . -type f -exec chmod 0644 {} \;