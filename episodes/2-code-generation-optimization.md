---
title: "Code Generation and Optimization"
teaching: 20
exercises: 20
---

### TODO: Update times
### TODO: Update questions and objectives

:::::::::::::::::::::::::::::::::::::: questions 

- How to generate useful snippets of code using Codeium as AI-assistant?
- What steps to follow to optimize the performance of the code that Codeium generates?
- How to refactor and improve the structure of existing code using Codeium as AI-assistant?
- What are the best ways to use Codeium for identifying and fixing bugs in a code?
- How does Codeium’s context-awareness improve code suggestions during optimization and refactoring?
- How can the Autocomplete function in Codeium help improve your coding speed?
- What types of repetitive coding tasks can be automated?
- What are some key components of a clear and effective prompt when using the Autocomplete function?
- In what ways can Codeium assist in generating and improving code documentation?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Generate snippets of code using Codeium as AI-assistant
- Optimize performance of the generated code using Codeium as AI-assistant
- Refactor and improve the structure and quality of existing code using Codeium as AI-assistant
- Identify and fix bugs using Codeium as AI-assistant
- Learn about context-awareness in AI-assisted coding
- Use an Autocomplete function of Codeium to improve coding speed
- Automate repetitive coding tasks using the Autocomplete function of Codeium
- Compose clear and effective prompts that capture and facilitate the expected outcomes using the Autocomplete function
- Generate and improve documentation using Codeium

::::::::::::::::::::::::::::::::::::::::::::::::

Codeium accelerates software development through three key modes: Command, Chat, and Autocomplete. Each mode leverages Codeium’s real-time context awareness engine to deliver highly relevant and useful suggestions. We will explore how to use these features to generate, optimize, and refactor code, as well as to identify and fix bugs. 

Please note that while using Python is not required since Codeium supports multiple programming languages, all exercises and solutions will be provided in Python.

## Command

The **Command** feature of Codeium allows you to generate or modify code by using natural language inputs. Instead of manually coding everything, you can describe what you want in plain English, and Codeium will help you do it — whether it's creating new functions or refactoring existing pieces of code. 

- By pressing `⌘(Command)+I` on Mac or `Ctrl+I` on Windows/Linux, you can enter a prompt and receive code suggestions, making it easier and faster to develop code directly within your editor. 

- Codeium will then provide a multiline suggestion that you can accept or reject. You can accept a suggestion by pressing `⌥(Option)+A` on Mac or `Alt+A` on Windows/Linux, reject (`⌥+R` on mac or `Alt+R` on Windows/Linux), or follow-up a generation (`⌥+F` on Mac or `Alt+F` on Windows/Linux) by using the appropriate shortcuts or by clicking the corresponding code lens above the generated diff.

If you highlight a section of code before invoking **Command**, then the AI will edit the selection spanned by the highlighted lines. Otherwise, it will generate code at your cursor’s location.

![](episodes/fig/codeium_command_vscode.mp4){alt='Command'}

### Refactoring, Docstrings, and More

In Codeium, code lenses appear right above your function and class definitions, providing convenient shortcuts for common tasks. These clickable labels allow you to quickly generate docstrings, explain code, or refactor code with just a click, saving time on manual edits. These features are powered by Command, which is invoked when the code lenses are clicked.

- **Refactor Functionality**: Clicking the `Refactor` label triggers Codeium’s refactoring capabilities, providing a dropdown of pre-filled options or allowing you to write a custom instruction. This is particularly useful for improving performance or restructuring code. You can also highlight a block of code and use Command (`⌘+I` or `Ctrl+I`) to perform more targeted refactoring.

- **Docstring Generation**: For generating documentation, clicking the `Docstring` label automatically creates a docstring above your function header (or under the function header in Python). This AI-generated documentation will describe what the function does, helping you maintain well-documented, readable code. In Python, for example, the docstring will be correctly placed directly beneath the function header.

![](episodes/fig/command.webp){alt='Command'}

![](episodes/fig/jetbrains_docstrings.gif){alt='Docstring generation'}

::::::::::::::::::::::::::::::::::::: callout

### Smart Paste

This feature lets you copy code and paste it into a file in your IDE that's written in a different programming language. Use `⌘+⌥+V` (Mac) or `Ctrl+Alt+V` (Windows/Linux) to activate Smart Paste. Codeium will automatically detect the language of the destination file and translate the code in your clipboard accordingly. With context awareness, Codeium will also adapt the pasted code to integrate seamlessly, such as by referencing relevant variable names.


Here are some potential use cases:

- Code migration: for instance, converting JavaScript to TypeScript or translating Java into Kotlin.
- Adapting code from online sources: you found a helpful utility function in Go, but your project is in Rust.
- Exploring a new language: if you're curious about Haskell, you can see how your code might look if written in it.

:::::::::::::::::::::::::::::::::::::

### Best Practices

Here are a few things to remember when using Command function of Codeium:

- The model behind Command is more advanced than the one used for autocomplete, making it slower but more capable of following complex instructions.

- To edit a specific selection of code, highlight that piece of code before using Command. If not, it will generate new code at the cursor's position.

- For effective use, try to give clear and detailed prompts. While simple requests like “Fix this” or “Refactor” can work well due to context awareness, more specific instructions like “Write a function that takes two inputs of type `Diffable` and implements the Myers diff algorithm” can yield even better results.

![](episodes/fig/codeium_chat_best_practices.png){alt='Best Practices for Command'}

::::::::::::::::::::::::::::::::::::: challenge

## Assisted Code Generation, Part 1 (5 min)

### TODO: add part 2 in debugging

In this exercise, you will use the Command mode to load a [CO2 concentration dataset](https://datahub.io/core/co2-ppm/) from the file `co2-mm-mlo.csv` into a Pandas DataFrame, then generate descriptive statistics and visualize data distributions.

1.  Write a function that takes a DataFrame as input and calculates key descriptive statistics, including:

   - Number of rows and columns
   - Data types of each column
   - Summary statistics (e.g., mean, minimum, maximum) for numeric columns

2. Write a function that accepts a DataFrame and a specific column as inputs. If the column is numeric (e.g., `int64`, `float64`), create a histogram to display its distribution; if categorical, create a bar plot to show category frequencies.

3. Write a function to plot the `Average` and `Interpolated` columns on a single graph, with Date on the x-axis, to visualize their distributions over time.

After completing these tasks, review the AI-generated code and compare it to the version you might have written independently, considering structure, readability, and accuracy.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

Here is what you would expect to see in the generated code:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
url = 'https://datahub.io/core/co2-ppm/r/co2-mm-mlo.csv'
df = pd.read_csv(url)

def calculate_descriptive_stats(data_frame):
    nrow, ncol = data_frame.shape
    data_types = data_frame.dtypes
    summary_stats = data_frame.describe()
    return nrow, ncol, data_types, summary_stats

def visualize_column_distribution(data_frame, column):
    if data_frame[column].dtype in ['int64', 'float64']:
        plt.hist(data_frame[column], bins=20, edgecolor='k')
        plt.xlabel(column)
        plt.ylabel('Frequency')
        plt.title(f'Histogram of {column}')
    else:
        data_frame[column].value_counts().plot(kind='bar')
        plt.xlabel(column)
        plt.ylabel('Count')
        plt.title(f'Bar Plot of {column}')
    plt.show()

def plot_average_and_interpolated(data_frame):
    data_frame['Date'] = pd.to_datetime(data_frame['Date'])
    plt.figure(figsize=(12, 6))
    plt.plot(data_frame['Date'], data_frame['Average'], label='Average')
    plt.plot(data_frame['Date'], data_frame['Interpolated'], label='Interpolated', linestyle='--')
    plt.xlabel('Date')
    plt.ylabel('CO2 Concentration (ppm)')
    plt.title('Average vs Interpolated CO2 Concentrations Over Time')
    plt.legend()
    plt.grid()
    plt.show()

# Example usage
nrow, ncol, data_types, summary_stats = calculate_descriptive_stats(df)
print(f'Number of rows: {nrow}, Number of columns: {ncol}')
print(f'Data types:\n{data_types}')
print(f'Summary statistics:\n{summary_stats}')

for col in df.columns:
    visualize_column_distribution(df, col)

plot_average_and_interpolated(df)
```

There is something wrong here—can you spot it? We will address this issue later, but for now, let's continue.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge 

## Docstrings Generation (5 min)

Modify the `calculate_descriptive_stats()` and `visualize_column_distribution()` functions you created during the previous exercise to add a detailed docstring using Codeium's `Docstring` lens. Each docstring should:

- Describe the purpose of the function
- Document the function’s arguments and expected data types
- Explain what the function returns (if applicable)
- Optionally, provide a usage example

Please note that, while you could manually write the docstring and use suggestions from Autocomplete mode (which we will cover later in this episode), this task is designed to demonstrate Codeium's `Docstring` functionality.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

Here’s an example of how the `calculate_descriptive_stats()` and the `visualize_column_distribution() `functions might look with the generated docstrings:

```python
def calculate_descriptive_stats(data_frame):
    """
    Calculate the number of rows, number of columns, data types of columns,
    and descriptive statistics of a given DataFrame.

    Parameters
    ----------
    data_frame : pandas.DataFrame
        The DataFrame to be analyzed

    Returns
    -------
    tuple
        A tuple containing (nrow, ncol, data_types, summary_stats)
    """
    nrow, ncol = data_frame.shape
    data_types = data_frame.dtypes
    summary_stats = data_frame.describe()
    return nrow, ncol, data_types, summary_stats

def visualize_column_distribution(data_frame, column):
    """
    Visualize the distribution of the given column in a DataFrame.

    Parameters
    ----------
    data_frame : pandas.DataFrame
        The DataFrame containing the column to be visualized
    column : str
        The column name to be visualized

    Returns
    -------
    None

    Notes
    -----
    If the column is numeric (int64 or float64), a histogram is plotted.
    Otherwise, a bar plot of the value counts is plotted.
    """    
    if data_frame[column].dtype in ["int64", "float64"]:
        plt.hist(data_frame[column], bins=20, edgecolor="k")
        plt.xlabel(column)
        plt.ylabel("Frequency")
        plt.title(f"Histogram of {column}")
    else:
        data_frame[column].value_counts().plot(kind="bar")
        plt.xlabel(column)
        plt.ylabel("Count")
        plt.title(f"Bar Plot of {column}")
    plt.show()
```

Note that you might need to adjust the generated docstring if the function has complex logic or if the generated docstring lacks specific details about edge cases or exceptions.

::::::::::::::::::::::::::::::::::::::::::::::::

## Chat

### TODO: refactor this section

The Codeium Chat feature offers a powerful way to interact with an AI assistant directly within your coding environment, providing instant, contextual feedback on your code. Unlike the Command function, Codeium Chat is designed for a more conversational and responsive interaction, making it easy to discuss complex coding questions and solutions.

In Visual Studio Code, you can access Codeium Chat by clicking on the Codeium icon located in the left sidebar by default.

![](episodes/fig/chat_vscode_where_to_find.png){alt='Chat'}

To quickly open the chat panel or toggle focus between it and your code editor, use `⌘+⇧+A` on Mac or `Ctrl+⇧+A` on Windows/Linux. For a more flexible experience, you can pop the chat panel out of the IDE entirely by clicking the "pop-out" icon at the top of the chat window.

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
Here’s a sample Python code that processes the dataset to find the difference between the average and interpolated CO2 concentration for each row:

```python
avg_int = []
for i in range(df.shape[0]):
    avg_int.append(df.iloc[i]['Average'] - df.iloc[i]['Interpolated'])

df['Avg-Int'] = avg_int
```

- Review the provided code. Identify areas that could be improved in terms of clarity, efficiency, or functionality.

- Use Command feature to generate suggestions, and then review and implement them. Did your code improve in terms of clarity, efficiency, or functionality?

You can try this with your own piece of code and see how it improves.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

After applying the suggestions, your optimized code might look something like this:

```python
df['Avg-Int_opt'] = df.apply(lambda x: x['Average'] - x['Interpolated'], axis=1)
assert df['Avg-Int'].equals(df['Avg-Int_opt'])
```
Or even like this:

```python
df['Avg-Int'] = df['Average'] - df['Interpolated']
```

**Comparison:**

- The second version is faster and more memory-efficient because it uses vectorized operations, which are a key feature of the pandas library.
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Optimization of the Code - 2 

Similar to the exercise above, execute the code as is to verify it works and examine the output. Then use Codeium’s Chat feature to analyze and suggest potential improvements. Look for ways to enhance performance, readability, and conciseness.

```python
# Convert 'Date' column to datetime format
data['Date'] = pd.to_datetime(data['Date'], format='%Y-%m')

# Filter data for a specific date range
filtered_data = data[(data['Date'] >= '2000-01-01') & (data['Date'] <= '2010-12-31')]

# Extract the year value from the 'Date' column
filtered_data['Year'] = filtered_data['Date'].dt.year

# Group data by year and calculate the average CO2 level for each year
avg_co2_per_year = filtered_data.groupby('Year')['Interpolated'].mean()

# Plot the results
plt.figure(figsize=(10, 6))
plt.plot(avg_co2_per_year.index, avg_co2_per_year, label='Average CO2 (ppm)', marker='o')
plt.xlabel('Year')
plt.ylabel('CO2 (ppm)')
plt.title('Average CO2 Levels by Year (2000-2010)')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

```python
# Convert 'Date' column to datetime format and filter data for a specific date range
filtered_data = data[(pd.to_datetime(data['Date'], format='%Y-%m') >= '2000-01-01') & 
                     (pd.to_datetime(data['Date'], format='%Y-%m') <= '2010-12-31')]


# Group data by year and calculate the average CO2 level for each year
avg_co2_per_year = filtered_data.groupby(pd.to_datetime(filtered_data['Date'], format='%Y-%m').dt.year)['Interpolated'].mean()


# Plot the results
avg_co2_per_year.plot(figsize=(10, 6), marker='o')
plt.xlabel('Year')
plt.ylabel('CO2 (ppm)')
plt.title('Average CO2 Levels by Year (2000-2010)')
plt.grid(True)
plt.tight_layout()
plt.show()
```

**Comparison:**

- Combined the `pd.to_datetime` conversion and filtering steps into one.

- Removed the unnecessary `filtered_data['Year']` column and used the `dt.year` accessor to extract the year from the `'Date'` column.

- Simplified the plotting code by using the `plot` method of the Series object and removing the unnecessary `plt.figure` call.

- Removed the `label` parameter from the `plot` function, as it is not necessary when using the `plot` method of the Series object.

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Optimization of the Code - 3

In this exercise, you’ll again work with a code snippet that loads a dataset, processes CO₂ concentration data, and performs calculations. The initial code is functional but could benefit from optimization. Your task is to analyze it with Codeium to find improvements in both performance and readability.

```python
# Process data
data['Date'] = pd.to_datetime(data['Date'], errors='coerce')
data = data.dropna(subset=['Date', 'Interpolated'])

# Calculate annual CO2 average
annual_avg = data.groupby(data['Date'].dt.year)['Interpolated'].mean()

# Find the highest year-over-year increase
yearly_diff = annual_avg.diff().fillna(0)
max_increase_year = annual_avg.idxmax()
max_increase = yearly_diff[max_increase_year]

print(f"The year with the highest CO₂ increase was {max_increase_year} with an increase of {max_increase:.2f} ppm.")
```

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

```python
# Process data and calculate annual CO2 average
annual_avg = data.dropna(subset=['Date', 'Interpolated'])['Interpolated'].groupby(pd.to_datetime(data['Date'], errors='coerce').dt.year).mean()


# Find the highest year-over-year increase
max_increase_year = annual_avg.idxmax()
max_increase = annual_avg.diff().fillna(0)[max_increase_year]


print(f"The year with the highest CO₂ increase was {max_increase_year} with an increase of {max_increase:.2f} ppm.")
```

**Comparison:**

- Combined the data processing and annual average calculation into a single line of code.

- Removed the unnecessary `yearly_diff` variable and instead calculated the difference directly in the line where `max_increase` is calculated.

- Removed the unnecessary `max_increase_year` calculation and instead used the `idxmax` method directly on the `annual_avg` series.

::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: challenge

## Debugging Assistance (5 min)

In this exercise, you will use Codeium to identify and fix errors in a Python code snippet that processes the CO2 concentration dataset. The initial code has both logical and runtime errors, and there's potential for optimizations. You’ll use Codeium to debug, correct, and improve the script for better functionality and efficiency.

```python
# Filter data where CO₂ concentration is above average
above_avg_data = data[data['ppm'] > data['ppm'].mean]

# Calculate the monthly change in CO₂ concentration
data['monthly_change'] = data['ppm'] - data['ppm'].shift()

# Find the max monthly change
max_monthly_change = max(data['monthly_change'])

# Find the date when max monthly change occurred
max_change_date = data['date'][data['monthly_change'] == max_monthly_change]

print(f"The maximum monthly change in CO₂ concentration was {max_monthly_change} ppm on {max_change_date}.")
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

```

**Changes:**


::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Debugging Assistance - 2 (5 min)

```python
import pandas as pd
import numpy as np

# Load the dataset
data = pd.read_csv("https://datahub.io/core/co2-ppm/r/co2-mm-mlo.csv")

# Filter data for the years 2010 and 2020
data_2010 = data[data['Year'] == 2010]
data_2020 = data[data['Year'] == 2020]

# Calculate average CO2 concentration for each year
avg_co2_2010 = data_2010['Interpolated'].mean
avg_co2_2020 = data_2020['Interpolated'].mean

# Calculate the CO2 increase
co2_increase = avg_co2_2020 - avg_co2_2010

print("The increase in CO2 levels from 2010 to 2020 is:", co2_increase)
```
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

After applying the corrections suggested by Codeium, your code should look something like this:

```python

```

**Changes:**


::::::::::::::::::::::::::::::::::::::::::::::::

## Autocomplete

### TODO: refactor this section

A key feature of Codeium is its Autocomplete function: with every keystroke, Codeium actively attempts to predict and complete what you're typing. By analyzing the current file, previous edits, and contextual snippets from your codebase, it offers relevant suggestions as "ghost text".

![](episodes/fig/acceleration.gif){alt='Autocomplete Function'}

This feature can be particularly useful when you're writing boilerplate code (which refers to repetitive code that often serves as a standard template), as it can save you time and reduce the likelihood of errors. By leveraging Codeium's Autocomplete function, you can speed up your coding process and focus on the more creative and challenging aspects of your work.

### Boilerplate, Formatting, and More

As already mentioned above, one of the most powerful ways to use Codeium is for automating repetitive coding tasks. Whether you’re writing boilerplate code, standard functions, or common design patterns, Codeium's AI assistant can help speed up the process and reduce the manual effort required.

By recognizing patterns in your codebase, Codeium can predict and suggest repetitive structures such as:

- **Boilerplate code**: Generate routine code structures like class definitions, function signatures, or common initialization blocks with minimal effort.
- **Repetitive functions**: Quickly replicate commonly used functions or methods that follow a similar pattern, reducing the need for retyping or copy-pasting.
- **Code formatting and styling**: Maintain consistency in your code format by allowing Codeium to suggest and automate repetitive formatting tasks, saving you from manual corrections.

For example, when writing a set of functions that handle similar operations, Codeium can recognize the pattern after a few examples and suggest the next method based on prior code. This not only speeds up your workflow but also minimizes the risk of errors from copying or manually creating repetitive code.

::::::::::::::::::::::::::::::::::::: callout 

## Autocomplete Feature for Docstrings

Note that Codeium's Autocomplete feature may also suggest docstrings as you type, further assisting in creating well-documented functions without needing to manually write them. This can be particularly useful when you need to create specific wordings and have the freedom to customize documents interactively.

::::::::::::::::::::::::::::::::::::::::::::::::

### Fill-in-the-middle (FIM)

Codeium's Autocomplete model also includes Fill-in-the-Middle (FIM) capabilities. This is crucial because, more often than not, you're inserting code within an existing file, rather than just appending new lines. With FIM, Autocomplete analyzes the code both above and below the current line to provide more accurate suggestions.

Let's compare the FIM-enabled model to the standard model.

Codeium Autocomplete (with FIM):

![](episodes/fig/fim_12.png){alt='FIM'}

Competitor Autocomplete (without FIM): 

![](episodes/fig/fim_13.png){alt='No FIM'}

Note that the non-FIM model suggests a generic docstring based on only the preceding line with the function signature. In contrast, the FIM model provides a more contextually relevant suggestion based on the entire function definition.

### Inline Comments

You can guide the Autocomplete feature by using comments within your code. Codeium interprets these comments and generates code suggestions to implement what the comment describes.

![](episodes/fig/minimize_boilerplate.gif){alt='Inline Comments'}

### Shortcuts

The following shortcuts can be used to speed up your workflow: 

- `Tab` = accept suggestion
- `Esc` = clear suggestions

#### MacOS

- `Cmd` + `Left Arrow` = accept next word in suggestion
- `Option` + `]` = next suggestion

#### Windows/Linux

- `Ctrl` + `Left Allow` = accept next word in suggestion
- `Alt` + `]` = next suggestion


### Best Practices

- Avoid manually triggering Autocomplete; instead, let it naturally enhance your workflow. Writing prompts as comments is not recommended, but decorating your code with quality comments and information variable/function names yields the best results.
- To achieve the best results with Autocomplete, it's important to enhance your code with clear, *declarative* (not instructive) code, descriptive function names, and good comments with examples of the desired inputs and outputs. See the table below for examples:

    ![](episodes/fig/table_autocomplete.png){alt='Best Practices for Autocomplete'}

- If needed, you can temporarily snooze Autocomplete. This feature is available in VS Code version 1.8.66. Simply click the Codeium button in the bottom right to access it.

::::::::::::::::::::::::::::::::::::: challenge 

## Autocomplete Exploration (10 min)

Familiarize yourself with Codeium's Autocomplete feature by practicing coding tasks. Create the function `analyze_co2_trends()` that processes the CO2 data in `weekly_in_situ_co2_mlo.csv` to calculate monthly average CO2 concentrations and visualizes the trend over time. The function should:

- Accept the dataframe as an argument.
- Convert the `date` column to a datetime format.
- Discard any rows with missing values.
- Resample the data to calculate monthly averages for CO2 concentrations.
- Visualize the trends over time in a well-formatted plot.
- Return the monthly averages.

**Note**: While this task can be solved without using Autocomplete, it’s important to use Codeium in this exercise to demonstrate how Autocomplete can assist with coding. Although using Python is not mandatory, the solution will be provided in Python.

1. What are the benefits of using Codeium’s Autocomplete feature in this function?
2. What are the potential drawbacks of relying on Autocomplete?
3. How can you improve the accuracy of suggestions using Autocomplete?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: solution 

## Solution

Here’s a sample outline of what the `analyze_co2_trends()` function might look like:

```python
def analyze_co2_trends(df):
    # Convert 'date' column to datetime
    df['date'] = pd.to_datetime(df['date'])
    
    # Set 'date' as index
    df.set_index('date', inplace=True)
    
    # Drop rows with NaN values
    df.dropna(inplace=True)
    
    # Resample data to get monthly averages
    monthly_avg = df.resample('M').mean()
    
    # Plotting
    plt.figure(figsize=(10, 5))
    plt.plot(monthly_avg.index, monthly_avg['CO2 ppm'], marker='o')
    plt.title('Monthly Average CO2 Concentrations')
    plt.xlabel('Date')
    plt.ylabel('CO2 Concentration (ppm)')
    plt.grid()
    plt.show()
    
    return monthly_avg
```

1. Autocomplete saves time by suggesting common functions, reducing the need for memorization, preventing typos, and recognizing patterns to speed up repetitive tasks.
2. Be cautious! You might miss out on understanding the code if you accept suggestions blindly. Autocomplete can also suggest incorrect functions if the context is unclear.
3. Improve suggestion accuracy by writing clear comments and using meaningful variable/function names, which help Codeium understand the context better.

::::::::::::::::::::::::::::::::::::::::::::::::

## Context Awareness

### TODO: refactor this section

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

- Codeium's Autocomplete boosts coding speed by predicting and completing code based on context, past edits, and current files.

- Automating repetitive tasks like boilerplate code, repetitive functions, and formatting reduces errors and saves time.

- Fill-in-the-Middle (FIM) improves suggestions by analyzing the code above and below the insertion point.

- Docstring generation via code lenses automates the creation of accurate docstrings in the correct location.

::::::::::::::::::::::::::::::::::::::::::::::::
