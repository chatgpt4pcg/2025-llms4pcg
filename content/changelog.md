---
title: Changelog
type: default
toc: false
---

## May 31, 2025

### Added

**Prize and Sponsor Information**  
- Added information about the total prize pool (1,000 USD), sponsor (IEEE CIS Education Competition Subcommittee), and prize distribution (1st: 500 USD, 2nd: 300 USD, 3rd: 200 USD).
- [Read more about this update]({{< ref "/competition/prizes">}}).

## May 19, 2025

### Changed

**Updated Similarity and Diversity Metrics Section**  
- Revised the explanation for the similarity metric to clarify that the class token embedding from the final layer of the Vision Transformer encoder is used as the level image representation.  
- Diversity metric now compares pairs of output vectors from the class token embedding.  
- [Read more about this update]({{< ref "/competition/rules/evaluation#similarity">}}).

**Improved Random Seed Handling**
- **Bug Fix in llms4pcg-python 2.0.0:** Resolved an issue in the previous dependency package where, under environments with full Ollama seed support, i.e., identical outputs were generated for every trial due to improper random seed implementation.
- **New Approach:** The seed is now treated as a **master seed**. For each trial, a unique seed is generated from this master seed, ensuring diverse outputs across trials.
- **Evaluation Change:** To prevent overfitting to a specific seed, the master seed value is now provided only for reference. During evaluation, a different randomly selected master seed will be used.
- For detailed information, please refer to the [release notes](https://github.com/chatgpt4pcg/llms4pcg-python/releases/tag/2.0.0).

**Updated packages**
- Competition package:
  - [llms4pcg-python](https://github.com/chatgpt4pcg/llms4pcg-python) updated to `2.0.0` (includes seed bug fix)
- Evaluation packages:
  - [Similarity checking script](https://github.com/chatgpt4pcg/similarity-checking-script) updated to `v0.2.0`
  - [Diversity checking script](https://github.com/chatgpt4pcg/diversity-checking-script) updated to `v0.2.0`

## April 9, 2025

### Added

- Submission form and deadline.

## January 4, 2025

### Added

- Examples of prompt engineering for LLMs4PCG competition utilizing our Python package, [llms4pcg-python](https://github.com/chatgpt4pcg/llms4pcg-python).
- Model selection: `qwen-2.5-32b`, `phi-3-14b`, and `gemma-2-27b`.

## December 5, 2024

### Added

- Competition outline for next year's event
- Basic site structure and navigation