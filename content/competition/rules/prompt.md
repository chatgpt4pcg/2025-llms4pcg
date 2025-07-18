---
title: Prompt
type: docs
prev: competition/rules/
next: competition/rules/submission/
weight: 1
---

## Prompt Engineering Examples

We provide a few example programs implemented using various prompt engineering techniques. These examples are offered to assist you in getting started with the competition. You can utilize these examples as a foundation to develop your own advanced prompt engineering techniques. The examples are accessible in a GitHub repository, which you can find [here](https://github.com/chatgpt4pcg/llms4pcg-pe-examples).

## Prompt Rules

1. The organizers reserve the right to update the rules and details of the competition at any time. Any changes will be communicated through our website.
   1. A submitted program must implement the interface through the [`llms4pcg-python`](https://github.com/chatgpt4pcg/llms4pcg-python) package provided by the competition to interact with your model via API and output final results in a specified format. Participants are <span style="color:#f44336">**not allowed**</span> to interact with your model via API through other methods.
   2. During each evaluation, we will use the latest version of the required competition's Python package available as of one week before the submission deadline.
   3. Any tools needed for the implementation of prompt engineering techniques are the responsibility of the participants to provide to the organizers. We do not aim to provide any free or paid services required by your program. We do not guarantee the compatibility of additional tools required as a part of your program. Instructions on how to set up these tools must be provided by participants. In case you utilize paid services, such as gated APIs, proprietary software, or specialized databases, it is the participants' responsibility to provide any required information to run the said software and confirm with these providers about the licenses, terms, and agreements for use in this competition. Any parts of the software that could not be made public must be explicitly stated and informed to the organizer to be removed before being made publicly available. We recommend participants check the specifications of the evaluation computer to ensure compatibility beforehand.
   4. The program <span style="color:#f44336">**must not**</span> modify responses from your model before writing them to files as final output for evaluation. We consider direct intervention to be cheating. Only the direct response from your model may be utilized as a final output.
   5. Modification of the message history of your model in a way that is considered cheating, such as altering the message history with manually created content (i.e., hard-coding answers), is prohibited.
   6. Modification of the token counter and timer used for the evaluation is prohibited.
   7. In the event of an error during a trial, that trial will be treated as producing an empty response.
   8. To ensure fairness, each program combined (source code, tools, databases, etc.) must be at most 1GB in total size including any data downloaded as a result of running the submitted program, and each trial will last only 120 seconds.
   9. Automatic prompt optimization may be utilized, but its use during the evaluation is discouraged as it quickly consumes available token limits. Therefore, we suggest employing these techniques beforehand.
   10. The sampling temperature is always fixed at 1. The random seed is not set during regular use to allow for varied outputs; however, a selected master seed will be used during final evaluation for reproducibility.
   11. If your code uses random number generation (e.g., `random` in Python), you <span style="color:#f44336">**must set a fixed seed in your code**</span> (e.g., `random.seed(42)`) to ensure reproducibility. Do not use system time or other varying values as the seed. 
2. Programs failing to follow the requirements in 1. will result in automatic disqualification.
3. To ensure that code blocks can be extracted successfully from responses generated by the your model API, each output must include three backticks ` ``` `.
   1. The code extraction script will only extract the content between the last pair of three backticks ` ``` `.
   2. The extracted code <span style="color:#f44336">**must not**</span> contain any loops. Any use of loops will be ignored, resulting in only one instance of the loop's content. The code <span style="color:#f44336">**should not**</span> use variables in the call of the `drop_block()` function, as this will result in an error and that response will be skipped for the rest of the evaluation process. To check the behavior of the code extractor, please refer to the [Resources]({{< ref "/competition/resources">}}) page where you can find an online tool for this task.
   3. If no code blocks are present or extracted code results in an empty string, the response will be skipped, and its score will be 0.
4. All plugins and function callings are disabled during the evaluation process.
5. The final response from your program must explicitly include a series of `drop_block()`, which will be executed in that order by our tool to generate a character-like structure in a Science Birds level.

### The `drop_block()` function

The definition of the `drop_block(block_type: str, x_position, int)` function is as follows:
1. It drops a block vertically drop a block from the top and center it at a specific slot, denoted by `x_position`.
2. This function works on the following settings:
   1. A structure is situated on a 2D grid with a width (`W`) of 20 columns and a height (`H`) of 16 rows. The grid consists of 320 cells, each of equal size.
   2. Coordinates `(x, y)` are used to represent the positions in the grid, where `x` and `y` show the horizontal and vertical indices of cells, respectively. For example, `(0, 0)` denotes the bottom-left corner cell of the grid, and `(W-1, H-1)` is the top-right corner cell.
   3. A cell on the grid has a size of 1x1. Each cell has unique `(x, y)` coordinates associated with it.
3. This function accepts two parameters:
   1. `block_type: str`: a value that indicates the type of block to be placed. The possible values are`b11`, `b13`, and `b31`. An invalid block type will result in an error.
      1. `b11` denotes a square block whose size is 1x1.  
         ![image](https://chatgpt4pcg.github.io/images/nextImageExportOptimizer/b11-opt-48.WEBP)
      2. `b13` denotes a column block whose size is 1x3.  
         ![image](https://chatgpt4pcg.github.io/images/nextImageExportOptimizer/b13-opt-48.WEBP)
      3. `b31` denotes a row block whose size is 3x1.  
         ![image](https://chatgpt4pcg.github.io/images/nextImageExportOptimizer/b31-opt-256.WEBP)
   2. `x_position: int`: a horizontal index of a grid cell, where `0` represents the leftmost column of the grid, and `W-1` represents the rightmost column of the grid. The `x_position` parameter indicates the center pivot point of the block being placed. For example, if `b31` is the only block in the level and is placed at `x_position=4`, it will occupy cells `(3, 0)`, `(4, 0)`, and `(5, 0)`. An invalid position, like a position where a block of interest intrudes on the grid boundary, will result in an error.
