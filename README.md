# 🛍️ Quantifai Assignment: E-Commerce ETL Pipelines + AI Reconciliation

## 🧠 Project Overview

This repository contains an end-to-end data engineering solution built as part of a Quantifai assignment. It covers:

- V1: A static ETL pipeline loading data from local e-commerce CSV and JSON files into SQLite, with a Streamlit dashboard.
- V2: A dynamic ETL pipeline triggered by simulated external API (via Postman) and real-time transformation and loading, with interactive querying via Gradio chat and SQLite MCP server.
- Bonus Task: AI-powered customer data reconciliation using fuzzy matching, Gemini AI schema inference, and rule-based matching logic.

---

## 📂 Project Structure

quantifai-assignment/  
├── ai_reconciliation_bonus/         # Bonus AI reconciliation logic  
│   ├── corrected_mapping.py  
│   ├── gemini_mapper.py  
│   ├── fuzzy_mapping.py  
│   └── ...  
├── v1_static_pipeline/              # Static ETL pipeline using local data  
│   ├── app.py                       # Streamlit dashboard  
│   ├── etl/                         # Extract-Transform-Load modules  
│   ├── datasets/  
│   └── v1_ecommerce.db  
├── v2_dynamic_pipeline/             # Dynamic pipeline triggered by API  
│   ├── app.py                       # Gradio interface  
│   ├── etl/  
│   ├── db-chat-llm/  
│   └── v2_ecommerce.db  
├── data_discovery_analysis.ipynb    # Exploratory data analysis  
├── requirements.txt  
└── README.md  



---

## 🧱 Architecture Overview

### 🔹 V1: Static Pipeline

- ✅ Extract: Load CSV/JSON from local files
- 🛠️ Transform: ETL functions (cleansing, merging, normalization)
- 🧬 Load: Save output into SQLite database
- 📊 Visualize: Business KPIs via Streamlit

### 🔸 V2: Dynamic Pipeline

- 🚀 Trigger: External POST API (simulated via Postman)
- ⚙️ Pipeline: Extract → Transform → Load (automated per POST)
- 🗃️ DB: SQLite for storage
- 💬 Query: Chat with DB using Gradio interface (MCP server)

---

## 🤖 AI Reconciliation Task

- 📥 Input: New customer dataset
- 🔍 Step 1: Fuzzy match columns with orders_cleaned
- 🤖 Step 2: Use Gemini AI to suggest column mappings
- 🧩 Step 3: Final rule-based reconciliation logic
- 🧾 Output: reconciled_joined.csv

📍 Details in: ai_reconciliation_bonus/bonus-task-description.ipynb

---

## 🖼️ Visuals

### 🔷 Static Streamlit UI (V1)
![Streamlit UI](./assets/streamlit_ui.png)

### 🔷 Postman API Call (V2)
![Streamlit UI](./assets/postman.png)

### 🔶 Dynamic Chat UI with Gradio (V2)
![Gradio UI](./assets/gradio_chatdb.png)

### 🗂️ SQLite View
![SQLite View](./assets/sqlite_db.png)

---

## ⚙️ Setup Instructions

1. 🧬 Clone Repository

```bash
git clone https://github.com/yourusername/quantifai-assignment.git
cd quantifai-assignment
```

2. 📦 Create Python Environment
```bash
conda create -n quantifai-etl python=3.11
conda activate quantifai-etl
pip install -r requirements.txt
```

3. ▶️ Run V1 Static Pipeline
``` bash
cd v1_static_pipeline
streamlit run app.py
```

4. ▶️ Run V2 Dynamic Pipeline
``` bash
cd v2_dynamic_pipeline
uvicorn servers-archived.db_chat_llm_server:app --reload
python app.py
```
5. 🧪 Trigger Dynamic Flow via Postman
``` bash
POST http://127.0.0.1:5000/new_order
```
Attach your simulated files in the body.

## 🛠️ Tech Stack & Tools

| Tech         | Description                  |
|--------------|------------------------------|
| 🐍 Python     | Core language                |
| 🐼 Pandas     | Data manipulation            |
| 📊 Matplotlib | Visualizations               |
| 📈 Streamlit  | Dashboard (V1 UI)            |
| 💬 Gradio     | Chat interface (V2)          |
| 💾 SQLite     | Lightweight DB               |
| 🔍 FuzzyWuzzy | String matching logic        |
| 🤖 Gemini AI  | Schema & name matching       |
| 📬 Postman    | API testing                  |

---

## 🧩 Challenges & Solutions

| Challenge                       | Solution                                |
|--------------------------------|-----------------------------------------|
| Schema mismatches in raw data  | Custom coercion + schema normalization  |
| Realtime ETL on POST trigger   | FastAPI + internal orchestration        |
| Fuzzy matching accuracy        | Weighted similarity + Gemini fallback   |
| Insight querying from DB       | sqlite-chat + Gradio chat wrapper       |

---

## 🚀 Future Improvements

- Add test coverage for ETL modules  
- Add schema validation layer before DB load  
- Enhance NLP query handling with LangChain  

---

## 👩‍💻 Author

**Sarvesh Bajare**  
Third-year Instrumentation Engineering  
Interests: Gen AI, data science, deep learning
