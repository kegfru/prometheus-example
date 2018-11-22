# prometheus-example
small example of prometheus with nginx exporter in docker

## Nginx
```
cd nginx
docker build -t nginx4takeport .
docker run -d --rm -p 80:80 --name nginx nginx4takeport
cd ..
```

#### Test
http://192.168.88.225/nginx_status

## Nginx exporter
https://github.com/nginxinc/nginx-prometheus-exporter
```
docker run -d --rm -p 9113:9113 --name nginx-prometheus-exporter nginx/nginx-prometheus-exporter:0.2.0 -nginx.scrape-uri http://192.168.88.225/stub_status
```

#### Test
http://192.168.88.225:9113/metrics

## Prometheus
```
cd prometheus
docker build -t prometheus .
docker run -d --rm -p 9090:9090 --name prometheus prometheus
cd ..
```

#### Test
http://192.168.88.225:9090/graph

## Grafana
```
docker run -d --rm --name=grafana -p 3000:3000 grafana/grafana
```

#### Test
http://192.168.88.225:3000


## Stop
```
docker stop prometheus grafana nginx-prometheus-exporter nginx
```