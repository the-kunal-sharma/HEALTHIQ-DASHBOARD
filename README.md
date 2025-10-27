# ⚕️ HealthIQ Dashboard

An AI-powered hospital assistant application that provides intelligent health-related insights using FastAPI, PostgreSQL with vector embeddings, and Maverick LLM.

![HealthIQ Dashboard](image.png)

## 🚀 Features

- **AI-Powered Queries**: Ask health-related questions and get instant AI-powered responses
- **Semantic Search**: Vector-based search through consultation notes using PGVector
- **Patient Management**: Store and manage patient records, lab reports, and consultation notes
- **Modern Web Interface**: Clean and intuitive dashboard for interacting with the AI assistant
- **RESTful API**: Well-structured FastAPI endpoints for all functionalities

## 🛠️ Tech Stack

- **Backend Framework**: FastAPI
- **Database**: PostgreSQL with PGVector extension
- **ORM**: SQLAlchemy
- **AI/LLM**: Maverick LLM API
- **Frontend**: HTML, CSS, JavaScript
- **Vector Embeddings**: PGVector for semantic search
- **Template Engine**: Jinja2

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Python 3.8+
- PostgreSQL 12+ with PGVector extension
- pip (Python package manager)

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/health.git
   cd health
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies**
   ```bash
   cd backend
   pip install -r requirements.txt
   ```

5. **Set up PostgreSQL with PGVector**
   ```sql
   CREATE EXTENSION IF NOT EXISTS vector;
   ```

6. **Create a `.env` file** in the `backend` directory:
   ```env
   DATABASE_URL=postgresql://username:password@localhost:5432/health_db
   MAVERICK_API_KEY=your_maverick_api_key_here
   MAVERICK_API_URL=https://api.maverick.com/v1
   ```

## 🚀 Running the Application

1. **Initialize the database** (run once to create tables):
   ```bash
   python -c "from backend.database import init_db; init_db()"
   ```

2. **Start the FastAPI server**:
   ```bash
   uvicorn backend.main:app --reload
   ```

3. **Access the application**:
   - Web Dashboard: http://localhost:8000
   - API Documentation: http://localhost:8000/docs
   - Alternative API Docs: http://localhost:8000/redoc

## 📁 Project Structure

```
health/
├── backend/
│   ├── main.py                 # FastAPI application entry point
│   ├── database.py            # Database connection and session management
│   ├── models.py              # SQLAlchemy models (Patient, LabReport, etc.)
│   ├── schemas.py             # Pydantic schemas for request/response validation
│   ├── requirements.txt       # Python dependencies
│   ├── routes/
│   │   ├── ai.py             # AI-related endpoints
│   │   ├── health.py         # Health check endpoint
│   │   └── query.py          # Query handling endpoints
│   ├── services/
│   │   ├── ai_agent.py       # AI agent service logic
│   │   ├── db_service.py     # Database service functions
│   │   ├── llm_service.py    # LLM API integration
│   │   └── vector_service.py # Vector search operations
│   ├── utils/
│   │   ├── embeddings.py     # Embedding generation utilities
│   │   └── prompt_templates.py # AI prompt templates
│   ├── static/
│   │   ├── style.css         # Frontend styles
│   │   └── script.js         # Frontend JavaScript
│   ├── templates/
│   │   └── index.html        # Main dashboard template
│   └── vectorstore.py        # Vector store configuration
└── README.md
```

## 🔌 API Endpoints

### Health Check
- `GET /health/` - Check if the backend and database are operational

### AI Endpoints
- `POST /ai/` - Send a query directly to the LLM (no database search)
  ```json
  {
    "query_text": "What are the symptoms of diabetes?"
  }
  ```

### Query Endpoints
- `POST /query/` - Handle user query with AI agent and semantic search
  ```json
  {
    "query_text": "Show me recent patient consultations"
  }
  ```

## 🗄️ Database Schema

The application uses the following main tables:

- **patients**: Patient demographic information
- **lab_reports**: Laboratory test results linked to patients
- **consultation_notes**: Doctor consultation notes with vector embeddings
- **query_logs**: Log of user queries and AI responses

## 🔐 Environment Variables

Create a `.env` file in the `backend` directory with the following variables:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
MAVERICK_API_KEY=your_api_key
MAVERICK_API_URL=https://api.maverick.com/v1
```

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 👤 Author

Your Name - [GitHub Profile](https://github.com/yourusername)

---

Made with ❤️ for better healthcare management

