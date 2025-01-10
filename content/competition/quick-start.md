---
title: Quick Start
type: docs
prev: /
next: competition/rules/
weight: 1
---

## Easily run LLMs locally

{{< tabs items="Ollama (CLI), LM Studio (GUI)">}}

   {{< tab >}}
   1. Download Ollama from [Ollama](https://ollama.com).
   2. Download large language models:  
      To ensure fairness to the full，these **open-source models** are recommended to be used:

         - **qwen 2.5** `32b`: [`32b-instruct-fp16`](https://ollama.com/library/qwen2.5:32b-instruct-fp16)
         - **phi 3** `14b`: [`14b-medium-128k-instruct-fp16`](https://ollama.com/library/phi3:14b-medium-128k-instruct-fp16)
         - **gemma 2** `27b`: [`27b-instruct-fp16`](https://ollama.com/library/gemma2:27b-instruct-fp16)

         _If your computer can't afford these models, you are welcome to use a quantized version or other open-source models._

   3. We provide a few example programs implemented using various prompt engineering techniques. These examples are offered to assist you in getting started with the competition. You can utilize these examples as a foundation to develop your own advanced prompt engineering techniques. The examples are accessible in a GitHub repository, which you can find [here](https://github.com/chatgpt4pcg/llms4pcg-pe-examples).
   {{< /tab >}}

  {{< tab >}}
  1. Download LM Studio from [LM Studio](https://lmstudio.ai/).
  2. Download large language models from the "Search" page:  
   To ensure fairness to the full，these **open-source models** are recommended to be used:

      - **qwen2.5-32B**: `Q8_0` [bartowski/Qwen2.5-32B-Instruct-GGUF](https://model.lmstudio.ai/download/bartowski/Qwen2.5-32B-Instruct-GGUF)
      - **phi-3-medium**: `Q8_0` [ssmits/Phi-3-medium-128k-instruct-Q8_0-GGUF](https://model.lmstudio.ai/download/ssmits/Phi-3-medium-128k-instruct-Q8_0-GGUF)
      - **gemma2-27B**: `Q8_0` [lmstudio-community/gemma-2-27b-it-GGUF](https://huggingface.co/lmstudio-community/gemma-2-27b-it-GGUF)

      _If your computer can't afford these models, you are welcome to use a quantized version or other open-source models._

   3. Once the model is downloaded, navigate to the "Local Server" tab, select the model, and click "Start Server".  
   Please view more details on [Prompt Engineering for Science Birds Level Generation and Beyond](https://chatgpt4pcg.github.io/tutorial)
   4. You can start the tutorial code from [this github repository](https://github.com/chatgpt4pcg/tutorial-2024-notebook)
   5. We provide a few example programs implemented using various prompt engineering techniques. These examples are offered to assist you in getting started with the competition. You can utilize these examples as a foundation to develop your own advanced prompt engineering techniques. The examples are accessible in a GitHub repository, which you can find [here](https://github.com/chatgpt4pcg/llms4pcg-pe-examples).
  {{< /tab >}}

{{< /tabs >}}
