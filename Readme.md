# Rishil Boddula

**I build and ship LLM products end to end** — retrieval pipelines, streaming APIs, and the boring infrastructure that keeps them running.

MSc Advanced Computer Science @ University of Hertfordshire (UK) · Previously ~1 year as a production software engineer building RAG pipelines and enterprise integrations · Open to UK graduate and internship roles in ML/AI engineering.

---

## Featured work

### 🔥 [Crucible](https://github.com/ris2002/Crucible) — a social platform where you have to earn the right to post
**[→ Try it live](https://idea-forge-beryl-phi.vercel.app)**

You can't publish an idea until you've worked it through an AI dialogue across 8 intellectual genres. The premise: friction improves ideas.

Built and deployed solo. React 18 + Vite on Vercel, FastAPI on Render, Supabase (Postgres + Auth + RLS), Stripe.

What's interesting in the code:
- **Provider-agnostic streaming router** — SSE token streaming over Anthropic, OpenAI, or Google, with per-session token accounting; the top tier is BYOK, so those sessions cost the platform nothing.
- **Safety that can't be prompt-injected** — a deterministic regex crisis check runs *before* any model call, returns region-specific helplines, and locks the session. No LLM in the decision path.
- **Cost control as a feature** — prompt caching, per-tier turn limits, input caps, and a configurable monthly spend ceiling with admin kill switches.

---

### 🧠 [Forge_Mind](https://github.com/ris2002/Forge_Mind) — a local-first AI workspace that never phones home
A modular desktop AI workspace where adding a capability is a folder plus a registry entry — the core stays untouched. Ships as a native app: Tauri v2 shell, FastAPI backend compiled with PyInstaller and run as a sidecar over loopback HTTP.

- Defaults to **Ollama**, so nothing leaves your machine. API keys and OAuth tokens are Fernet-encrypted at rest; CORS is locked to local origins.
- Modules only ever call `llm_generate` / `llm_stream` — Ollama, Claude, OpenAI, and Gemini are one file each behind a common interface.


---

### 🩺 [Diabetes_Prediction-MLE](https://github.com/ris2002/Diabetes_Prediction-MLE) — the full MLOps loop, not a notebook
Five baseline classifiers under heavy class imbalance, wrapped in the pipeline you'd actually need to run it again in six months: DVC for data versioning, Airflow for orchestration, MLflow for tracking, Docker Compose for the whole stack, Jenkins for CI.

---

### 📊 [Adult-Census-Income-MLE-NN](https://github.com/ris2002/Adult-Census-Income-MLE-NN) — neural nets vs. ensembles, honestly reported
Seven documented neural network experiments benchmarked against gradient-boosted ensembles. SMOTENC applied *after* the split, not before. Includes a corrected evaluation section where I caught and re-ran a metrics bug in my own results — the write-up shows the wrong numbers and the right ones.

---

## Learning MLOps, one tool at a time

Rather than copying a full stack from a template, I took a single training pipeline and added one piece of infrastructure per repo — so I understood what each layer was actually solving before adding the next. Read in order:

| # | Repo | What got added |
|---|---|---|
| 1 | [ci-cd-ml-training-pipeline-zenml](https://github.com/ris2002/ci-cd-ml-training-pipeline-zenml) | Pipeline structure and step orchestration with ZenML |
| 2 | [dockerized-ml-api-ci-cd](https://github.com/ris2002/dockerized-ml-api-ci-cd) | Containerised serving behind an API, plus a CI pipeline |
| 3 | [data-versioned-ml-pipeline-dvc](https://github.com/ris2002/data-versioned-ml-pipeline-dvc) | Data and model versioning with DVC — reproducible reruns |
| 4 | [airflow-kubernetes-ml-pipeline](https://github.com/ris2002/airflow-kubernetes-ml-pipeline) | Scheduled orchestration on Airflow, running on Kubernetes |
| 5 | [event-driven-ml-system-kafka](https://github.com/ris2002/event-driven-ml-system-kafka) | Event-driven inference with Kafka instead of request/response |

The models themselves are deliberately simple — the point of each repo is the infrastructure around it. [Diabetes_Prediction-MLE](https://github.com/ris2002/Diabetes_Prediction-MLE) above is where the whole stack comes together on one problem.

---

## Also worth a look
| Repo | What it is |
|---|---|
| [Loan-default-MLOPS](https://github.com/ris2002/Loan-default-MLOPS) | Loan-default prediction with a full training-to-serving pipeline |
| [Govt-Data-Looker-App-](https://github.com/ris2002/Govt-Data-Looker-App-) | Assistant over Indian government spending data (eGramSwaraj) |
| [AI-Agent-Project-1-simple-python-coding-agent](https://github.com/ris2002/AI-Agent-Project-1-simple-python-coding-agent) | A coding agent built from scratch to understand the tool-use loop |
| [FAQ-chatbot-with-Pinecone](https://github.com/ris2002/FAQ-chatbot-with-Pinecone) | Vector-search FAQ bot |

---

## Toolbox
**Languages** Python · TypeScript/JavaScript · SQL
**ML/AI** PyTorch · scikit-learn · LangChain · RAG · ChromaDB · Pinecone · Ollama · Anthropic / OpenAI / Gemini APIs
**Backend** FastAPI · REST · SSE streaming · OAuth 2.0 · Postgres · Supabase
**Infra** Docker · Airflow · MLflow · DVC · Jenkins · GitHub Actions · Vercel · Render · Tauri

---

## Background
- **MSc Advanced Computer Science**, University of Hertfordshire, UK — 2025 to 2027
- **Software Engineer**, Reva Solutions (Hyderabad) — Aug 2024 to Aug 2025. Built LangChain RAG pipelines over the SAM.GOV federal contracts API, and a ServiceNow ↔ OpenText enterprise integration (REST, OAuth 2.0).
- **BTech, Information Technology**, CBIT Hyderabad — 2020 to 2024

Ask me about any file in these repos.

---

📫 [LinkedIn](https://linkedin.com/in/rishilboddula) · rb25abl@herts.ac.uk · Based in the UK, with full right to work via the Graduate Route from 2027
