# Kafka Docker
Dette repository har 2 forskellige Kafka-konfigurationer på 2 forskellige branches:
- **`main`**: køre Kafka, Zookeeper, Schema Registry, Kafka UI
- **`Prometheus`**: køre Kafka, Zookeeper, Schema Registry, Kafka UI, Prometheus, Grafana, Loki og de nødvendige exporters for at få Kafka og Prometheus til at kommunikere.

## Services

### **Zookeeper**
- **Port**: 2181
- **Navn**: docker-kafka-zookeeper-1

### **Kafka**
- **Port**: 9092
- **Navn**: docker-kafka-kafka-1

### **Schema Registry**
- **Port**: 8081
- **Navn**: kafka-schema-registry

### **Kafka UI**
- **Port**: 8080
- **Navn**: kafka-ui

### **Prometheus**
- **Port**: 9090
- **Navn**: prometheus

### **Node Exporter**
- **Port**: 9100
- **Navn**: node-exporter

### **Kafka Exporter**
- **Port**: 9308
- **Navn**: kafka-exporter

### **Grafana**
- **Port**: 3000
- **Navn**: docker-kafka-grafana-1

### **Loki**
- **Port**: 3100
- **Navn**: docker-kafka-loki-1

## Setup

Når du har hentet dette repository, skal du redigere `docker-compose.yml` og ændre `KAFKA_ADVERTISED_LISTENERS` til at bruge din WSL IP-adresse. Når du ændrer IP'en, skal den se sådan her ud, bare med din egen IP: `PLAINTEXT://172.25.224.0:9092`.

For at finde din WSL IP-adresse:
1. Åbn kommandoprompt (cmd) på din Windows-maskine.
2. Skriv `ipconfig` og tryk Enter.
3. Find "Ethernet adapter vEthernet" sektionen og kopier IP-adressen, der er opført der (fx. `172.25.224.0`).

### Commands

- **Start Docker**:  
  `docker-compose up -d`

- **Stop Docker**:  
  `docker-compose down -v`

- **Tjek Docker-netværket**:  
  `docker network inspect docker-kafka_kafka-net`

## Bugs

Der kan være en bug i Kafka UI, hvor den ikke automatisk kan finde et topic, og URL'en ikke ændres korrekt. Hvis det sker, skal du selv opdatere URL'en til noget lignende: `http://localhost:8080/ui/clusters/local/all-topics/<dit-topic-navn>`

## Bemærkninger

Jeg har ikke haft tid til at teste det hele, så der kan være andre fejl.
