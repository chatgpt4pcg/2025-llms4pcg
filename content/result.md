---
title: Result
type: default
toc: false
---

{{< callout emoji="🎉" >}}
**Congratulations to the competition winners!**  
🥇 **1st Place** - **"HFLN"**  
🥈 **2nd Place** - **"Z2A"**  
🥉 **3rd Place** - **"FNRX"**   
{{< /callout >}}

{{% details title="Evaluation Leaderboard" %}}

| Rank | Team Name                              | Total Prompt Score | Normalized Score |
|:----:|----------------------------------------|--------------------:|-----------------:|
|  1   | HFLN                                   | 0.0977              | 44.96            |
|  2   | Z2A                                    | 0.0345              | 15.88            |
|  3   | FNRX                                   | 0.0221              | 10.19            |
|  4   | ChatZero                               | 0.0161              | 7.42             |
|  5   | CARRASCO_VELO_Pablo                    | 0.0154              | 7.11             |
|  6   | MY_Team                                | 0.0121              | 5.57             |
|  7   | jaidh                                  | 0.0088              | 4.04             |
|  -   | <span style="color:#f44336">*Strong Baseline (Zero-Shot Multi-turn)*</span> | 0.0084 | 3.87 |
|  -   | <span style="color:#1ABF12">*Weak Baseline (Zero-Shot)*</span> | 0.0021 | 0.96 |
| Dis  | MyAwesomeTeam                          | -                   | -                |

> **Dis** means disqualified.  
> **MyAwesomeTeam** is disqualified due to not using our provided package, `llms4pcg.chat_with_llm`, for interacting with the model.

{{% /details %}}

{{% details title="Model-Specific Team Rankings" closed="true" %}}

| Rank | Team Name                           | Model   | Prompt Score | Normalized Prompt Score |
|:----:|:------------------------------------|:-------:|------------:|----------------------:|
| 1    | HFLN                                | gemma 2 | 0.0387      | 17.80                 |
| 2    | HFLN                                | qwen 2.5| 0.0386      | 17.76                 |
| 3    | HFLN                                | phi 3   | 0.0204      | 9.40                  |
| 4    | Z2A                                 | phi 3   | 0.0168      | 7.74                  |
| 5    | FNRX                                | qwen 2.5| 0.0141      | 6.47                  |
| 6    | Z2A                                 | qwen 2.5| 0.0095      | 4.39                  |
| 7    | Z2A                                 | gemma 2 | 0.0081      | 3.75                  |
| 8    | CARRASCO_VELO_Pablo                 | qwen 2.5| 0.0079      | 3.62                  |
| 9    | ChatZero                            | qwen 2.5| 0.0077      | 3.56                  |
| 10   | ChatZero                            | gemma 2 | 0.0057      | 2.62                  |
| 11   | FNRX                                | gemma 2 | 0.0056      | 2.56                  |
| 12   | CARRASCO_VELO_Pablo                 | gemma 2 | 0.0054      | 2.50                  |
| 13   | MY_Team                             | gemma 2 | 0.0052      | 2.39                  |
| 14   | MY_Team                             | qwen 2.5| 0.0052      | 2.38                  |
| 15   | <span style="color:#f44336">*Zero-Shot Multi-turn*</span>  | qwen 2.5| 0.0051      | 2.36                  |
| 16   | jaidh                               | gemma 2 | 0.0050      | 2.29                  |
| 17   | jaidh                               | qwen 2.5| 0.0038      | 1.74                  |
| 18   | <span style="color:#f44336">*Zero-Shot Multi-turn*</span> | gemma 2 | 0.0029      | 1.35                  |
| 19   | ChatZero                            | phi 3   | 0.0027      | 1.24                  |
| 20   | FNRX                                | phi 3   | 0.0025      | 1.16                  |
| 21   | CARRASCO_VELO_Pablo                 | phi 3   | 0.0021      | 0.98                  |
| 22   | MY_Team                             | phi 3   | 0.0017      | 0.80                  |
| 23   | <span style="color:#1ABF12">*Zero-Shot*</span> | gemma 2 | 0.0010      | 0.45                  |
| 24   | <span style="color:#1ABF12">*Zero-Shot*</span> | qwen 2.5| 0.0009      | 0.43                  |
| 25   | <span style="color:#f44336">*Zero-Shot Multi-turn*</span> | phi 3   | 0.0003      | 0.16                  |
| 26   | <span style="color:#1ABF12">*Zero-Shot*</span> | phi 3   | 0.0002      | 0.08                  |
| 27   | jaidh                               | phi 3   | 0.0000      | 0.00                  |

{{% /details %}}

{{% details title="Evaluation Configuration" closed="true" %}}

**Parameters used during final evaluation:**
- Competition package: [`llms4pcg-python`](https://github.com/chatgpt4pcg/llms4pcg-python) version `2.0.1`
- Starting seed for LLM interaction (Ollama): 6280
- Random seed for programming package: 42

{{% /details %}}

{{% details title="Download Competition Data" closed="true" %}}

Competition related data can be downloaded from the following link (August 29, 2025): [OSF Storage](https://osf.io/xr8qe/files/osfstorage?view_only=971d0fecbae0465ab98faa20be810980)

{{< filetree/container >}}
  {{< filetree/folder name="result - The final evaluation outputs" state="closed">}}
    {{< filetree/file name="character_scores.csv" >}}
    {{< filetree/file name="constants.json - Weights and constant values." >}}
    {{< filetree/file name="final_team_rankings.csv" >}}
    {{< filetree/file name="prompt_scores_ranks.csv" >}}
    {{< filetree/file name="trial_scores.csv" >}}
  {{< /filetree/folder >}}

  {{< filetree/folder name="submissions - Each team’s submitted code." state="closed">}}
    {{< filetree/folder name="baselines" >}}
        {{< filetree/file name="zero_shot_multi_turn.zip" >}}
        {{< filetree/file name="zero_shot.zip" >}}
    {{< /filetree/folder >}}
    {{< filetree/file name="CARRASCO_VELO_PABLO.zip" >}}
    {{< filetree/file name="ChatZero.zip" >}}
    {{< filetree/file name="FNRX.zip" >}}
    {{< filetree/file name="HFLN.zip" >}}
    {{< filetree/file name="jaidh.zip" >}}
    {{< filetree/file name="MyAwesomeTeam.zip" >}}
    {{< filetree/file name="MY_Team.zip" >}}
    {{< filetree/file name="Z2A.zip" >}}
  {{< /filetree/folder >}}
  {{< filetree/file name="competition.zip - Generated data from the evaluation process." >}}
{{< /filetree/container >}}

{{% /details %}}
