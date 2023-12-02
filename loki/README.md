# Loki Workshop

## Prerequisite
```bash
docker network create grafanet
```

## Action
**Loki**
```bash
docker run --name loki --network grafanet -d -v $(pwd)/loki-config.yaml:/mnt/config/loki-config.yaml -p 3100:3100 grafana/loki:2.9.1 -config.file=/mnt/config/loki-config.yaml
```

**Promtail**
```bash
docker run --name promtail --network grafanet -d -v $(pwd)/promtail-config.yaml:/mnt/config -v $(pwd)/log:/var/log --link loki grafana/promtail:2.9.1 -config.file=/mnt/config/promtail-config.yaml
```

**or Grafana Agent**
```bash
docker run --name agent --network grafanet -v $(pwd):/etc/agent/data -v $(pwd)/agent.yaml:/etc/agent/agent.yaml grafana/agent:v0.38.1
```

**Dashboard**
```bash
docker run --network grafanet --name=grafana -d -p 3000:3000 grafana/grafana
```

**Information:**
datasource: `loki`
http://loki:3100
