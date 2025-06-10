# An-AI-Agent-That-Builds-a-Model-from-Scratch
Autonomous agent that plans, writes, explains, and runs data science workflows (e.g., churn prediction) using LangGraph and LLMs.

```
An-AI-Agent-That-Builds-a-Model-from-Scratch/
├── README.md
├── requirements.txt
├── .env.template
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── data/
│   ├── churn_data.csv            # Mock dataset
│   └── schema.md                 # Markdown schema summary or description
│
├── notebooks/
│   └── eda_exploration.ipynb     # Optional manual EDA for testing
│   ├── research.ipynb            # Testing 
├── langgraph_app/                # Core orchestration layer
│   ├── __init__.py
│   ├── graph.py                  # LangGraph DAG setup
│   ├── config.py
│   └── state.py                  # Shared state structure
│
├── tools/                        # Modular tools for agent tasks
│   ├── schema_reader.py          # Reads and interprets dataset schema
│   ├── planner.py                # Breaks goal into subtasks
│   ├── eda_generator.py          # Generates code to explore data
│   ├── model_selector.py         # Chooses model type
│   ├── model_trainer.py          # Produces training code
│   └── evaluator.py              # Generates evaluation logic
│
├── sandbox/
│   └── executor.py               # (Optional) mock/safe execution of code
│
├── ui/
│   └── app.py                    # Streamlit or CLI interface
│
├── tests/
│   ├── test_planner.py
│   ├── test_schema_reader.py
│   └── test_model_trainer.py
│
└── docs/
    ├── architecture.md           # High-level architecture explanation
    └── task_templates.md         # Task decomposition examples
```

---

##  Goal
Given a user input like "predict churn from this dataset," the system:
1. Reads dataset schema
2. Plans modeling steps (EDA, preprocessing, training, evaluation)
3. Generates code for each step
4. (Optional) Runs the code in a sandbox
5. Outputs code and commentary

---

##  Architecture

- **LangGraph**: Orchestration of task flow
- **LangChain**: Tool routing and code generation
- **Python REPL Tool (optional)**: Execution sandbox

### Agent Workflow
```
[User Goal] --> [Planner] --> [Tool Router] --> [Code Generator] --> [Evaluator]
```

### Modules
- `schema_reader`: Understands structure of the dataset
- `planner`: Converts goal into step-by-step plan
- `eda_generator`: Generates code to explore the data
- `model_selector`: Picks model type (e.g., logistic regression)
- `model_trainer`: Creates training code
- `evaluator`: Outputs evaluation metrics and visuals

---

## Example Prompt
> "Build a churn prediction model using this CSV file."

##  Usage

# Clone and install
pip install -r requirements.txt or we can use uv

---

##  Tech Stack
- Python, LangGraph, LangChain
- OpenAI API or Anthropic
- Streamlit (optional UI)
- pytest for testing


---

##  Team Collaboration
- Each module lives in `tools/` — assigned to one dev
- Main DAG lives in `langgraph_app/`
- CI via GitHub Actions 
- PR-based dev flow with review gates on `main`

