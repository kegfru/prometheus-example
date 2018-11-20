# prometheus-example
small example of prometheus with nginx exporter in docker

## Nginx
```
docker build -t nginx4takeport .
docker run -d --rm -p 80:80 --name nginx nginx4takeport
```

#### Test
http://192.168.88.225/nginx_status

## Nginx exporter
```
docker run -d --rm -p 9113:9113 --name nginx-prometheus-exporter nginx/nginx-prometheus-exporter:0.2.0 -nginx.scrape-uri http://192.168.88.225/nginx_status
```

#### Test
http://192.168.88.225:9113/metrics

## Prometheus
```
docker build -t prometheus .
docker run -d --rm -p 9090:9090 --name prometheus prometheus
```

#### Test
http://192.168.88.225:9090/graph

