---
title: "Introduction to AI Coding Assistants"
teaching: 20
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do AI coding assistants work?
- What are the main AI coding assistants and what are their main characteristics?
- How to set up Codeium as a coding assistant for the lesson?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn about AI models behind coding assistants
- Outline the main AI coding assistants and their capabilities
- Set up Codeium as a coding assistant for the lesson

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction ##

Artificial intelligence (AI) models for coding assistants, such as Codeium and GitHub Copilot, rely on machine learning (ML) techniques, particularly deep learning and natural language processing (NLP), to assist developers. These models are trained on vast amounts of publicly available code and documentation to understand patterns, syntax, and code logic across various programming languages. Here is a schematic process of training an AI coding assistant model.

![](episodes/fig/AI_tool_development.png) 

::::::::::::::::::::::::::::::::::::: callout

It’s important to note that many AI coding assistants are fine-tuned from foundation models rather than trained from scratch. Fine-tuning involves adapting a pre-trained model to specific tasks using smaller, task-specific datasets. This approach is more efficient as it uses the broad capabilities of foundation models, requiring *fewer resources* and *less time* than starting from scratch.

::::::::::::::::::::::::::::::::::::::::::::::::

Now let’s break down the *key characteristics* of how these models work:

| Characteristic | Description | Examples |
| --- | ----------- | ------- |
| **Code understanding through ML** | AI coding assistants are built on models that analyze and learn from vast amounts of data, including open-source codebases, libraries, and developer behavior. These models break down code into a mathematical representation that the AI can interpret. They learn common patterns, best practices, syntax rules, and how developers approach specific tasks or problems. | When you start typing, the AI assistant predicts what you are likely to write next based on patterns it has learned. These predictions can be simple line completions or even more complex, multi-line code suggestions.|
| **Context awareness** | AI coding assistants are designed to understand context at multiple levels, including code, variables, and functions. This makes them able to suggest relevant code suggestions based on the context. | If you're writing a loop to iterate over a list of items, the AI can suggest the entire loop structure based on what it recognizes in the surrounding code.|
| **NLP** | AI models are both trained to understand code syntax and to interpret natural language. This is crucial for features like chat-based interaction or when a developer types a comment or command in plain English, expecting the AI to generate code. | If you write a comment like `"Create a function to fetch user data from an API"`, the AI can generate the function code based on that request. You can also ask questions, like `"How do I format dates in Python?"`, and the AI will provide an answer or relevant code snippet.
| **Learning from user interaction** | AI coding assistants learn and improve from ongoing user interactions. Over time, they adjust to individual developer preferences and coding styles, offering more personalized and relevant suggestions. | As users accept or reject suggestions, the assistant refines its future outputs based on this feedback (so-called "feedback loop"). Many AI coding assistants can learn from private codebases (when privacy policies allow) to better align with specific project structures, libraries, or functions common to a particular team or organization (custom adaptations). |
| **Code generation and refactoring** | *Code generation*: Based on a high-level description of what you want, the assistant can write larger code blocks.<br> *Code refactoring*: AI can help optimize and refactor your code. | You might describe a task such as, `“Create a function to handle user authentication using OAuth2”`, and the assistant will generate the appropriate code. You might also ask, `“Refactor this code to use async/await for better performance”`, and the AI will generate the necessary changes to convert synchronous functions into asynchronous ones.|
| **Multilanguage and multimodal support** | AI coding assistants are designed to support many programming languages and paradigms, enabling them to work across domains (e.g., web development, data science, system programming). They are trained on the syntax, idioms, and patterns of languages like Python, JavaScript, C++, and many others. | Codeium supports Assembly, C, C++, C#, Clojure, CMake, CoffeeScript, CSS, CUDA, Dart, Delphi, Dockerfile, Elixir, F#, Go, Groovy, Haskell, HCL, HTML, Java, JavaScript, Julia, JSON, Kotlin, LISP, Less, Lua, Makefile, MATLAB, Objective-C, pbtxt, PHP, Protobuf, Python, Perl, Powershell, R, Ruby, Rust, Sass, Scala, SCSS, shell, Solidity, SQL, Starlark, Swift, TypeScript, TSX, VBA, Vue, YAML. |

::::::::::::::::::::::::::::::::::::: callout 

Not all AI-powered code assistance tools rely on generative AI. Many utilize traditional machine learning techniques to enhance coding efficiency, such as identifying errors, suggesting optimizations, or automating repetitive tasks. These tools often focus on static analysis, pattern recognition, or rule-based systems to provide real-time support without generating new content. By complementing human expertise, these AI tools streamline development workflows and help maintain code quality, offering reliable solutions for various programming needs.

For instance, [PMD](https://pmd.github.io/), an open-source static code analyzer to find code issues, that focuses on maintainability. [SonarQube](https://www.sonarsource.com/products/sonarqube/) analyzes code to identify bugs, vulnerabilities, and code smells using static analysis techniques. Finally, [Snyk Code](https://docs.snyk.io/scan-with-snyk/snyk-code) uses AI to suggest improvements and detect security issues in code.

::::::::::::::::::::::::::::::::::::::::::::::::

With a foundation of how AI models for coding assistants function — how they analyze code, offer suggestions, and improve efficiency — let’s explore some of the most popular AI coding assistants available today. Each tool uses AI in slightly different ways to enhance your coding experience. In the following table, we'll compare these tools to give you an overview of their key features, pricing, and capabilities. This will help you understand where Codeium fits and what alternatives you might consider.

## Popular AI Coding Assistants ##

| | **GitHub Copilot** | **Codeium** | **Amazon CodeWhisperer / Amazon Q Developer** | **Tabnine** | **Hugging Chat**  | **Cline** |
|------------|-----------|-----------------|-----------------|-------------------|------------------|----------------|
|  | ![](episodes/fig/github_copilot_logo.png) | ![](episodes/fig/codeium_logo.png) | ![](episodes/fig/amazon_Q_developer_logo.png) | ![](episodes/fig/Tabnine_AI_logo.png) | ![](episodes/fig/hugging_chat_logo.webp) | ![](episodes/fig/Cline_logo.png) |
| **Brief Introduction**  | AI coding assistant developed in collaboration with OpenAI, suggests code as you type within the IDE | AI coding assistant that provides code completions and refactoring suggestions | AI assistant from Amazon Web Services, offers real-time code recommendations and integrates into various development environments | AI code completion tool providing accurate, context-aware code suggestions across multiple languages | Leverages open-source models for flexible and customizable AI code assistance | AI-powered coding assistant available as a VSCode extension and a browser version |
| **Key Features** | Integration with GitHub ecosystem<br><br> Multilingual and multiline support<br><br> Acts as a virtual pair programmer  | Advanced code completions<br><br> Code refactoring capabilities<br><br> Supports multiple programming languages | Code recommendations<br><br> Security scans for vulnerabilities<br><br> Real-time documentation assistance<br><br> Multilingual support  | Robust autocompletion<br><br> Learns from codebase to suggest relevant snippets and APIs<br><br> Extensive language support  | Open-source model integration<br><br> High flexibility in deployment<br><br> Supports diverse coding environments | Autonomous coding capabilities using Claude 3.5 Sonnet<br><br> Terminal integration for executing commands<br><br> Browser interaction for debugging and testing |
| **Pricing** | Free for verified students (via GitHub Student Pack)<br><br> Monthly subscription fee, often with a free trial month | Free version with basic features<br><br> Paid version for full access to advanced features and higher usage limits | Free tier with basic features<br><br> Paid tiers with additional features, higher usage limits, and advanced support | Free version with limited features<br><br> Pro version subscription-based, available monthly or yearly<br><br> Discounts for team licenses | Free access to open-source models<br><br> Paid options for advanced support and additional features | A "free, open-source" extension|

::::::::::::::::::::::::::::::::::::: callout 

To maintain relevance and functionality, AI-powered coding tools must be updated regularly. These updates are critical for addressing evolving user needs, technological advancements, and emerging challenges in security, compliance, and language support. 

::::::::::::::::::::::::::::::::::::::::::::::::

Now that we've compared some of the top AI coding assistants, you can see that each tool offers unique features and benefits. For this lesson, we’ll focus on how to use AI coding assistants with Codeium as our primary example. Codeium offers a powerful, beginner-friendly experience that helps you speed up coding through intelligent completions, refactoring suggestions, and support for multiple programming languages.

For setting up Codeium, you can follow the instructions on [this lesson's setup page](https://olgaminaeva.github.io/gen-ai-coding/#setting-up-codeium).


### Using Codeium as your Coding Assistant ###

In this lesson, we will learn about the three ways Codeium can assist with coding: *Autocomplete*, *Chat*, and *Command*.

**Autocomplete:** This feature is always working in the background of your coding tool (IDE). It gives suggestions as you type, shown in light gray text. Autocomplete is most helpful when you already have a rough idea of what you want to code and just need to finish it quickly. It helps you stay focused and keeps your work flowing smoothly.

**Chat:** This feature allows you to ask questions and get answers using simple, everyday language. You can access Chat from the side panel in your coding tool. It’s great for when you’re working with new or unfamiliar code and need quick guidance or explanations.

**Command:** With Command, you can tell Codeium what changes you want to make to your code in plain language. Codeium will then suggest the changes, which you can choose to accept, reject, or adjust as needed.


::::::::::::::::::::::::::::::::::::: keypoints 

- AI coding assistants work by combining ML, contextual code understanding, and NLP to help developers code faster and more efficiently. 
- These tools predict, generate, and even optimize code based on the developer’s input and ongoing context, making them powerful companions in modern software development.
- There are several AI coding assistants available on the market, and they are designed to optimize your coding experience.
- To set up Codeium as your coding assistant you need to download and install the extension on our local PC.

::::::::::::::::::::::::::::::::::::::::::::::::
