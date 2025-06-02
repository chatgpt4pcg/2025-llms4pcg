---
title: Submission
type: docs
prev: competition/rules/prompt
next: competition/rules/evaluation/
weight: 2
---

## Submission Guideline

Before submitting, please ensure that your **program** follows our guidelines by checking the [Rules]({{< ref "/competition/rules">}}) and [Prompt]({{< ref "/competition/rules/prompt">}}) pages. It is particularly important that the `drop_block()` function used in your **program** is defined in the same way as our rules. If not, your results may be unexpected.

The submitted file should be zipped and provide a `README.md` file containing instructions on how to run your **program** along with any required dependencies in the zip file. Please also describe your approach in the `README.md` file. Failure to provide your instructions may result in a delayed evaluation process and disqualification from the competition. You may find the following `README.md` template helpful.

Your submission can be made using the following form: https://forms.gle/oAZQscN1S9UsQEv66

```md {filename=README.md}
# Team Name

## Team Members

List the names of the members of this team.

## Overview

Briefly describe your approach.

## Instructions

Describe what are the necessary environments or specific steps to run your program after unzipping the file.

## How to Run

Include detailed instructions on how to run your program. This may include commands, configurations, or specific steps.

## Dependencies

List all dependencies required to run your program. This may include libraries, frameworks, or specific software versions.
```

## What to Submit

Participants must submit the following files in a single zipped archive:

1. Program Code: The source code implementing the prompt generation algorithm. 
2. `README.md`: A document containing:
    - Team name and members
    - Overview of the approach
    - Instructions on setting up the environment
    - How to run the program
    - List of dependencies
3. Additional Resources (if any): Any supplementary files required for the execution of the program.

{{< callout type="warning" >}}
You do not need to submit the LLM itself, only the program that utilizes it.
{{< /callout >}}

## Evaluation Process

To participate, you must submit your prompt according to our guidelines. We will then generate a number of samples, each of which will undergo rigorous testing for stability, similarity, and diversity. Stability will be evaluated by loading the level in Science Birds and examining the ratio of unmoved blocks after 10 seconds of the initialization. The similarity of each generated level to its corresponding English character will be determined using an open-source ViT-based classifier model. The stability testing system and the instructions to use the classifier model, as well as all the relevant tools, will be provided. The newly introduced diversity is assessed by averaging the distances of unordered pairs of output vectors from the ViT classifier across trials, all pertaining to the same target character and prompt.

We hope that this edition will be more exciting and contribute to collective learning and discovery in the world of prompt engineering through this game competition!

## Submission Rules

1. If a team submits multiple entries during a stage, midterm or final, we will consider the most recent submission as that team's final submission.
2. Submissions received after the deadline will not be considered for the evaluation process.
3. By submitting, you accept all rules and agree that all submitted prompts and programs will be made public.

## Submission Deadline

~~**Midterm**: 30 May 2025 (23:59 JST)~~

**Final**: 30 July 2025 (23:59 JST)

Midterm submission is optional, although we recommend it. Any team that submits during the mid-term submission will be notified of the preliminary results. However, all teams, whether they submit during the midterm or not, must submit during the final submission period. Only submissions during the final submission period will be considered for the final ranking.

## Result Announcement

All participating teams will receive email notifications of their results using the email addresses provided in the submission email. The winner will also be announced on our website.
