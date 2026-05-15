# Kafka Lab (3 brokers) - Como rodar

## Requisitos
- Docker e Docker Compose instalados.
- Portas livres: `19092`, `29092`, `39092`.

## Subir o cluster
No diretório onde está o `compose.yaml`, execute:

```bash
docker compose up -d
```

Verifique se os 3 containers estão no ar:

```bash
docker compose ps
```

1. Criar um tópico:

```bash
docker exec kafka-1 /opt/kafka/bin/kafka-topics.sh --create \
  --topic audio-monitoring \
  --bootstrap-server 172.23.168.107:19092 \
  --partitions 3 \
  --replication-factor 3
```

Para remover também os volumes (dados):

```bash
docker compose down -v
```

Para remover dados residuais:

```bash
 docker volume prune -f
```

Para lista topico

```bash
docker exec kafka-1 /opt/kafka/bin/kafka-topics.sh --describe \
  --topic audio-monitoring \
  --bootstrap-server 172.23.168.107:19092
```

Deletar topico

```bash
docker exec kafka-1 /opt/kafka/bin/kafka-topics.sh --delete \
  --topic audio-monitoring \
  --bootstrap-server 172.23.168.107:19092
```
