# Data Science in Python: Cheat Sheet
## Data Sources, Data Types & Data Formats

---

## 📊 COMMON DATA SOURCES

### 1. **Files**
- Local files (CSV, Excel, JSON, XML, text files)
- Cloud storage (AWS S3, Google Cloud Storage, Azure Blob)
- Shared drives and network storage

### 2. **Databases**
- **Relational Databases**: PostgreSQL, MySQL, SQLite, Oracle
- **NoSQL Databases**: MongoDB, Cassandra, Redis
- **Data Warehouses**: Snowflake, BigQuery, Redshift

### 3. **APIs (Application Programming Interfaces)**
- REST APIs (JSON/XML responses)
- GraphQL APIs
- Public APIs: Twitter, GitHub, OpenWeather, etc.
- Internal company APIs

### 4. **Web Scraping**
- HTML pages (using BeautifulSoup, Scrapy)
- Dynamic websites (using Selenium)
- Note: Always check `robots.txt` and terms of service

### 5. **Streaming Data**
- Apache Kafka
- Real-time sensors and IoT devices
- Social media streams
- Financial market feeds

### 6. **Public Datasets**
- Kaggle, UCI ML Repository
- Government data (data.gov, census data)
- Research repositories
- Google Dataset Search

### 7. **Generated/Synthetic Data**
- Simulations
- Test data creation
- Faker library for mock data

---

## 🏗️ DATA TYPES

### 1. **Structured Data**
- Organized in rows and columns
- Predefined schema
- Easy to search and analyze
- **Examples**: SQL databases, spreadsheets, CSV files

### 2. **Semi-Structured Data**
- Has some organizational properties
- Doesn't fit rigid table structure
- Self-describing with metadata
- **Examples**: JSON, XML, HTML, log files

### 3. **Unstructured Data**
- No predefined structure
- Most difficult to process and analyze
- **Examples**: Text documents, images, videos, audio, social media posts, PDFs

### 4. **Time-Series Data**
- Data points indexed by time
- **Examples**: Stock prices, sensor readings, weather data

### 5. **Geospatial Data**
- Contains location information
- **Examples**: GPS coordinates, maps, satellite imagery

---

## 💾 DATA FORMATS

### File Formats

| Format | Type | Use Case | Python Library |
|--------|------|----------|----------------|
| **CSV** | Structured | Tabular data, simple datasets | `pandas`, `csv` |
| **JSON** | Semi-structured | APIs, web data, nested data | `json`, `pandas` |
| **XML** | Semi-structured | Legacy systems, configuration | `xml`, `lxml` |
| **Excel** | Structured | Business data, reports | `pandas`, `openpyxl` |
| **Parquet** | Structured | Big data, columnar storage | `pandas`, `pyarrow` |
| **HDF5** | Structured | Large numerical datasets | `h5py`, `pandas` |
| **Pickle** | Any | Python object serialization | `pickle` |
| **Feather** | Structured | Fast I/O between Python/R | `pandas`, `pyarrow` |
| **Avro** | Semi-structured | Hadoop, data serialization | `fastavro` |
| **ORC** | Structured | Big data, Hive | `pyarrow` |

### Text Formats

| Format | Description | Python Library |
|--------|-------------|----------------|
| **TXT** | Plain text | Built-in `open()` |
| **Markdown** | Formatted text | `markdown` |
| **Log Files** | Application logs | `logging`, regex |

### Database Formats

| Type | Examples | Python Library |
|------|----------|----------------|
| **SQL** | PostgreSQL, MySQL, SQLite | `sqlite3`, `sqlalchemy`, `psycopg2` |
| **NoSQL** | MongoDB, Redis | `pymongo`, `redis-py` |

### Image/Media Formats

| Format | Type | Python Library |
|--------|------|----------------|
| **JPEG/PNG** | Images | `PIL/Pillow`, `opencv` |
| **MP3/WAV** | Audio | `librosa`, `pydub` |
| **MP4/AVI** | Video | `opencv`, `moviepy` |

### Binary Formats

| Format | Description | Python Library |
|--------|-------------|----------------|
| **NumPy Arrays** | `.npy`, `.npz` | `numpy` |
| **Protocol Buffers** | Efficient serialization | `protobuf` |

---

## 🐍 PYTHON QUICK REFERENCE

### Reading Common Formats

```python
import pandas as pd
import json

# CSV
df = pd.read_csv('file.csv')

# Excel
df = pd.read_excel('file.xlsx', sheet_name='Sheet1')

# JSON
df = pd.read_json('file.json')
# or for custom parsing:
with open('file.json', 'r') as f:
    data = json.load(f)

# Parquet
df = pd.read_parquet('file.parquet')

# SQL
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql_query("SELECT * FROM table", conn)

# HDF5
df = pd.read_hdf('file.h5', key='data')

# Pickle
df = pd.read_pickle('file.pkl')
```

### Writing Common Formats

```python
# CSV
df.to_csv('output.csv', index=False)

# Excel
df.to_excel('output.xlsx', index=False, sheet_name='Data')

# JSON
df.to_json('output.json', orient='records', indent=2)

# Parquet
df.to_parquet('output.parquet')

# SQL
df.to_sql('table_name', conn, if_exists='replace', index=False)

# HDF5
df.to_hdf('output.h5', key='data', mode='w')

# Pickle
df.to_pickle('output.pkl')
```

---

## 💡 CHOOSING THE RIGHT FORMAT

### CSV
✅ Simple tabular data  
✅ Human-readable  
✅ Widely supported  
❌ No data types preserved  
❌ Large file size  

### JSON
✅ Nested/hierarchical data  
✅ Web APIs  
✅ Human-readable  
❌ Larger than binary formats  

### Parquet
✅ Big data analytics  
✅ Columnar storage (fast queries)  
✅ Good compression  
✅ Preserves data types  
❌ Not human-readable  

### Excel
✅ Business users  
✅ Multiple sheets  
✅ Formatting preserved  
❌ Size limitations  
❌ Slower than CSV  

### Pickle
✅ Python objects  
✅ Fast  
❌ Python-specific  
❌ Security risks  
❌ Version compatibility issues  

### HDF5
✅ Very large datasets  
✅ Fast I/O  
✅ Partial reading  
❌ Complex  

---

## 🎯 BEST PRACTICES

1. **Choose formats based on use case**
   - Development: CSV, JSON (readable)
   - Production: Parquet, HDF5 (efficient)
   - Sharing: CSV, Excel (compatible)

2. **Consider file size**
   - Use compression (gzip, zip)
   - Use efficient formats (Parquet vs CSV)

3. **Preserve data types**
   - Parquet, HDF5, Pickle preserve types
   - CSV requires specification

4. **Document your data**
   - Include README files
   - Data dictionaries
   - Metadata

5. **Version control for data**
   - DVC (Data Version Control)
   - Git LFS for large files

6. **Security considerations**
   - Never pickle untrusted data
   - Encrypt sensitive data
   - Use secure connections for APIs

---

## 📚 ADDITIONAL RESOURCES

- **Pandas Documentation**: https://pandas.pydata.org/docs/
- **Python Data Science Handbook**: Free online book
- **Real Python**: Tutorials on data formats
- **Kaggle Learn**: Free courses on data handling

---

