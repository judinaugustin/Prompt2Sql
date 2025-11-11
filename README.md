# 🧠 Prompt2SQL

**Prompt2SQL** is an AI-powered web app that converts **natural language questions into SQL queries** — and executes them live against a real SQLite database.  
Built with **Flask**, **Groq’s LLaMA-3.1 LLM**, and a **dynamic schema visualization interface**, it bridges the gap between human reasoning and database querying.

---

## 🚀 Features

✅ **Natural Language → SQL**  
Type queries in plain English (e.g., *“Show total revenue by region”*) and get executable SQL instantly.

✅ **Live Database Execution**  
Run queries directly against a real `SQLite` database and view results in a formatted HTML table.

✅ **Interactive Schema Viewer**  
Browse tables and columns in collapsible sections — dynamically fetched from your database.

✅ **Query History Panel**  
View your previous questions and their generated SQL, neatly organized and expandable.

✅ **Built with Groq LLM (LLaMA-3.1)**  
Fast and cost-efficient SQL generation powered by Groq’s blazing inference engine.

✅ **Zero Hard-Coding of Schema**  
Schema data is read dynamically using `PRAGMA` commands — changes in your DB reflect instantly.

---

## 🏗️ Architecture Overview

User → Flask Web UI → Groq LLM API → SQL Generation → SQLite Execution → HTML Table Output


**Core Components**
| Component | Description |
|------------|-------------|
| `Flask` | Web server and frontend template renderer |
| `Groq LLaMA-3.1` | Natural language → SQL generator |
| `SQLite` | In-memory database for live execution |
| `PyNgrok` | Generates public URL for testing |
| `Pandas` | Query execution and HTML table rendering |

---

## 📚 Example Queries

| User Query | Generated SQL |
|-------------|---------------|
| *Show total sales by region* | `SELECT o.region, SUM(o.quantity * p.price) AS total_sales FROM orders o JOIN products p ON o.product_id = p.product_id GROUP BY o.region;` |
| *List all customers who bought electronics* | `SELECT DISTINCT c.name FROM customers c JOIN orders o ON c.customer_id = o.customer_id JOIN products p ON o.product_id = p.product_id WHERE p.category = 'Electronics';` |
| *Find top 3 products by revenue* | `SELECT p.name, SUM(o.quantity * p.price) AS total_revenue FROM orders o JOIN products p ON o.product_id = p.product_id GROUP BY p.name ORDER BY total_revenue DESC LIMIT 3;` |

---

## 🧩 Tech Stack

| Layer | Technology |
|--------|-------------|
| Frontend | HTML5, CSS3 (with responsive styling) |
| Backend | Flask (Python 3.10+) |
| Database | SQLite |
| AI/LLM | Groq LLaMA-3.1-8B-Instant |
| Deployment | PyNgrok (temporary public URL) |

---
🧠 How It Works

1.User enters a natural language question.
2.The app builds a context-aware prompt with database schema details.
3.Groq’s LLaMA-3 model generates SQL code.
4.Flask executes it on the SQLite DB using pandas.read_sql().
5.Results and the generated SQL are displayed in the browser.

+---------------------------------------+
| 🧠 Prompt2SQL                         |
+---------------------------------------+
| 📚 Schema Viewer (collapsible)        |
| 🧩 Generated SQL Query                |
| 📊 Query Results (HTML Table)         |
| 🕘 Previous Queries (expandable)      |
+---------------------------------------+

🤝 Contributing
Pull requests are welcome!
If you’d like to extend Prompt2SQL with:

Vector-based schema retrieval (for large DBs)
Multi-database connectors (PostgreSQL/MySQL)
Fine-tuned NL→SQL models

please open an issue or submit a PR.

💬 Prompt2SQL bridges human thought and structured data — turning natural questions into powerful insights.
