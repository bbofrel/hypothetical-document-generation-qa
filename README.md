# Enhancing Open-Domain Question Answering with Hypothetical Document Generation

The paper is available at `report.pdf`.
This project explores whether synthetic document generation can improve open-domain question answering performance compared to traditional retrieval-based approaches.

Instead of retrieving external documents, I investigate a generate-then-read pipeline where a language model first generates a hypothetical document related to a question, and another model uses this document as additional context during answer generation.

## Research Question

Can generated documents serve as an effective alternative to retrieved context in open-domain question answering?

## Method

The system consists of two language models:

* **Mistral-7B-Instruct** for hypothetical document generation
* **Llama 3.2-3B** for question answering

For each question, Mistral generates a synthetic document that is then provided to Llama as additional context. Performance is compared against:

1. Baseline QA without external context
2. QA with generated documents
3. QA with Wikipedia passages

## Dataset

* TriviaQA validation set
* 1,000 evaluation samples

## Evaluation

Models were evaluated using:

* Exact Match (EM)
* BERTScore

Multiple prompting strategies were explored to investigate how strongly language models rely on provided context versus their internal knowledge.

## Key Findings

* Generated documents improved semantic answer quality as measured by BERTScore.
* Synthetic documents often outperformed Wikipedia passages in terms of semantic relevance.
* Exact Match scores did not improve consistently.
* Llama 3.2 showed strong over-reliance on supplied context, sometimes ignoring knowledge already stored in its parameters.
* Prompt design significantly influenced model behavior and context usage.

