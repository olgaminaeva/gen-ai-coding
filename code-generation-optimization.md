---
title: "Code Generation and Optimization"
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

Codeium accelerates software development through three key modes: Command, Chat, and Autocomplete. Each mode leverages Codeium’s real-time context awareness engine to deliver highly relevant and useful suggestions. In this lesson, we will explore the Command and Chat modes, as well as the concept of context awareness. The next lesson will focus on the Autocomplete mode.

## Command ##

Sometimes it can be easier to describe the what we want to code in natural language, espetially when writing simple pieces of code. In this episode, we will learn to use the **Command** feature of Codeium, which allows you to generate or modify code simply by using natural language inputs. Instead of manually coding everything, you can describe what you want in plain English, and Codeium will help you do it — whether it's creating new functions or refactoring existing pieces of code. 

- By pressing `⌘+I` on Mac or `Ctrl+I` on Windows/Linux, you can enter a prompt and receive code suggestions, making it easier and faster to develop code directly within your editor. 

- Codeium will then provide a multiline suggestion that you can accept or reject. You can accept a suggestion by pressing `⌥(Option)+A` on Mac or `Alt+A` on Windows/Linux, reject (`⌥+R` on mac or `Alt+R` on Windows/Linux), or follow-up a generation (`⌥+F` on Mac or `Alt+F` on Windows/Linux) by using the appropriate shortcuts or by clicking the corresponding code lens above the generated diff.

If you highlight a section of code before invoking **Command**, then the AI will edit the selection spanned by the highlighted lines. Otherwise, it will generate code at your cursor’s location.

![](episodes/fig/codeium_command_vscode.mp4){alt='Command'}

### Refactoring and Docstrings

In Codeium, code lenses appear right above your function and class definitions, providing convenient shortcuts for common tasks. These clickable labels allow you to quickly generate docstrings, explain code, or refactor code with just a click, saving time on manual edits. These features are powered by Command, which uses natural language inputs to assist with tasks like improving code structure and generating documentation.

Codeium’s Command feature enhances your coding workflow by offering specific functions through code lenses.

- **Refactor Functionality**: Clicking the Refactor label triggers Codeium’s refactoring capabilities, providing a dropdown of pre-filled options or allowing you to write a custom instruction. This is particularly useful for improving performance or restructuring code. You can also highlight a block of code and use Command (`⌘+I` or `Ctrl+I`) to perform more targeted refactoring.

- **Docstring Generation**: For generating documentation, clicking the Docstring label automatically creates a docstring above your function header (or under the function header in Python). This AI-generated documentation will describe what the function does, helping you maintain well-documented, readable code.

![](episodes/fig/command.webp){alt='Command'}

### Best Practices ###

Here are a few things to remember when using Command function of Codeium:

- The model behind Command is more advanced than the one used for autocomplete, making it slower but more capable of following complex instructions.

- To edit a specific selection of code, highlight that piece of code before using Command. If not, it will generate new code at the cursor's position.

- For effective use, try to give clear and detailed prompts. While simple requests like “Fix this” or “Refactor” can work well due to context awareness, more specific instructions like “Write a function that takes two inputs of type Diffable and implements the Myers diff algorithm” can yield even better results.

- Always review AI-generated docstrings to ensure they accurately reflect the purpose and parameters of the function.


::::::::::::::::::::::::::::::::::::: challenge

## Code and Functions Generation (10 min)

Read a datafile into a Pandas `DataFrame` object, produce datafile descriptives and plot the data distributions.

- Write a function that takes as input a `DataFrame` and that calculates basic descriptive statistics like: number of rows (`nrow`), number of columns (`ncol`), data types of each column, basic summary statistics (like mean, min, max for numeric columns).

- Write a function that takes as inputs a `DataFrame` and a column and generate an histogram to visualize data distribution if the column is numeric (e.g., `int64`, `float64`), a bar plot showing the category frequency if the column is categorical.

Review the AI-generated code and compare it to the version you would have written independently without the AI-assistant.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

Here is what you would expect to see in the generated code:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import glob

def calculate_descriptives(data_frame):
    nrow, ncol = data_frame.shape
    data_types = data_frame.dtypes
    summary_stats = data_frame.describe()
    
    return nrow, ncol, data_types, summary_stats

url = 'https://datahub.io/core/co2-ppm/r/co2-mm-mlo.csv'
df = pd.read_csv(url)
nrow, ncol, data_types, summary_stats = calculate_descriptives(df)
print(f'\nFile: {url}')
print(f'Number of rows: {nrow}\nNumber of columns: {ncol}\nData types: {data_types}')
summary_stats

```

And here is the histograms and bar plots that should be generated:

```python
def visualize_data_distribution(data_frame, column):
    if data_frame[column].dtype in ['int64', 'float64']:
        plt.hist(data_frame[column])
        plt.xlabel(column)
        plt.ylabel('Frequency')
        plt.title('Histogram of {}'.format(column))
        plt.show()

for col in df.columns:
    visualize_data_distribution(df, col)
```

Keep in mind, this is a suggested code, and you should always verify that it works as expected.

::::::::::::::::::::::::::::::::::::::::::::::::

## Chat

Another useful feature of Codeium is Chat function. It allows you to chat with the AI assistant and get instant feedback on your code. The Chat function is similar to the Command function, but it allows you to interact with the AI assistant in a more interactive and interactive way.

To use Chat function in VS code, click on the **Codeium** icon on the left sidebar of the VS code window. 

![](episodes/fig/chat_vscode_where_to_find.png){alt='Chat'}

### @mentions

In any chat message, you can use the @mentions feature to refer to context items from within the chat input by prefixing a word with `@`. Context items can be function names, class names, directories and files, or even content of your termnal history. By doing this explicitly, Codeium will make the most relevant suggestions for you.

For instance, you can mention classes, as shown below:

![](episodes/fig/atmentions1.gif){alt='@mentions'}

Here are some typical use cases of Chat function in VS code:
- **Writing Boilerplate Code**: Easily generate function headers or repetitive code blocks by providing simple prompts like “Write a function that takes X and Y, performs A, B, C, and returns Z.”

- **Writing Unit Tests**: You can use Chat to quickly write unit tests for your functions. For instance, ask it, “Write a unit test for @function-name that tests edge cases for X and Y.”

- **Generating Docstrings and Comments**: Use Chat to add useful comments or docstrings to your code. Simply prompt it by saying, “Write a docstring for @function-name,” and it will generate a detailed explanation.

- **Explaining Code**: For those new to a codebase or trying to understand complex logic, Chat can explain functions. You might ask, “Explain @function,” and Chat will provide a breakdown of the function’s purpose and workings.

### Prompting

Clear and efficient prompting is a vital element of both Chat and Command features. There are three key components to a good prompt:

- **Clear Objective:** Be specific about what you want Chat to produce—whether it’s new code, a refactor, or an explanation.

- **Contextual Details:** Use `@` mentions to provide context, such as referring to specific functions, classes, or modules.

- **Constraints:** If there are specific requirements, such as using certain frameworks or considering performance, include these in your prompt.

**Example:**

Bad: Refactor rawDataTransform

Good: Refactor @func:rawDataTransform by turning the while loop into a for loop and using the same data structure output as @func:otherDataTransformer

![](episodes/fig/best practices chat.png){alt='Best Practices for Chat'}

::::::::::::::::::::::::::::::::::::: challenge

## Optimization of the Code (5 min)

You will use Codeium to suggest improvements and restructure a sample Python code that processes a CO2 concentration dataset. 
Here’s a sample Python code that reads the dataset, processes it to find the average CO2 concentration, and plots the data:

```python
# Extract date and mean CO2
df['year'] = pd.to_datetime(df['Date']).dt.year
mean_co2 = df.groupby('year')['Interpolated'].mean()

# Plot the data
plt.figure(figsize=(10,5))
plt.plot(mean_co2.index, mean_co2)
plt.title('Average CO2 Concentration Over Years')
plt.xlabel('Year')
plt.ylabel('CO2 Concentration (ppm)')
plt.grid()
plt.show()
```

- Review the provided code. Identify areas that could be improved in terms of clarity, efficiency, or functionality.

- Use Command feature to generate suggestions, and then review and implement them. Did your code improve in terms of clarity, efficiency, or functionality?

You can try this with your own piece of code and see how it improves.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

After applying the suggestions, your optimized code might look something like this:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Convert date to datetime and extract the year
data['year'] = pd.to_datetime(df['Date']).dt.year

# Calculate the average CO2 concentration per year
mean_co2 = df.groupby('year')['Interpolated'].mean()

# Function to plot CO2 concentration
def plot_co2(data):
    plt.figure(figsize=(10, 5))
    plt.plot(data.index, data.values)
    plt.title('Average CO2 Concentration Over Years')
    plt.xlabel('Year')
    plt.ylabel('CO2 Concentration (ppm)')
    plt.grid()
    plt.show()

# Call the plotting function
plot_co2(mean_co2)
```

**Comparison:**

- The restructured code introduces a function `(plot_co2)` for plotting, making it clearer and more modular. Variable names remain descriptive, and comments provide context.

- The restructured version might have slightly more lines due to the function encapsulation, but it enhances readability and reusability.

- Further, the use of functions is generally considered best practice in Python, making the code easier to maintain.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Debugging Assistance (5 min)

In this exercise, you will use Codeium to identify and fix errors in a Python code snippet that processes the CO2 concentration dataset. Here’s a sample code snippet that contains several bugs:

```python
# Plot the data
plt.figure(figsize=(10, 5))
plt.plot(mean_co2.index, mean_co2)
plt.title('Average CO2 Concentration Over Years')
plt.xlabel('Year')
plt.ylabel('CO2 Concentration (ppm)')
plt.grid()
plt.show()
```

- Review the provided code snippet. Note any potential errors or issues that may prevent it from running correctly.

- Use the Chat or Command feature to generate suggestions to fix the errors. Review the suggestions provided by Codeium and apply the necessary fixes. Did your code improve in terms of clarity, efficiency, or functionality?

- Test the corrected code to ensure it runs without errors and produces the expected output.

- Review the changes made and discuss how Codeium helped identify and fix the errors. Consider the impact of these fixes on code functionality and readability.

- Reflect on the debugging process. What did you learn about using AI tools for debugging? How might this affect your future coding practices?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

After applying the corrections suggested by Codeium, your code should look something like this:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Read the CSV file into a Pandas DataFrame
data = pd.read_csv('co2-mm-mlo.csv')

# Convert date column to datetime
data['date'] = pd.to_datetime(data['date'])

# Extract year and CO2 levels
data['year'] = data['date'].dt.year
mean_co2 = data.groupby('year')['Interpolated'].mean()

# Plot the data
plt.figure(figsize=(10, 5))
plt.plot(mean_co2.index, mean_co2.values)
plt.title('Average CO2 Concentration Over Years')
plt.xlabel('Year')
plt.ylabel('CO2 Concentration (ppm)')
plt.grid()
plt.show()
```

**Changes:**

*Date Conversion:*

The code attempted to access the dt attribute of the 'date' column without first converting it to a datetime format, which would raise an error. --><br>
Added `data['date'] = pd.to_datetime(data['date'])` to ensure the date column is in the correct format for extracting the year.

*Plotting Values:*

When plotting, the code used mean_co2 directly, which could lead to confusion about the data being plotted. --><br> 
Changed `plt.plot(mean_co2.index, mean_co2)` to `plt.plot(mean_co2.index, mean_co2.values)` for clarity and to explicitly use the values.

::::::::::::::::::::::::::::::::::::::::::::::::

## Context Awareness

Above we mentioned that the Chat function is particularly helpful due to context awareness. Context awareness is one of Codeium’s most powerful features, allowing it to offer personalized and highly relevant suggestions by pulling information from various sources. Traditionally, generating code required training large LLMs on specific codebases, which is resource-intensive and not scalable for individual users. However, Codeium uses a more efficient method known as **retrieval-augmented generation (RAG)**.

![](episodes/fig/RAG.png){alt='RAG'}

Instead of retraining the model, it retrieves the most relevant pieces of context, such as:

1. **Open files in your IDE**: Codeium scans the current file and other open files in your development environment to gather context. This means the suggestions you receive are directly related to the code you're actively working on, ensuring relevance.
   
2. **Local repository**: Codeium goes beyond open files and searches through your entire local codebase. This retrieval engine can pull relevant snippets from the broader project, even from files that aren’t currently open, providing deeper insights and more accurate suggestions.

For instance, if you're working on a function and ask Codeium to help refactor it, the tool will pull in relevant context from both your active file and other parts of your codebase to improve the output. This combination of multiple context sources ensures higher-quality code generation, fewer errors, and suggestions that feel tailored to your project.

::::::::::::::::::::::::::::::::::::: keypoints 

- Command and Chat allow you to generate or edit code using natural language instructions, making it easy to describe complex tasks concisely.

- Chat can also be useful for code-related discussions and quick responses to queries; it will help you draft boilerplate code, write unit tests, and explain code functionality.

- Lenses, which are clickable prompts appear above functions and classes, offer shortcuts for common tasks like refactoring or generating docstrings, could help improve workflow efficiency.

- With Context Awareness, Codeium retrieves relevant context from open files and your entire codebase, ensuring tailored, high-quality suggestions that align with your current coding task.

::::::::::::::::::::::::::::::::::::::::::::::::
