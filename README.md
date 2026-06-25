# AI Interviewer

A multi-agent interview simulation platform that delivers realistic, role-specific interview experiences powered by AI. Practice your responses, receive real-time coaching, and walk into your next interview with confidence.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Supported Roles](#supported-roles)
- [Dependencies](#dependencies)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [License](#license)

---

## Overview

AI Interviewer uses a three-agent pipeline — an Interviewer, a Candidate (you), and a Career Coach — to simulate professional job interviews end-to-end. Each session is tailored to a specific job role and evaluates technical depth, communication clarity, problem-solving ability, and cultural fit. After every answer, the Career Coach provides actionable feedback; at the end of the session, you receive a comprehensive performance summary.

---

## Features

- **Role-specific questioning** — Interview questions adapt to the target job position
- **Real-time feedback** — The Career Coach analyses each response immediately after it is given
- **Structured evaluation** — Covers technical skills, behavioral fit, communication, and problem-solving
- **End-of-session summary** — Consolidated performance review with improvement recommendations and interview readiness score
- **Extensible design** — Easily plug in new roles, models, or agent behaviours

---

## Architecture

The system is built around three collaborating agents:

```
┌──────────────────────────────────────────┐
│             Interview Session            │
│                                          │
│  ┌─────────────┐      ┌───────────────┐  │
│  │ Interviewer │─────▶│   Candidate   │  │
│  │    Agent    │      │     (User)    │  │
│  └─────────────┘      └──────┬────────┘  │
│                              │           │
│                              ▼           │
│                    ┌─────────────────┐   │
│                    │  Career Coach   │   │
│                    │     Agent       │   │
│                    └─────────────────┘   │
└──────────────────────────────────────────┘
```

| Agent | Responsibility |
|---|---|
| **Interviewer** | Conducts the interview; asks targeted, role-specific questions |
| **Candidate** | The human participant; answers questions through the CLI |
| **Career Coach** | Evaluates responses in real time; provides structured feedback and career guidance |

---

## Prerequisites

- Python 3.8 or higher
- An OpenAI API key
- Internet connection

---

## Installation

**1. Clone the repository**

```bash
git clone <repository-url>
cd AI_INTERVIEWER
```

**2. Install dependencies**

```bash
pip install -r requirements.txt
```

**3. Configure environment variables**

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

---

## Configuration

### Changing the Target Role

Open `main.py` and update the `job_position` variable:

```python
job_position = "Data Scientist"   # default
```

Any of the [supported roles](#supported-roles) can be substituted here.

### Changing the Model

The default model is `gpt-4o-mini`. To use a different OpenAI model, update the client initialisation in `AI_interview.py`:

```python
model_client = OpenAIChatCompletionClient(
    model="gpt-4o",               # replace with any supported model
    api_key=os.getenv("OPENAI_API_KEY"),
    timeout=20
)
```

---

## Usage

### Running the Interview

```bash
python main.py
```

### Using as a Python Module

```python
from AI_interview import team_Config, interview
import asyncio

async def run():
    job_position = "Product Manager"
    team = await team_Config(job_position)

    async for message in interview(team):
        print(message)

asyncio.run(run())
```

### Interview Flow

1. Agents are initialised for the selected role
2. The Interviewer asks a question
3. The Candidate types their response
4. The Career Coach delivers immediate feedback
5. Steps 2–4 repeat for the duration of the session
6. A final performance summary is generated

### Example Session

```
Interviewer:  Tell me about a challenging technical problem you solved recently.

Candidate:    I built a RAG-based chatbot that significantly improved our internal
              document search accuracy.

Career Coach: Strong example — the technology choice is relevant and clearly explained.
              To make this answer more impactful, consider quantifying the outcome:
              for instance, how much did search accuracy improve, or how did it
              affect team productivity? Measurable results leave a lasting impression
              on interviewers.
```

---

## Project Structure

```
AI-INTERVIEWER/
├── AI_interview.py      # Agent definitions and interview workflow
├── main.py              # Application entry point
├── requirements.txt     # Python dependencies
├── .env                 # Environment variables (not committed to version control)
└── README.md            # Project documentation
```

---

## Supported Roles

| Domain | Roles |
|---|---|
| Engineering | Software Engineer, DevOps Engineer |
| Data & AI | Data Scientist, AI Engineer, Machine Learning Engineer |
| Product & Business | Product Manager, Business Analyst |

To add a new role, update the `job_position` string in `main.py`. The agents adapt their questions and evaluation criteria accordingly.

---

## Dependencies

| Package | Purpose |
|---|---|
| `autogen-agentchat` | Multi-agent conversation framework |
| `autogen-core` | Core agent abstractions |
| `autogen-ext` | Extensions for AutoGen |
| `openai` | OpenAI API client |
| `python-dotenv` | Environment variable management |
| `tiktoken` | Token counting |
| `pydantic` | Data validation |

Install all dependencies:

```bash
pip install -r requirements.txt
```

---

## Troubleshooting

**`AuthenticationError` or API key errors**
Confirm that your `.env` file exists in the project root and contains a valid key:
```env
OPENAI_API_KEY=sk-...
```

**`ModuleNotFoundError`**
Reinstall all dependencies:
```bash
pip install -r requirements.txt
```

**Slow or hanging responses**
The default request timeout is 20 seconds. If you are on a slow connection or using a larger model, increase the `timeout` value in `AI_interview.py`.

---

## Roadmap

- [ ] Resume-based question generation
- [ ] Voice interview support
- [ ] Multi-language interviews
- [ ] Quantitative scoring system
- [ ] Analytics dashboard
- [ ] PDF performance reports
- [ ] Interview history and progress tracking
- [ ] ATS (Applicant Tracking System) integration

---

## License

This project is released under the [MIT License](LICENSE).

---

*Practice deliberately. Improve consistently. Succeed confidently.*