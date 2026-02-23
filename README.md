# ⚙️ Data Pipeline Automation

> Raw data is like crude oil — it only has value once you refine it.

An automated **ETL data pipeline** built with Apache Airflow, Python and PostgreSQL. Handles multi-source data ingestion, cleaning, transformation and loading — fully containerized with Docker Compose.

---

## 🔄 Pipeline Overview

```
[Source A: CSV files]  ──┐
[Source B: REST API]   ──┼──► EXTRACT ──► TRANSFORM ──► LOAD ──► PostgreSQL
[Source C: Database]   ──┘
                                               │
                                        Airflow DAG
                                     (scheduled / triggered)
```

---

## 🗂️ Project Structure

```
data-pipeline-automation/
│
├── dags/
│   └── pipeline_dag.py           # Airflow DAG definition
│
├── etl/
│   ├── extract.py                # Data ingestion from multiple sources
│   ├── transform.py              # Cleaning, normalization, feature engineering
│   └── load.py                   # Insert/upsert into PostgreSQL
│
├── config/
│   └── settings.py               # DB credentials, paths, schedule config
│
├── sql/
│   └── create_tables.sql         # Schema initialization
│
├── docker-compose.yml            # Airflow + PostgreSQL + pgAdmin stack
├── Dockerfile
├── requirements.txt
└── README.md
```

---

## ⚙️ Quickstart

```bash
# Clone and start the full stack
docker-compose up -d

# Access Airflow UI
http://localhost:8080
# user: airflow / pass: airflow

# Access pgAdmin
http://localhost:5050
```

---

## 🐳 Services (Docker Compose)

| Service | Port | Description |
|---|---|---|
| Airflow Webserver | 8080 | DAG monitoring & triggering |
| PostgreSQL | 5432 | Data warehouse |
| pgAdmin | 5050 | DB management UI |

---

## 🔧 ETL Steps

**Extract**
- CSV files from local or remote storage
- REST API calls with pagination handling
- SQL queries from source databases

**Transform**
- Null value handling & type casting
- Deduplication & outlier filtering
- Feature normalization & aggregation

**Load**
- Upsert into PostgreSQL target tables
- Load validation & row count checks
- Error logging & alerting

---

## ⏱️ Scheduling

The DAG runs on a configurable cron schedule:

```python
schedule_interval="0 6 * * *"   # Every day at 6:00 AM
```

---

## 📦 Tech Stack

- **Python 3.11**
- **Apache Airflow 2.9** — orchestration
- **Pandas** — data transformation
- **SQLAlchemy + psycopg2** — DB connection
- **PostgreSQL** — data storage
- **Docker / Docker Compose** — containerization

---

## 👤 Author

**ELOUAFI Abderrahmane**  
Ingénieur Big Data & Cloud — ENSET Mohammedia  
[LinkedIn](https://www.linkedin.com/in/abderrahmane-elouafi-43226736b/) • [Portfolio](https://my-first-porfolio-six.vercel.app/)
