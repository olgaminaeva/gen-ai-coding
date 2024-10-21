---
title: "Code generation and optimization"
teaching: 20
exercises: 20
---

:::::::::::::::::::::::::::::::::::::: questions 

- How to generate useful snippets of code using Codeium as AI-assistant?
- What steps to follow to optimize the performance of the code that Codeium generates?
- How to refactor and improve the structure of existing code using Codeium as AI-assistant?
- What are the best ways to use Codeium for identifying and fixing bugs in a code?
- How does Codeium’s context-awareness improve code suggestions during optimization and refactoring?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Generate snippets of code using Codeium as AI-assistant
- Optimize performance of the generated code using Codeium as AI-assistant
- Refactor and improve the structure and quality of existing code using Codeium as AI-assistant
- Identify and fix bugs using Codeium as AI-assistant
- Learn about context-awareness in AI-assisted coding

::::::::::::::::::::::::::::::::::::::::::::::::

## Command ##

Sometimes it can be easier to describe the what we want to code in natural language, espetially when writing simple pieces of code. In this episode, we will learn to use the **Command** fature of Codeium, which allows you to generate or modify code simply by using natural language inputs. Instead of manually coding everything, you can describe what you want in plain English, and Codeium will help you do it — whether it's creating new functions or refactoring existing pieces of code. 

- By pressing `⌘+I` on Mac or `Ctrl+I` on Windows/Linux, you can enter a prompt and receive code suggestions, making it easier and faster to develop code directly within your editor. 

- Codeium will then provide a multiline suggestion that you can accept or reject. You can accept a suggestion by pressing `⌥(Option)+A` on Mac or `Alt+A` on Windows/Linux, reject (`⌥+R` on mac or `Alt+R` on Windows/Linux), or follow-up a generation (`⌥+F` on Mac or `Alt+F` on Windows/Linux) by using the appropriate shortcuts or by clicking the corresponding code lens above the generated diff.


If you highlight a section of code before invoking **Command**, then the AI will edit the selection spanned by the highlighted lines. Otherwise, it will generate code at your cursor’s location.

![](episodes/fig/codeium_command_vscode.mp4){alt='Command'}

### Best practices ###

Here are a few things to remember when using Command function of Codeium:

- The model behind Command is more advanced than the one used for autocomplete, making it slower but more capable of following complex instructions.

- To edit a specific selection of code, highlight that piece of code before using Command. If not, it will generate new code at the cursor's position.

- For effective use, try to give clear and detailed prompts. While simple requests like “Fix this” or “Refactor” can work well due to context awareness, more specific instructions like “Write a function that takes two inputs of type Diffable and implements the Myers diff algorithm” can yield even better results.

::::::::::::::::::::::::::::::::::::: challenge

**Exercise 1: Code and functions generation**

- Read a datafile into a Pandas `DataFrame` object, produce datafile descriptives and plot the data distributions.

    - Write a function that takes as input a `DataFrame` and that calculates basic descriptive statistics like: number of rows (`nrow`), number of columns (`ncol`), data types of each column, basic summary statistics (like mean, min, max for numeric columns).

    - Write a function that takes as inputs a `DataFrame` and a column and generate an histogram to visualize data distribution if the column is numeric (e.g., `int64`, `float64`), a bar plot showing the category frequency if the column is categorical.

- Review the AI-generated code and compare it to the version you would have written independently without the AI-assistant.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution


::::::::::::::::::::::::::::::::::::::::::::::::

## Chat

### @mentions

### Code lenses

::::::::::::::::::::::::::::::::::::: challenge

**Exercise 2: Optimization of the code**

- Provide a sample code that needs optimization (will be an example from the medical field or, alternatively, I’ll search on stack exchange)

- Use Codeium to suggest improvements and restructure the code

- Compare the original and restructured versions (clarity, length…)

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution


::::::::::::::::::::::::::::::::::::::::::::::::


TODO

::::::::::::::::::::::::::::::::::::: challenge

**Exercise 3: Debugging assistance**

- You are presented with a code snippet with errors

- Use Codeium to detect and propose fixes

- Apply and test the corrections

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution


::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints 

TODO

::::::::::::::::::::::::::::::::::::::::::::::::
