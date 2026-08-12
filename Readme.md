# Rishil Boddula

**I build and ship LLM products end to end**: retrieval pipelines, streaming APIs, and the boring infrastructure that keeps them running.

MSc Advanced Computer Science @ University of Hertfordshire (UK) · Previously ~1 year as a production software engineer building RAG pipelines and enterprise integrations · Open to UK graduate and internship roles in ML/AI engineering.

---

## Featured work

### 🔥 [Crucible](https://github.com/ris2002/Crucible): a social platform where you have to earn the right to post
**[→ Try it live](https://idea-forge-beryl-phi.vercel.app)**

You can't publish an idea until you've worked it through an AI dialogue across 8 intellectual genres. The premise: friction improves ideas.

Built and deployed solo. React 18 + Vite on Vercel, FastAPI on Render, Supabase (Postgres + Auth + RLS), Stripe.

What's interesting in the code:
- **Provider-agnostic streaming router.** SSE token streaming over Anthropic, OpenAI, or Google, with per-session token accounting; the top tier is BYOK, so those sessions cost the platform nothing.
- **Safety that can't be prompt-injected.** A deterministic regex crisis check runs *before* any model call, returns region-specific helplines, and locks the session. No LLM in the decision path.
- **Cost control as a feature.** Prompt caching, per-tier turn limits, input caps, and a configurable monthly spend ceiling with admin kill switches.

---

### 🧠 [Forge_Mind](https://github.com/ris2002/Forge_Mind): a local-first AI workspace that never phones home
A modular desktop AI workspace where adding a capability is a folder plus a registry entry, leaving the core untouched. Ships as a native app: Tauri v2 shell, FastAPI backend compiled with PyInstaller and run as a sidecar over loopback HTTP.

- Defaults to **Ollama**, so nothing leaves your machine. API keys and OAuth tokens are Fernet-encrypted at rest; CORS is locked to local origins.
- Modules only ever call `llm_generate` / `llm_stream`. Ollama, Claude, OpenAI, and Gemini are one file each behind a common interface.
- Untrusted content is tagged and isolated before it reaches downstream inference, and the test suite verifies that inference stays local-only with no telemetry leaving the machine.

---

## Implemented from scratch

Before reaching for a framework, I build the thing once by hand. These are the results, reported as they came out.

### 🔬 [Multi30k English to German: RNN vs LSTM](https://github.com/ris2002/Multik30-Eng-De-RNN_LSTM_Comparision)
Encoder-decoder baselines compared on Multi30k. Best of two runs: **BLEU 0.05 for the RNN against 0.02 for the LSTM**, with further runs limited by Colab compute.

The interesting part is why the LSTM lost. Its higher parameter count (3M against 2.8M) needs more epochs to converge on a dataset this size, which is a training budget problem rather than architectural inferiority. Two runs is too few to generalise from, and the write-up says so. I kept the LSTM for the next iteration on the reasoning that its gating structure should advantage long-range dependencies once it has the epochs to use them. Next: attention-based LSTM with longer training, targeting BLEU in the 25 to 30 range.

### ✏️ [Neural_Network_Scratch](https://github.com/ris2002/Neural_Network_Scratch)
A fully connected network built by hand: dense layers, ReLU, Softmax, categorical cross-entropy, and backpropagation derived from first principles.

### 🔁 [RNN_Scratch_Using_numpy_Pytorch](https://github.com/ris2002/RNN_Scratch_Using_numpy_Pytorch)
RNN forward pass, hidden-state update, and BPTT written from scratch in NumPy, then validated against PyTorch to confirm gradient correctness and reproduce vanishing-gradient dynamics.

---

### 🩺 [Diabetes_Prediction-MLE](https://github.com/ris2002/Diabetes_Prediction-MLE): the full MLOps loop, not a notebook
Five baseline classifiers under heavy class imbalance, wrapped in the pipeline you'd actually need to run it again in six months: DVC for data versioning, Airflow for orchestration, MLflow for tracking, Docker Compose for the whole stack, Jenkins for CI.

---

### 📊 [Adult-Census-Income-MLE-NN](https://github.com/ris2002/Adult-Census-Income-MLE-NN): neural nets vs. ensembles, honestly reported
Seven documented neural network experiments benchmarked against gradient-boosted ensembles. SMOTENC applied *after* the split, not before. Includes a corrected evaluation section where I caught and re-ran a metrics bug in my own results. The write-up shows the wrong numbers and the right ones.

---

## Learning MLOps, one tool at a time

Rather than copying a full stack from a template, I took a single training pipeline and added one piece of infrastructure per repo, so I understood what each layer was actually solving before adding the next. Read in order:

| # | Repo | What got added |
|---|---|---|
| 1 | [ci-cd-ml-training-pipeline-zenml](https://github.com/ris2002/ci-cd-ml-training-pipeline-zenml) | Pipeline structure and step orchestration with ZenML |
| 2 | [dockerized-ml-api-ci-cd](https://github.com/ris2002/dockerized-ml-api-ci-cd) | Containerised serving behind an API, plus a CI pipeline |
| 3 | [data-versioned-ml-pipeline-dvc](https://github.com/ris2002/data-versioned-ml-pipeline-dvc) | Data and model versioning with DVC, for reproducible reruns |
| 4 | [airflow-kubernetes-ml-pipeline](https://github.com/ris2002/airflow-kubernetes-ml-pipeline) | Scheduled orchestration on Airflow, running on Kubernetes |
| 5 | [event-driven-ml-system-kafka](https://github.com/ris2002/event-driven-ml-system-kafka) | Event-driven inference with Kafka instead of request/response |

The models themselves are deliberately simple. The point of each repo is the infrastructure around it. [Diabetes_Prediction-MLE](https://github.com/ris2002/Diabetes_Prediction-MLE) above is where the whole stack comes together on one problem.

---

## Also worth a look
| Repo | What it is |
|---|---|
| [Vector_Voyages_Project-](https://github.com/ris2002/Vector_Voyages_Project-) | Research-paper RAG chatbot with a dual ingestion path: pdfplumber for digital PDFs, a vision-model fallback for figure-heavy pages, file-hash caching to prevent reprocessing |
| [Mail-Mind-App](https://github.com/ris2002/Mail-Mind-App) | Gmail triage on the History API, roughly 60-second new-message latency at near-zero cost on quiet inboxes |
| [Loan-default-MLOPS](https://github.com/ris2002/Loan-default-MLOPS) | Loan-default prediction with a full training-to-serving pipeline, Blue-Green and Canary rollouts |
| [Govt-Data-Looker-App-](https://github.com/ris2002/Govt-Data-Looker-App-) | Assistant over Indian government spending data (eGramSwaraj) |
| [AI-Agent-Project-1-simple-python-coding-agent](https://github.com/ris2002/AI-Agent-Project-1-simple-python-coding-agent) | A coding agent built from scratch to understand the tool-use loop |

---

## Toolbox
**Languages** Python · TypeScript/JavaScript · SQL
**ML/AI** PyTorch · NumPy · scikit-learn · XGBoost · LangChain · RAG · ChromaDB · Pinecone · Ollama · Anthropic / OpenAI / Gemini APIs
**Backend** FastAPI · REST · SSE streaming · OAuth 2.0 · Postgres · Supabase
**Infra** Docker · Kubernetes · Airflow · MLflow · DVC · Jenkins · GitHub Actions · Vercel · Render · Tauri

---

## Background
- **MSc Advanced Computer Science**, University of Hertfordshire, UK. 2025 to 2027.
- **Software Engineer**, Reva Solutions (Hyderabad). Aug 2024 to Aug 2025. Built LangChain RAG pipelines over the SAM.GOV federal contracts API, and a ServiceNow to OpenText enterprise integration (REST, OAuth 2.0).
- **BTech, Information Technology**, CBIT Hyderabad. 2020 to 2024.

Ask me about any file in these repos.

---

📫 [LinkedIn](https://linkedin.com/in/rishilboddula) · rb25abl@herts.ac.uk · Based in the UK, with full right to work via the Graduate Route from 2027
