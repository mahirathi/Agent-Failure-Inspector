# Agent Failure Inspector

Find where an AI agent run went wrong—and the trace evidence that explains why.

Agent Failure Inspector (AFI) is an offline diagnostic tool for completed,
failed AI agent runs. It analyzes execution traces containing messages,
tool calls, and tool results to identify the failure step, classify the
error, and produce an evidence-backed explanation.

## Status

In development. This repository will track the baseline implementation,
retrieval experiments, fine-tuning, and evaluation results.

## Planned Features

- Upload and inspect execution traces through a local Streamlit interface.
- Identify the step where a run went wrong.
- Classify failures across 14 error categories.
- Explain diagnoses using validated references to trace steps.
- Compare four approaches: prompting, RAG, LoRA fine-tuning, and LoRA with RAG.

## Initial Scope

Version 1 focuses on static text traces from the smolagents subset of the
Who and When Pro dataset.

AFI analyzes uploaded traces without executing their code or tool instructions.
Automatic repair, live monitoring, and multi-agent attribution are outside
the initial scope.

## Approach

Trace JSON → Schema validation → Step normalization → Diagnostic model
→ Output and evidence validation → Diagnostic report

Optional retrieval supplies similar failure cases from the training split.

## Planned Technology Stack

- Python and Pydantic
- Streamlit
- sentence-transformers and FAISS
- Hugging Face Transformers
- PEFT and TRL for LoRA fine-tuning
- pytest

## Evaluation

The benchmark will measure:

- Exact failure-step localization
- Error-category macro F1
- Joint step-and-category correctness
- Invalid outputs and nonexistent evidence references
- Latency, token usage, and cost per diagnosis

Evaluation safeguards include separate model inputs and labels,
task-grouped splits, a training-only retrieval index, and a held-out test set.

Results will be published as experiments are completed, including findings
where retrieval or fine-tuning does not improve performance.

## Roadmap

1. Baseline diagnostic pipeline, CLI, and Streamlit demo
2. Retrieval-assisted diagnosis and matched baseline comparison
3. LoRA fine-tuning and four-mode benchmark
4. Results report, model card, and recorded demo

