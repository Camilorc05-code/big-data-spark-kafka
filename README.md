Copia y pega este bloque en el editor de GitHub (o en tu archivo `README.md` en VS Code). Al estar dentro de un bloque de código Markdown, mantendrá la estructura, las negritas y los recuadros sin cortarse ni perder formato:

```markdown
# Sustentación Práctica de Big Data: Análisis Batch y Procesamiento Streaming

**Estudiante:** Jhojan Camilo Rodríguez Castañeda  
**Programa:** Ingeniería de Sistemas  
**Institución:** Universidad Nacional Abierta y a Distancia (UNAD)  

---

## 📌 Descripción de la Solución

Este repositorio contiene la solución práctica para el procesamiento de grandes volúmenes de datos utilizando el ecosistema de Apache Spark y Apache Kafka sobre un entorno distribuido en una máquina virtual Linux. El desarrollo consta de dos componentes fundamentales:

1. **Análisis Batch (Lote):** Procesamiento analítico de conjuntos de datos históricos estructurados utilizando PySpark (`tarea3.py`), realizando transformaciones, agregaciones y consultas distribuidas.
2. **Procesamiento en Tiempo Real (Streaming - Anexo 3):** Ingesta continua de métricas simuladas de sensores mediante un Productor en Python (`kafka_producer.py`) transmitidos a un broker de Apache Kafka (puerto 9092), consumidos y procesados en micro-batches en tiempo real mediante Spark Streaming (`spark_streaming_consumer.py`).

---

## 📁 Estructura del Repositorio

```text
.
├── batch/
│   └── tarea3.py                     # Script para procesamiento en lote con PySpark
├── streaming/
│   ├── kafka_producer.py             # Generador y emisor de eventos a Kafka
│   └── spark_streaming_consumer.py   # Consumidor de flujo continuo con Spark Streaming
└── README.md                         # Documentación del proyecto

```

---

## 🛠️ Tecnologías Utilizadas

* **Lenguaje de Programación:** Python 3.x
* **Motor de Procesamiento Distribuido:** Apache Spark 3.5.8 / PySpark
* **Plataforma de Transmisión de Eventos:** Apache Kafka & ZooKeeper
* **Infraestructura Virtualizada:** VirtualBox (Ubuntu Linux)

---

## 🚀 Instrucciones de Ejecución

### 1. Iniciar los Servicios de Infraestructura

Antes de ejecutar los componentes de procesamiento, active el servicio de Apache Kafka en la máquina virtual:

```bash
# Iniciar Kafka Server en segundo plano (puerto 9092)
sudo nohup /opt/Kafka/bin/kafka-server-start.sh /opt/Kafka/config/server.properties > /dev/null 2>&1 &

# Verificar la conectividad del puerto
nc -zv localhost 9092

```

---

### 2. Ejecución del Análisis Batch (Lote)

Para correr el procesamiento masivo de datos estáticos:

```bash
python3 batch/tarea3.py
# O mediante la consola de submisiones de Spark:
spark-submit batch/tarea3.py

```

---

### 3. Ejecución del Procesamiento Streaming (Tiempo Real)

Se requiere la apertura de dos terminales independientes en la máquina virtual:

**Paso A: Iniciar el Productor de Eventos (Terminal 1)**

```bash
python3 streaming/kafka_producer.py

```

**Paso B: Iniciar el Consumidor en Spark Streaming (Terminal 2)**

```bash
spark-submit --conf spark.driver.host=0.0.0.0 --conf spark.ui.port=4040 --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.5.3 streaming/spark_streaming_consumer.py

```

---

## 📊 Monitoreo y Métricas en Spark UI

Durante el procesamiento continuo en tiempo real, las métricas de rendimiento, los micro-batches, los hilos de ejecución y el entorno del motor se pueden auditar en tiempo real desde la consola web:

* **Dirección de acceso:** `http://localhost:4040` o `http://127.0.0.1:4040`
* **Módulos auditados:** Jobs, Stages, Environment y Executors.

```

```
