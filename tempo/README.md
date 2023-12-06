# Tempo Workshop

## Prerequisite
```bash
docker network create grafanet
```

## Action
```bash
docker run  --name tempo --network grafanet  -d -p 3200:3200 -p 4318:4318 -v $(pwd)/tempo.yaml:/etc/tempo.yaml grafana/tempo -config.file=/etc/tempo.yaml
```

**Dashboard**
```bash
docker run --name=grafana --network grafanet -d -p 3000:3000 grafana/grafana
```

**Information:**
user: `admin`
pass: `admin`
datasource: `tempo`
http://tempo:3200