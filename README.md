# Dumroo Admin Panel — Natural Language Query System (AI + RBAC)

This project demonstrates an AI-powered **natural language query system** with **role-based access control (RBAC)** for the Dumroo Admin Panel.  
It allows admins to ask simple English questions like:

- “Which students haven’t submitted their homework yet?”
- “Show me performance data for Grade 8 from last week”
- “List all upcoming quizzes scheduled for next week”

The system parses these queries (rule-based OR LLM-based), fetches the relevant data from a CSV, and ensures that admins only see data within their **assigned grade/class scope**.

---

# 🚀 Features

## 🔍 Natural Language Querying  
Supports admin questions related to:
- Homework submissions  
- Quiz performance  
- Upcoming quizzes  
- Time windows (“last week”, “next week”)  
- Grade-level filtering  
- Class filtering  

Admins can type plain English; the system converts it to structured filters.

---

## 🛡 Role-Based Access Control (RBAC)
Admins are restricted to their assigned:
- **Grade**  
- **Class**

Examples:
- Grade 8 admin cannot access Grade 9 data  
- Admin of Class 7A cannot view Class 7B  

All access restrictions are enforced **server-side** even if the LLM tries manipulating filters.

---

## 🤖 LLM-Powered Parsing (Optional)
With the OpenAI API + LangChain:
- The system converts English questions to **strict validated JSON**  
- JSON is checked for:
  - Intent  
  - Grade  
  - Class  
  - Time-window  
- Only allowed keys/types are accepted  
- Any “trick” (e.g., asking for Grade 9) is blocked by RBAC

This ensures **safe, injection-proof AI behavior**.

---

## 🧰 Dataset
Included file:
dumroo_students.csv

Contains fields:
- Student ID  
- Student Name  
- Grade  
- Class  
- Homework Submitted  
- Last Submission Date  
- Upcoming Quiz Name  
- Upcoming Quiz Date  
- Last Quiz Score  
- Last Quiz Date  

This dataset simulates real-life student activity monitoring.

---

## 🖥 Gradio User Interface

Features:
- Choose admin (Grade 8, 7A, Region, etc.)  
- Enter English questions  
- Optionally toggle **LLM Parser (OpenAI)**  
- View results as HTML table  
- View full audit log  

### Audit log includes:
- Timestamp  
- Admin username  
- Query text  
- Parsed filter (JSON)  
- Number of rows returned  

---

# 📁 Project Structure

/
├── dumroo_nl_query_system.ipynb # Main notebook (Colab-ready)
├── dumroo_students.csv # Dataset
├── requirements.txt # Dependencies
└── README.md # Project documentation

---

# ▶️ How To Run (Google Colab)

1. Open Google Colab
2. Upload the notebook:
3. Run all cells sequentially (**Cell 1 → Last Cell**)
4. When the Gradio UI loads:
- Select an admin (e.g., `admin_grade8`)
- Type a natural-language question
- Click **Run**
5. (Optional) Toggle **Use LLM parser**  
You will be prompted to enter your OpenAI API key securely.

---

# 📝 Example Queries (Works in both Rule-based & LLM modes)

### 🔹 Missing homework  
Which students haven't submitted their homework yet?


### 🔹 Performance  
List all upcoming quizzes scheduled for next week


### 🔹 Role restriction demo  
Logged in as `admin_grade8`:


Show me performance of Grade 9 students

→ Output:

---

# 🧪 Testing
A basic test cell is included inside the notebook to validate:

- `scope_filter()`
- `parse_time_window()`
- `enforce_admin_scope()`

For full testing in a local environment:

---

# 🌐 Technologies Used
- **Python**
- **Pandas**
- **Gradio**
- **LangChain**
- **OpenAI API**
- **Dateutil**
- **JSON validation**
- **RBAC logic**

---

# 🏁 Conclusion
This project satisfies all assignment requirements:

✔ Natural language querying  
✔ Structured data filtering  
✔ Role-based access enforcement  
✔ Optional LLM integration  
✔ Validation to prevent security breaches  
✔ Simple UI for demonstration  
✔ Ready for real-world extension (DB, API, dashboards)

Upload this repository to GitHub and submit the link.

---

# 📬 Contact
If you need clarification or improvements, feel free to reach out.
contact : dhanraj.t1616@gmail.com

