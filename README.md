# Yusuf Çiçek

**Machine Learning Engineer — Recommender Systems & LLM** · Baykar Technologies

I build personalization and retrieval systems that serve real traffic: recommendation
pipelines, hybrid retrieval over vector and graph stores, and LLM-based ranking — with the
MLOps around them to keep it running. ~4 years across recommender systems, GenAI, and
computer vision.

[![Email](https://img.shields.io/badge/Email-yusufcicekk%40proton.me-8B89CC?style=flat-square&logo=protonmail&logoColor=white)](mailto:yusufcicekk@proton.me)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-yusufcicekk-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yusufcicekk)

---

## What I work on

**Personalization, Search & Recommendation** — Architected NSosyal's "For You" feed: a
modular, event-driven pipeline (Go, Python/gRPC, Kafka) covering candidate generation,
retrieval, ranking, re-ranking and diversification.

- Hybrid 3-slot retrieval — collaborative signals (favourite / in-network authors,
  social-proof boosting via Neo4j graph queries) alongside dense retrieval through Qdrant
  ANN search over multimodal post embeddings.
- Personalized learning-to-rank scorer — a weighted Alpha/Beta/Gamma model blending an 8B
  multimodal LLM re-ranker, Wilson-score engagement decay and novelty signals, with weights
  tuned online by Thompson Sampling multi-armed bandits.
- Multimodal embeddings from an 8B vision-language model over text, image and video posts;
  HDBSCAN clustering for topic discovery and MMR-based diversification that adapts to
  real-time engagement.
- Real-time user/context fusion — EMA offline profiling plus time-decayed online signal,
  PCA dimensionality reduction, and an on-demand Redis-cached feed-materialization layer
  for low-latency serving.

**LLM systems & developer tooling** — a token-aware Smart Memory Strategy that prioritizes
security-critical insights inside a bounded context window, and a Dependency Impact
Tracking system that performs Ripple Effect Analysis to catch indirect regressions in code
outside the immediate git diff.

**Platform** — a Go-based RBAC reverse proxy for LakeFS with GitLab OAuth, for
authentication and granular access management.

---

## Featured projects

### [Enterprise AI Code Review Agent](https://github.com/yusfcicek/code-reviewer) · Python

An open-source AI code review agent for CI/CD pipelines. It triages a merge request before
spending tokens on it, runs static analyzers over the changed files, routes each file to a
committee of specialist agents, and turns the result into a deterministic pipeline verdict.

- **Smart triage** — classifies each changed file (SKIP / AUTO_APPROVE / CRITICAL /
  QUICK_SCAN / FULL_REVIEW) so LLM spend goes where it matters.
- **Analysis beyond the diff** — AST-based semantic change classification, two-level
  dependency ripple tracing, SAST mapped to CWE and OWASP Top 10, plus complexity, SOLID
  and N+1 checks.
- **A committee, not a prompt** — architecture, security, performance and dependency agents,
  each with its own prompt, a narrowed tool catalogue and a weighted share of the file's
  token budget. Security gets the largest share, because "spend more on security than on
  style" should be something the system holds rather than something it hopes for.
- **Hybrid retrieval, fully offline** — the checkout is chunked by syntax tree and indexed
  twice, over BM25 and over embeddings, then fused by reciprocal rank and reduced by
  maximal marginal relevance. No embedding service, no network call.
- **The diff is hostile input** — declared trust boundaries, path confinement, a credential
  deny-list, a per-review read budget and output redaction. A refused access becomes a
  CRITICAL finding, so an injection attempt fails the pipeline instead of being mentioned
  in the report.
- **Deterministic gate** — the PASS/WARN/FAIL verdict comes from static analysis, not model
  output, so an unreachable LLM cannot turn a failing review into a passing one. A false
  positive is suppressible one line or one file at a time, with a recorded reason and a
  count in the report — never with a blanket off-switch.
- **Built to hold up** — 25k lines in a hexagonal architecture with layering enforced by an
  import test, 2631 tests at 94 % coverage, and lint, types, a dependency audit and
  measured precision / recall / F1 floors all gating CI. The GitLab pipeline runs the agent
  on the project's own merge requests.

### [CVAT Remote Inference Server](https://github.com/yusfcicek/cvat-remote-inference-server) · Python

A FastAPI orchestrator that runs annotation models on dedicated remote GPU hosts and wires
them into CVAT through auto-generated Nuclio functions.

- Detectors, trackers and interactors behind one interface; multiple instances of the same
  model with different weights.
- New model implementations are auto-detected, registered, assigned a port and given
  generated Nuclio deployment files — zero-config scaling.
- Lazy initialization and idle-model unloading to keep GPU memory honest.

### [Autonomous Curriculum Generator](https://github.com/yusfcicek/autonomous-curriculum-generator) · Python

A LangGraph multi-agent system that generates CEFR-aligned language curricula as
strictly-typed JSON, grounded by a RAG pipeline over Qdrant. Give it a language and a CEFR
level; get back deduplicated, Pydantic-validated vocabulary and grammar.

### [MaskFreeVIS — optical-flow data fusion](https://github.com/yusfcicek/MaskFreeVIS) · Python

A fork of [SysCV/MaskFreeVIS](https://github.com/SysCV/MaskFreeVIS) (CVPR 2023) adding an
early-fusion path that feeds Farnebäck dense optical flow into the backbone alongside the
raw frame, so motion reaches the video instance segmentation model at train and inference
time. Registry-driven and config-gated on detectron2, so the block is swappable and turns
off cleanly.

---

## Toolbox

**Recommenders & retrieval** — Recommendation Systems · Collaborative & Content-Based
Filtering · Hybrid Recommenders · Learning-to-Rank · Multi-Armed Bandits (Thompson
Sampling) · Dense/Sparse/Hybrid Retrieval · Semantic & Vector Search (Qdrant, HNSW, ANN) ·
Re-Ranking & Diversification (MMR) · Feature Stores (Redis)

**LLM, GenAI & multimodal** — Multimodal Embeddings (Qwen3-VL) · Vision-Language Models ·
Agentic AI · RAG · LangChain · Hugging Face · Model Serving (OpenAI, vLLM)

**AI/ML & computer vision** — Machine Learning · Deep Learning · Computer Vision · PyTorch ·
TensorFlow · Object Detection & Segmentation · OpenCV · Scikit-Learn · Transformers

**Deployment & systems** — MLOps · CI/CD · Event-Driven Architecture (Kafka) · gRPC ·
TensorRT · K8s · Docker · GCP · AWS · Vertex AI · Azure · Redis · Qdrant · Neo4j · REST API

**Languages** — Go · Python · C++ · SQL · PostgreSQL · Git · OOP · Design Patterns

---

## Background

**Baykar Technologies** — Artificial Intelligence Software Engineer · Sep 2022 – present

**Segion Analytics** — Founding Machine Learning Engineer · Oct 2020 – Oct 2021

Built the API for an AI-powered autonomous expert system (four deep learning models,
FastAPI), deployed on AWS with Nginx and Docker, and shipped end-to-end license plate
detection and recognition that cut Character Error Rate 47 % and Word Error Rate 12 %
against OCR baselines.

**B.Sc. Computer Engineering**, Beykent University — GPA 3.55/4.00

Turkish (native) · English (B2)
