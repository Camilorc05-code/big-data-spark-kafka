# Sustentación Práctica de Big Data: Análisis Batch y Procesamiento Streaming

**Estudiante:** Jhojan Camilo Rodríguez Castañeda  
**Programa:** Ingeniería de Sistemas  
**Institución:** Universidad Nacional Abierta y a Distancia (UNAD)  

---

## 📌 Descripción de la Solución

Este repositorio contiene la implementación práctica de procesamiento de Big Data utilizando el ecosistema de Apache Spark y Apache Kafka sobre una máquina virtual con entorno Linux. La solución se divide en dos componentes principales:

1. **Análisis Batch (Lote):** Procesamiento de datos históricos mediante PySpark (`tarea3.py`), realizando carga estructurada, transformaciones, agrupaciones y agregaciones analíticas.
2. **Procesamiento en Tiempo Real (Streaming - Anexo 3):** Ingesta continua de eventos simulados mediante un Productor en Python (`kafka_producer.py`) transmitidos a un broker de Apache Kafka (puerto 9092), consumidos y procesados en micro-batches en tiempo real con Spark Streaming (`spark_streaming_consumer.py`).

---

## 🛠️ Tecnologías Utilizadas

* **Lenguaje:** Python 3.x
* **Procesamiento Distribuido:** Apache Spark 3.5.8 / PySpark
* **Ingesta de Eventos:** Apache Kafka & ZooKeeper
* **Infraestructura:** Máquina Virtual (VirtualBox - Ubuntu Linux)

---

## 🚀 Instrucciones de Ejecución

### 1. Requisitos Previos
Asegurarse de tener activos los servicios de ZooKeeper y el Broker de Kafka en la máquina virtual:

```bash
# Iniciar ZooKeeper (puerto 2181)
/opt/Kafka/bin/zookeeper-server-start.sh /opt/Kafka/config/zookeeper.properties &

# Iniciar Kafka Server (puerto 9092)
/opt/Kafka/bin/kafka-server-start.sh /opt/Kafka/config/server.properties &
