---
title: Changelog
type: default
toc: false
---

## August 29, 2025

### Added

- We have released the [result of the competition]({{< ref "/result">}}).

## June 9, 2025

### Changed

**Evaluation Environment Updates**
- Updated supported operating systems to macOS Sequoia `15.2`.
- Updated supported Python versions to explicitly require Python >= `3.11`, < `3.14`.
- Upgraded new hardware configuration: Mac Studio M2 Ultra with 192 GB memory.

**llms4pcg-python Package Update**
- Upgraded `llms4pcg-python` from version `2.0.0` to `2.0.1`.
- Removed the explicit response timeout parameter from the OpenAI client, allowing model responses to proceed without a fixed timeout constraint.
- Increased the maximum trial time limit (`max_time`) from 120 seconds to 500 seconds, enabling longer trials and more complex interactions.
- For detailed information, please refer to the [release notes](https://github.com/chatgpt4pcg/llms4pcg-python/releases/tag/2.0.1).

## June 4, 2025

### Added

**Random Seed Requirement for Reproducibility**  
- Added a rule requiring all participant code that uses random number generation (e.g., `random` in Python) to set a fixed seed in the code (e.g., `random.seed(42)`) for reproducibility.  
- [Read more about this update]({{< ref "/competition/rules/prompt#prompt-rules">}}).  

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
- **Evaluation Change:** To prevent overfitting to a specific seed, the seed is now omitted during regular use, allowing for random responses. For the final evaluation, a selected master seed will be used to ensure reproducibility.
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
- Model selection: `qwen-2.5-32b`, `gemma-2-27b`, and `phi-3-14b`.

## December 5, 2024

### Added

- Competition outline for next year's event
- Basic site structure and navigation
