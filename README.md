# Data Science Project - Fast and Safe

## Team Members

* Juan Sebastian Sierra - 202343656
* Jhoan Sebastian Fernandez - 2222772
* Luis Felipe Londoño - 2343105

---

# Project Description

This project implements an ETL (Extract, Transform, Load) process and a Data Warehouse for the course project: **Fast and Safe**.

Starting from an operational database exported in SQL format (`copia-BD.sql`), the system:

1. Extracts the relevant information.
2. Transforms the data by applying business rules.
3. Builds dimensions and fact tables.
4. Generates CSV files for analysis.
5. Automatically loads the information into PostgreSQL.

---

# Architecture

Operational Database (SQL Dump)

↓

Extraction (Extract)

↓

Transformation (Transform)

↓

Data Warehouse

↓

PostgreSQL + CSV

↓

Power BI

---

# Technologies Used

* Python 3.11+
* Pandas
* NumPy
* PostgreSQL 12
* Docker
* pgAdmin 4
* SQLAlchemy
* psycopg2
* Power BI

---

# Project Structure

```text
proyecto_ciencia_de_datos/

├── data/
│   ├── copia-BD.sql
│   └── fast_and_safe_dw.sql
│
├── docs/
│
├── dw_data/
│   ├── Dim_Ciudad.csv
│   ├── Dim_Cliente.csv
│   ├── ...
│   ├── Fact_Servicios.csv
│   └── Fact_Novedades.csv
│
├── src/
│   ├── extract.py
│   ├── transform.py
│   ├── load.py
│   └── test_postgres.py
│
├── main.py
├── requirements.txt
└── README.md
```

# Installation

## 1. Clone the repository

```bash
git clone <https://github.com/Sebastian6174/Proyecto_Ciencia_de_Datos.git>
cd proyecto_ciencia_de_datos
```

## 2. Create a virtual environment

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

### PostgreSQL and pgAdmin Configuration

The project uses Docker Compose to deploy PostgreSQL and pgAdmin.

## Start the services

Navigate to the project root and run:

```bash
docker compose up -d
```

Verify that the containers are running:

```bash
docker ps
```

You should see the following containers:

```text
ciencia_datos
pgadmin4CD
```

## Configuration Used

### PostgreSQL

```text
Host: localhost
Port: 5432
User: postgres
Password: postgres
```

### pgAdmin

Access from the browser:

```text
http://localhost:8080
```

Credentials:

```text
Email: admin@admin.com
Password: 12345
```

## Register the server in pgAdmin

When logging into pgAdmin for the first time:

1. Right-click on "Servers".
2. Select "Register → Server".

### General

```text
Name: FastAndSafeDW
```

### Connection

```text
Host name/address: postgres
Port: 5432
Maintenance database: postgres
Username: postgres
Password: postgres
```

Save the configuration.

## Create the database

Inside the PostgreSQL server, create the database:

```text
fast_and_safe_dw
```

---

# Running the Project

Run:

```bash
python main.py
```

The system will automatically perform:

* Extraction
* Transformation
* Dimension building
* Fact table building
* CSV generation
* Loading into PostgreSQL

---

# Generated Tables

## Dimensions

* Dim_Ciudad
* Dim_Cliente
* Dim_Sede
* Dim_Mensajero
* Dim_Tipo_Urgencia
* Dim_Servicio
* Dim_Tipo_Novedad
* Dim_Hora
* Dim_Fecha

## Facts

* Fact_Servicios
* Fact_Novedades

---

# Connecting from Power BI

Select:

```text
Get Data
↓
PostgreSQL Database
```

Parameters:

```text
Server: localhost
Port: 5432
Database: fast_and_safe_dw
User: postgres
Password: postgres
```

Import the dimensions and fact tables to build the analytical dashboards.

---

# Expected Result

At the end of execution:

* The CSV files are stored in `dw_data/`.
* The Data Warehouse tables are loaded into PostgreSQL.
* The database can be queried from pgAdmin and Power BI.
