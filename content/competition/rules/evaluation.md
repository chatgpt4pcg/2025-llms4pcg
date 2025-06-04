---
title: Evaluation
type: docs
prev: competition/rules/submission
next: competition/prizes
weight: 3
math: true
---

{{< callout type="info" >}}
  The “**Similarity and Diversity Metrics**” section on this page was updated on May 19, 2025.  
  See details in our [Similarity and Diversity Metrics]({{< ref "#similarity">}}).
{{< /callout >}}

The submitted prompts will undergo an evaluation process that involves subjecting them to 10 trials for each of the 26 uppercase letters of the English alphabet (A-Z). The levels generated for each character will be evaluated based on their similarity, stability, and diversity, and scored using the criteria outlined in the scoring policy given below. The entire evaluation process will be conducted using [automated scripts and programs]({{< ref "/competition/resources">}}).

Please note that the evaluation process will be conducted twice, at midterm and final stages. The number of trials and characters in the evaluation set may be adjusted based on the number of teams.

## Evaluation Set

All 26 alphabetical uppercase characters.

<!-- A B C D E F G H I J K L M N O P Q R S T U V W X Y Z -->

$A \ B \ C \ D \ E \ F \ G \ H \ I \ J \ K \ L \ M \ N \ O \ P \ Q \ R \ S \ T \ U \ V \ W \ X \ Y \ Z$

## Scoring Policy

The following scoring process is applied for each prompt score per model. After calculating the prompt scores for all three models, the scores are summed before normalization for the final ranking.

In trial $i$ of target character $j$ for program $k$:

### Stability

The stability of a level is evaluated
using our [Science Birds Evaluator](https://github.com/chatgpt4pcg/modified-science-birds). Here, $total\\_blocks\_{ijk}$ is defined asthe number of blocks at the initialization step of loading the level into the evaluator. Then the program will calculate the value of $moving\\_blocks\_{ijk}$ which is defined as the number of moving blocks during the first 10 seconds after level initialization. Each level will receive an $sta\_{ijk}$ score according to the following equation. The score has a continuous value in $[0, 1]$.

$$ sta_{ijk} = \frac{total\\\_blocks_{ijk} - moving\\\_blocks_{ijk}}{total\\\_blocks_{ijk}} $$

### Similarity

The similarity score reflects the softmax probability $\sigma (\textbf{z}^0_{ijkL})_j$ of the model called [vit-base-uppercase-english-characters](https://huggingface.co/pittawat/vit-base-uppercase-english-characters), which is used to infer target character $j$ in trial $i$ from the image of the generated level after the first 10 seconds of initialization. Each level will receive a continuous value between $[0, 1]$. 

The class token embedding in the output of the [Vision Transformer](https://arxiv.org/pdf/2010.11929) encoder ($\textbf{z}^0_{ijkL}$) serves as the level image representation, and the softmax is computed over this embedding. This score, $sim\_{ijk}$, is given as

$$ sim_{ijk} = \sigma(\textbf{z}^0_{ijkL})_j $$

### Diversity

The diversity score represents how diverse the generated levels are under the same target character $j$ for program $k$. The score, $div_{jk}$, is calculated by computing cosine distance, $D_c$, of unordered pairs in the set $A$ containing pairs of output vectors from the class token embedding, $\textbf{v}\_{ijk} = \textbf{z}^0_{ijkL}$.
$\Xi\_{jk}$ denotes a set containing all such vectors across trials of the same target character $j$ from the same program $k$.

$$ div_{jk} = \frac{\sum_a^{|A_{jk}|} D_c(\textbf{v}_a^1, \textbf{v}_a^2)}{0.5T(T+1)-T}\text{,} $$

where

$$ A_{jk} = \{{(\textbf{v}_a^1, \textbf{v}_a^2) | (\textbf{v}_a^1, \textbf{v}_a^2) \in \Xi_{jk} \bowtie \Xi_{jk} \land v_a^1 \neq v_a^2 \}} $$

and $T$ represents the number of trials per target character.

### Weighting

Given that $P$ and $C$ represent the number of programs in the competition and the number of
characters, respectively, to give a higher weight to a more
difficult target character, $weight_{j}$ for
target character $j$ is defined as follows:

$$ weight_{j} = {w\_sta}_{j} \times {w\_sim}_{j} \times {w\_div}_{j}\text{,} $$

where

$$ {w\_sta}_{j} = max(1 - \frac{\sum_{k=1}^{P} \sum_{i=1}^{T} sta_{ijk}}{PT}, \frac{1}{C})\text{,} $$

$$ {w\_sim}_{j} = max(1 - \frac{\sum_{k=1}^{P} \sum_{i=1}^{T} sim_{ijk}}{PT}, \frac{1}{C})\text{,} $$

and

$$ {w\_div}_{j} = max(1 - \frac{\sum_{k=1}^{P} div_{jk}}{P}, \frac{1}{C}) $$

### Scoring

Next, the weighted $trial_{ijk}$ score is defined as follows:

$$ trial_{ijk} = weight_{j} \times sta_{ijk} \times sim_{ijk} $$

The average score for target character $j$ of program $k$, $char_{jk}$, is defined as follows:

$$ char_{jk} = \frac{div_{jk}\sum_{i=1}^{T} trial_{ijk}}{T} $$

The $prompt_{k}$ score is defined as follows:

$$prompt_{k} = \frac{\sum_{j=1}^{C} char_{jk}}{C}$$

### Final Scoring and Normalization

After calculating the $prompt_{k}$ score for each of the three models, sum these scores to get the total prompt score for program $k$:

$$ total\_prompt_{k} = \sum_{m=1}^{3} prompt_{k,m}$$

where $m$ represents each of the three models.

Next, the normalized $total\\\_prompt_{k}$ score, ${norm\\\_total\\\_prompt}_{k}$, is defined as follows:

$$$$

$$ {norm\_total\_prompt}_{k} = 100\ \frac{total\_prompt_{k}}{competition}, $$ 

where

$$ competition = \sum_{k=1}^P {total\_prompt}_{k} $$

Finally, ${norm\\\_total\\\_prompt}_{k}$ will be used for ranking.

## Ranking Policy

The team that has the highest ${norm\\\_total\\\_prompt}_{k}$ and overcomes our [zero-shot baseline](https://github.com/chatgpt4pcg/llms4pcg-pe-examples/tree/main/zero_shot) will be declared the winner. If there are multiple teams with the same highest score, the one with the shortest prompt will be chosen as the winner. However, if multiple teams still have the same score and the shortest prompt, they will be considered co-winners.

## Evaluation Tools

1. We will conduct the final evaluation on these 3 models using [Ollama](https://ollama.com/) interface:

   - **qwen 2.5** `32b`: [`32b-instruct-fp16`](https://ollama.com/library/qwen2.5:32b-instruct-fp16)
   - **phi 3** `14b`: [`14b-medium-128k-instruct-fp16`](https://ollama.com/library/phi3:14b-medium-128k-instruct-fp16)
   - **gemma 2** `27b`: [`27b-instruct-fp16`](https://ollama.com/library/gemma2:27b-instruct-fp16)

   While participants are free to explore other models during their research phase, our final assessment will be a comprehensive evaluation of submitted projects based on these three models.

2. [Science Birds Evaluator](https://github.com/chatgpt4pcg/modified-science-birds) with features to:

   - Automatically assess the stability.
   - Automatically export images using black-textured blocks on a white background for similarity testing.

3. [vit-base-uppercase-english-characters](https://huggingface.co/pittawat/vit-base-uppercase-english-characters).

4. Automation scripts available on our [Resources]({{< ref "/competition/resources">}}) page.

## Evaluation Environment for Response Generation Stage

Software:

- OS: macOS Sonoma Version 14.5
- Python: 3.11.xx
- Unity: 2019.4.40f1 - [Science Birds Evaluator](https://github.com/chatgpt4pcg/modified-science-birds)
- [Our automation scripts]({{< ref "/competition/resources">}})

Hardware:

- Chip: Apple M2 Ultra - RAM: 128 GB

## Evaluation Process

1. We manually inspect each submitted program for a potential violation of the rules. Qualified programs will be run to gather responses from the models to test the generalizable of prompt engineering
2. The [code extraction script](https://github.com/chatgpt4pcg/code-extraction-script) will load each response and produce a new file containing only a series of `drop_block()` commands.
3. The [text-to-xml conversion script](https://github.com/chatgpt4pcg/text-to-xml-converter-script) will load each code file and convert it into a Science Birds level description XML file.
4. Next, [Science Birds Evaluator](https://github.com/chatgpt4pcg/modified-science-birds) will individually load all levels to assess their stability and capture their images. The results of stability will be recorded, and for each level an image of the structure with black-textured blocks on a white background will be produced by the program.
5. The [similarity checking script](https://github.com/chatgpt4pcg/similarity-checking-script) will load each image and pass it through an open-source model called [vit-base-uppercase-english-characters](https://huggingface.co/pittawat/vit-base-uppercase-english-characters). It will then record the similarity result.
6. The [diversity checking script](https://github.com/chatgpt4pcg/diversity-checking-script) assesses the diversity of the levels by averaging the cosine distance of non-duplicated all-pairs of outputs from softmax for each level across trial of the same target character as described in the [Evaluation]({{< ref "/competition/rules/evaluation">}}).
7. The [scoring and ranking script](https://github.com/chatgpt4pcg/scoring-and-ranking-script) will load all stability, similarity, and diversity results for each team’s models. 
8. For each team, the scores from all three models are summed to obtain a total score. This total score is then normalized across all teams according to the scoring policy.  
9. Finally, the final ranking of all teams is determined based on these normalized total scores.  
