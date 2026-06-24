# Changelog

All notable changes to this project will be documented in this file.
Format loosely follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.0.0] - 2026-06-20

### Added
- Multi-model sentiment ensemble (DistilBERT-SST2, Twitter-RoBERTa,
  FinBERT, multilingual BERT) with confidence-weighted voting and
  entropy-based disagreement scoring.
- 7-class emotion classification service.
- Aspect-based sentiment analysis (clause splitting + spaCy noun-chunk
  extraction + per-clause scoring).
- Sarcasm/irony detection service.
- Toxicity detection service with sub-category scores.
- Topic modeling via TF-IDF + NMF over analysis history.
- Time-series trend bucketing and ARIMA/linear-trend forecasting.
- FastAPI backend: JWT auth (access + refresh tokens), RBAC role field,
  rate limiting, Redis caching, PostgreSQL persistence via SQLAlchemy.
- Model leaderboard endpoint (real agreement-rate computed from history).
- CSV export and deterministic executive summary report endpoints.
- Dark, glassmorphic single-page dashboard (no build step) with live
  charts and a model-consensus "constellation" visualization.
- Docker Compose stack (Postgres, Redis, backend, frontend, optional
  MLflow/Prometheus/Grafana profile).
- Kubernetes manifests (namespace, configmap/secrets, backend with HPA,
  frontend with ingress, Postgres StatefulSet, Redis).
- GitHub Actions CI (lint + test) and Docker image build/push workflows.
- Pytest suite covering auth flows and (network-gated) sentiment endpoints.
- Full documentation set: architecture (with Mermaid diagrams), API
  reference, deployment guide, dataset catalog, portfolio assets.

### Known Limitations
- Prometheus metrics export, RAG chat assistant, knowledge graph,
  BERTopic, and live social-media connectors are scaffolded but not fully
  wired — see `ROADMAP.md`.

## [Unreleased]

See `ROADMAP.md` for planned work.
