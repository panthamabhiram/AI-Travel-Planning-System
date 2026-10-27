# ✈️ AI Travel Planner — Multi-Agent System

An autonomous, multi-agent travel planning platform built with **LangGraph**, **Groq (GPT-OSS 120B)**, **PostgreSQL Checkpointing**, **AviationStack**, **Tavily Search**, and an interactive **Streamlit** frontend.

---

## 🌟 Architecture & Workflow

The system utilizes a 4-agent sequential workflow orchestrated by **LangGraph**:

```mermaid
graph LR
    User([User Query]) --> Flight[✈️ Flight Agent]
    Flight --> Hotel[🏨 Hotel Agent]
    Hotel --> Itinerary[🗓️ Itinerary Agent]
    Itinerary --> Final[🧠 Final Synthesis Agent]
    Final --> Memory[(🐘 PostgreSQL Memory Checkpoint)]
    Final --> Output([Complete Travel Plan])
```

1. **✈️ Flight Agent**: Queries real-time flight details and airlines using the AviationStack API and Tavily search.
2. **🏨 Hotel Agent**: Discovers accommodations, prices, amenities, and locations tailored to the user's budget.
3. **🗓️ Itinerary Agent**: Crafts day-by-day sightseeing, attractions, and activity schedules.
4. **🧠 Final Synthesis Agent**: Consolidates flights, stays, daily itineraries, estimated budgets, and travel tips into a complete markdown travel plan.
5. **🐘 PostgreSQL Checkpointing**: Preserves conversational thread memory across interactions using `PostgresSaver`.

---

## 🚀 Setup & Installation

### 1. Prerequisites
- Python 3.10+
- PostgreSQL database running locally or in the cloud

### 2. Clone Repository
```bash
git clone <your-repo-url>
cd "Multi AI agent planner"
```

### 3. Create & Activate Virtual Environment
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
```

### 4. Install Dependencies
```bash
pip install -r requirements.txt
```

### 5. Configure Environment Variables
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```
Fill in your API keys in `.env`:
```env
AVIATIONSTACK_API_KEY=your_aviationstack_key
GROQ_API_KEY=your_groq_key
TAVILY_API_KEY=your_tavily_key
DATABASE_URL=postgresql://username:password@localhost:5432/langgraph_memory
```

---

## 🖥️ Running the Application

Launch the Streamlit web application:
```bash
streamlit run frontend.py
```

The app will start at `http://localhost:8501`.

---

## 📁 Project Structure

```
├── .env.example              # Environment variables template
├── .gitignore                # Git ignore rules (protects .env & .venv)
├── requirements.txt          # Python dependencies
├── README.md                 # Project documentation
├── main.py                   # LangGraph graph definition and multi-agent workflow
├── frontend.py               # Streamlit web UI and agent stream runner
├── assets/                   # Static UI assets and backgrounds
└── tools/
    ├── flight_tool.py        # AviationStack flight search tool
    └── tavily_tool.py        # Tavily web search tool
```

---

## 👤 Author
- **Abhiram Pantham**
