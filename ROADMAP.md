# Roadmap

## Now (v1.x — current)
- [x] Multi-model sentiment ensemble with disagreement scoring
- [x] Emotion, aspect-based, sarcasm, and toxicity analysis
- [x] Topic modeling + trend forecasting
- [x] FastAPI backend with auth, caching, rate limiting
- [x] Dashboard, Docker Compose, Kubernetes manifests, CI/CD

## Next (v1.1 — observability & retrieval)
- [ ] Wire up `prometheus-fastapi-instrumentator` and ship a real Grafana
      dashboard JSON export
- [ ] RAG-powered chat assistant: embed analyzed text into ChromaDB
      (already configured), add `/chat` endpoint backed by an LLM API
- [ ] Alembic migrations to replace `create_all`-on-startup
- [ ] PDF report export (in addition to existing CSV export)

## Later (v1.2 — data ingestion)
- [ ] Live connectors: Twitter/X, Reddit, YouTube comments, RSS news
      (with mock-mode fallback when API keys are absent)
- [ ] Slack / Discord webhook integration for scheduled report delivery
- [ ] Email digest via SMTP (config already scaffolded in `.env.example`)

## Future (v2.0 — research-grade extensions)
- [ ] Swap TF-IDF/NMF topic modeling for BERTopic (embedding-based
      clustering using the configured sentence-transformer)
- [ ] Sentiment knowledge graph (entities: brands/people/products/events,
      relationship extraction, graph visualization)
- [ ] SHAP/LIME explainability dashboard for individual predictions
- [ ] Fine-tuned, in-house ABSA and fake-review-detection models (replacing
      the current heuristic/general-purpose approaches) tracked via MLflow
      experiment tracking + a model registry
- [ ] DVC-based dataset versioning for any fine-tuning pipelines
- [ ] Multi-language UI (dashboard currently English-only; backend already
      accepts a `language` field and the multilingual BERT model)

## Contributing to the Roadmap

Have an idea or want to pick up one of these? Open an issue describing
the use case before submitting a large PR, so we can align on approach.
See [`CONTRIBUTING.md`](CONTRIBUTING.md).
