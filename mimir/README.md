# Mimir Workshop

## Action
**Mimir**
```bash
docker run  --name mimir --network grafanet  -d -p 9009:9009 -v $(pwd)/demo.yaml:/etc/mimir/demo.yaml grafana/mimir --config.file=/etc/mimir/demo.yaml
```

**Mimir**
```bash
docker run --name otel-collector --network grafanet -p 4318:4318 -p 4317:4317 -d -v $(pwd)/otel-collector.yaml:/etc/otelcol-contrib/otel-collector.yaml otel/opentelemetry-collector-contrib:0.90.0
```

**Dashboard**
```bash
docker run --name=grafana --network grafanet -d -p 3000:3000 grafana/grafana
```

**Information:**
datasource: `prometheus`
ttp://mimir:9009/prometheus

**How to testing with python(version>=3.x)**
```bash
pip install -I -r requirements.txt
```