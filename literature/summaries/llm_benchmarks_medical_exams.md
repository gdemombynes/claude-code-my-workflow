# LLM Benchmarking on Medical Exams — Group Summary

**Papers in this group (all ⚠️ need full citation verification):**
- Goh et al. (2025) — large language models on medical qualification exams
- Arora et al. (2025) — LLM clinical benchmarks
- Nori et al. (2025) — GPT-4 / LLMs as medical assistants (likely Microsoft Research)
- Van Veen et al. (2024) — clinical text summarization and LLM benchmarks

**Type:** Benchmarking / capability evaluation (NOT causal evidence of real-world impact)
**Country/Region:** Primarily high-income settings; exams from US, UK, India
**Note:** These papers test LLM performance on written medical exams — they do NOT measure clinical outcomes

## Shared Research Question
Can LLMs pass medical licensing exams and clinical benchmarks at expert-level performance?

## Key Findings (general across this literature)
- GPT-4 and similar models pass USMLE (US medical licensing exam) at or above the passing threshold
- Performance is strong on structured knowledge questions; weaker on rare conditions and procedural judgment
- Some models tested on Indian and other national medical licensing exams show similar patterns
- Strong performance on exams ≠ strong performance in clinical care (confounding, context, physical exam not captured)

## Relevance to Paper
- Cited in Health section to establish that LLMs have reached medically relevant capability thresholds
- Important caveat: exam performance is a necessary but not sufficient condition for clinical deployment
- Key gap: almost no benchmarking on LMIC-specific diseases, drug formularies, or clinical contexts
- Exam benchmarks reflect training data distribution — likely overfit to high-income clinical scenarios

## Limitations / Caveats
- Benchmark contamination: LLMs may have seen exam questions in training data
- No randomized evidence of impact on actual patient outcomes
- LMIC disease burden (malaria, TB, neglected tropical diseases) poorly represented in standard benchmarks
- Physical examination, procedural skills, communication not captured by text benchmarks

## Section in paper
Health — AI capabilities / diagnostic benchmarks
