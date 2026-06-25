````markdown
# 🎙️ AI Interviewer


AI Interviewer creates realistic interview experiences using multiple AI agents that collaborate to conduct interviews, evaluate responses, and provide personalized career guidance.

---

## 🚀 Features

### 🤖 Multi-Agent Interview System

The application consists of three specialized agents:

- **Interviewer Agent**
  - Conducts professional interviews.
  - Asks targeted and role-specific questions.

- **Candidate (User)**
  - Answers interview questions.

- **Career Coach Agent**
  - Provides feedback and improvement suggestions.
  - Offers career guidance.

---

### 🎯 Role-Based Interviews

Customize interviews for any job position:

- Software Engineer
- Data Scientist
- AI Engineer
- Product Manager
- DevOps Engineer
- Business Analyst
- Machine Learning Engineer

---

### 📋 Structured Interview Process

The interview evaluates:

- Technical skills
- Problem-solving ability
- Professional experience
- Communication skills
- Behavioral and cultural fit

---

### 💬 Real-Time Feedback

After every response, the Career Coach provides:

- Strengths
- Areas of improvement
- Communication advice
- Interview tips

---

### 📈 Performance Summary

At the end of the interview:

- Overall evaluation
- Improvement recommendations
- Career suggestions
- Interview readiness assessment

---

# 🏗️ Architecture

```text
┌──────────────────┐
│   Interviewer    │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│    Candidate     │
│      User        │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│  Career Coach    │
└──────────────────┘
````

---

# 📂 Project Structure

```text
AI-INTERVIEWER/
│
├── AI_interview.py      # Agent definitions and interview workflow
├── main.py              # Application entry point
├── requirements.txt     # Project dependencies
├── .env                 # Environment variables
└── README.md            # Documentation
```

---

# ⚙️ Prerequisites

Before running the project, make sure you have:

* Python 3.8+
* OpenAI API Key
* Internet connection

---

# 🛠️ Installation

## 1. Clone the Repository

```bash
git clone <repository-url>
cd AI_INTERVIEWER
```

## 2. Install Dependencies

```bash
pip install -r requirements.txt
```

## 3. Configure Environment Variables

Create a `.env` file in the root directory.

```env
OPENAI_API_KEY=your_openai_api_key
```

---

# ▶️ Running the Application

Start the interview simulation:

```bash
python main.py
```

---

# 🎯 Customize the Job Position

Modify the job position in `main.py`.

```python
job_position = "Data Scientist"
```

Examples:

```python
job_position = "AI Engineer"
job_position = "Product Manager"
job_position = "Machine Learning Engineer"
```

---

# 💻 Using as a Python Module

```python
from AI_interview import team_Config, interview
import asyncio

async def custom_interview():

    job_position = "Product Manager"

    team = await team_Config(job_position)

    async for message in interview(team):
        print(message)

asyncio.run(custom_interview())
```

---

# 🔄 Interview Workflow

1. Initialize AI agents.
2. Configure the job position.
3. Interviewer asks a question.
4. Candidate provides an answer.
5. Career Coach gives feedback.
6. The process repeats.
7. Final evaluation is generated.

---

# ⚙️ Model Configuration

The default model is:

```python
model_client = OpenAIChatCompletionClient(
    model="gpt-4o-mini",
    api_key=os.getenv("OPENAI_API_KEY"),
    timeout=20
)
```

You can change it to any supported OpenAI model.

---

# 📝 Example Interview

### Interviewer

> Tell me about a challenging problem you solved recently.

### Candidate

> I built a RAG-based chatbot that improved document search accuracy.

### Career Coach

> Excellent example. Try including measurable business impact such as reduced response time or improved customer satisfaction.

---

# 📦 Dependencies

* autogen-agentchat
* autogen-core
* autogen-ext
* openai
* python-dotenv
* tiktoken
* pydantic

Install all dependencies:

```bash
pip install -r requirements.txt
```

---

# 🚨 Troubleshooting

### API Key Errors

Verify that your `.env` file contains a valid API key.

### Module Import Errors

Reinstall dependencies:

```bash
pip install -r requirements.txt
```

---

# 🔮 Future Enhancements

* Resume-based interview generation
* Voice interviews
* Multi-language support
* Interview scoring system
* Analytics dashboard
* PDF reports
* Interview history
* ATS integration

---

# 📄 License

This project is open source and available under the MIT License.

---

# ⭐ Support

If you find this project useful, consider giving it a star on GitHub.

---

## 🎤 Practice. Improve. Succeed.

Prepare smarter, gain confidence, and ace your next interview with AI Interviewer.

```
```
