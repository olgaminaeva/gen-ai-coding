---
title: "Introduction to AI coding assistants"
teaching: 20
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do AI coding assistants work?
- What are the main AI coding assistants and what are their main characteristics?
- How to set up Codeium as coding assistant for the lesson?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn about AI models behind coding assistants
- Outline the main AI coding assistants and their capabilities
- Set up Codeium as coding assistant for the lesson

::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction to AI coding assistants ##
Artificaial Intelligence (AI) models for coding assistants, such as Codeium and GitHub Copilot, rely on machine learning (ML) techniques, particularly deep learning and natural language processing (NLP), to assist developers. These models are trained on vast amounts of publicly available code and documentation to understand patterns, syntax, and code logic across various programming languages. 
Let’s break down the *key characteristics* of how these models work:

| Characteristic | Description | Examples |
| --- | ----------- | ------- |
| Code understanding through ML | AI coding assistants are built on models that analyze and learn from vast amounts of data, including open-source codebases, libraries, and developer behavior. These models break down code into a mathematical representation that the AI can interpret. They learn common patterns, best practices, syntax rules, and how developers approach specific tasks or problems. | When you start typing, the AI assistant predicts what you are likely to write next based on patterns it has learned. These predictions can be simple line completions or even more complex, multi-line code suggestions.|
| Context awareness | AI coding assistants are designed to understand context at multiple levels, including code, variables, and functions. This makes them able to suggest relevant code suggestions based on the context. | If you're writing a loop to iterate over a list of items, the AI can suggest the entire loop structure based on what it recognizes in the surrounding code.|
| NLP | AI models are both trained to understand code syntax and to interpret natural language. This is crucial for features like chat-based interaction or when a developer types a comment or command in plain English, expecting the AI to generate code. | If you write a comment like `"Create a function to fetch user data from an API"`, the AI can generate the function code based on that request. You can also ask questions, like `"How do I format dates in Python?"`, and the AI will provide an answer or relevant code snippet.
| Learning from user interaction | AI coding assistants also learn and improve from ongoing user interactions. Over time, they adjust to individual developer preferences and coding styles, offering more personalized and relevant suggestions | As users accept or reject suggestions, the assistant refines its future outputs based on this feedback (so-called "feedback loop"). Many AI coding assistants can learn from private codebases (when privacy policies allow) to better align with specific project structures, libraries, or functions common to a particular team or organization (custom adaptations). |
| Code generation and refactoring | *Code generation*: Based on a high-level description of what you want, the assistant can write larger blocks of code.<br> *Code refactoring*: AI can help optimize and refactor your code. | You might describe a task such as, `“Create a function to handle user authentication using OAuth2”`, and the assistant will generate the appropriate code. You might also ask, `“Refactor this code to use async/await for better performance”`, and the AI will generate the necessary changes to convert synchronous functions into asynchronous ones.|
| Multilanguage and multimodal Support | AI coding assistants are designed to support a wide variety of programming languages and paradigms, enabling them to work across different domains (e.g., web development, data science, system programming). They are trained on the syntax, idioms, and patterns of languages like Python, JavaScript, C++, and many others. | Codeium supports Assembly, C, C++, C#, Clojure, CMake, CoffeeScript, CSS, CUDA, Dart, Delphi, Dockerfile, Elixir, F#, Go, Groovy, Haskell, HCL, HTML, Java, JavaScript, Julia, JSON, Kotlin, LISP, Less, Lua, Makefile, MATLAB, Objective-C, pbtxt, PHP, Protobuf, Python, Perl, Powershell, R, Ruby, Rust, Sass, Scala, SCSS, shell, Solidity, SQL, Starlark, Swift, TypeScript, TSX, VBA, Vue, YAML. |

With a foundation of how AI models for coding assistants function — how they analyze code, offer suggestions, and improve efficiency — let’s explore some of the most popular AI coding assistants available today. Each tool uses AI in slightly different ways to enhance your coding experience. In the following table, we'll compare these tools to give you an overview of their key features, pricing, and capabilities. This will help you understand where Codeium fits and what alternatives you might consider.

## Popular AI coding assistants ##

| | **GitHub Copilot** | **Codeium** | **Amazon CodeWhisperer / Amazon Q Developer** | **Tabnine** | **Hugging Chat**  |
|------------|-----------|-----------------|-----------------|-------------------|------------------|
|  | ![](episodes/fig/github copilot logo.png) | ![](episodes/fig/codeium_logo.png) | ![](episodes/fig/amazon Q developer logo.png) | ![](episodes/fig/Tabnine-AI logo.png) | ![](episodes/fig/hugging chat logo.webp) |
| **Brief Introduction**  | AI-powered coding assistant developed in collaboration with OpenAI, suggests code as you type within the IDE. | AI coding assistant that enhances productivity with intelligent code completions and refactoring suggestions. | AI assistant from Amazon Web Services, offers real-time code recommendations and integrates into various development environments. | AI-powered code completion tool providing accurate, context-aware code suggestions across multiple languages. | Leverages open-source models for flexible and customizable AI code assistance. |
| **Key Features** | Integration with GitHub ecosystem<br><br> Multilingual support<br><br> Acts as a virtual pair programmer  | Advanced code completions<br><br> Code refactoring capabilities<br><br> Supports multiple programming languages | Code recommendations<br><br> Security scans for vulnerabilities<br><br> Real-time documentation assistance<br><br> Multilingual support  | Robust autocompletion<br><br> Learns from codebase to suggest relevant snippets and APIs<br><br> Extensive language support  | Open-source model integration<br><br> High flexibility in deployment<br><br> Supports diverse coding environments |
| **Pricing** | Free for verified students (via GitHub Student Pack)<br><br> Monthly subscription fee, often with a free trial month | Free version with basic features<br><br> Paid version for full access to advanced features and higher usage limits | Free tier with basic features<br><br> Paid tiers with additional features, higher usage limits, and advanced support | Free version with limited features<br><br> Pro version subscription-based, available monthly or yearly<br><br> Discounts for team licenses | Free access to open-source models<br><br> Paid options for advanced support and additional features |

Now that we've compared some of the top AI coding assistants, you can see that each tool offers unique features and benefits. For this lesson, we’ll focus on teaching you how to use AI coding assistants with Codeium as our primary example. Codeium offers a powerful, beginner-friendly experience that helps you speed up coding through intelligent completions, refactoring suggestions, and support for multiple programming languages.

In the next section, we’ll walk through the steps to set up Codeium in your development environment, so you can start taking advantage of these features right away.

## Setting up Codeium ##

1. Make sure you have an Integrated Development Environment (IDE) installed on your computer. Go to [the Codeium download page](https://codeium.com/download) to see a list of supported IDEs and installation instructions. In the current lesson, we will be working in Visual Studio Code (VS Code), therefore, we recommend installing VS Code. You can download it from the [VS Code download page](https://code.visualstudio.com/Download).

2. You can follow the [Codeium installation instructions in VS Code](https://codeium.com/vscode_tutorial) on the official website.

3. Open Extension Marketplace: Open the Extension Marketplace, which is the icon with boxes on the primary sidebar in your VS Code.

4. Install Codeium: Type Codeium in the marketplace search bar, open up the page and click the blue Install button.

![](episodes/fig/install_extension.png)

5. Authorize: After installation is complete, you should be prompted by Visual Studio Code with a pop-up on the bottom right to authorize Codeium. 
*If not, you should see an option to sign in to your Codeium account in the bottom left Accounts tab of your Visual Studio Code window.* 
Click the Sign in with Auth to use Codeium option. Either method (popup or Accounts tab) should redirect you to the Codeium website.

6. Create Account: If you do not have a Codeium account yet, you will be redirected to create an account.

7. Sign In: If you are not signed in, please sign in with your account details. Once you sign in, you will be redirected back to Visual Studio Code via pop-up.
Click Open Visual Studio Code, which should redirect you back to Visual Studio Code.
*If you are using a browser-based IDE, instead of being redirected back with pop-up, you will be routed to instructions on how to complete authentication by providing an access token. Please follow these instructions instead of Step 6, and then continue on with "Using Codeium."*

8. All Done! You will be asked to confirm the authentication in Visual Studio Code (click Open in the resulting pop-up).



### Using Codeium as your coding assistant ###

In this lesson, we will learn about the three ways Codeium can assist with coding: *Autocomplete*, *Chat*, and *Command*.

**Autocomplete:** This feature is always working in the background of your coding tool (IDE). It gives suggestions as you type, shown in light gray text. Autocomplete is most helpful when you already have a rough idea of what you want to code and just need to finish it quickly. It helps you stay focused and keeps your work flowing smoothly.

**Chat:** This feature allows you to ask questions and get answers using simple, everyday language. You can access Chat from the side panel in your coding tool. It’s great for when you’re working with new or unfamiliar code and need quick guidance or explanations.

**Command:** With Command, you can tell Codeium what changes you want to make to your code in plain language. Codeium will then suggest the changes, which you can choose to accept, reject, or adjust as needed.



::::::::::::::::::::::::::::::::::::: keypoints 

- AI coding assistants work by combining machine learning, contextual code understanding, and NLP to help developers code faster and more efficiently. 
- These tools predict, generate, and even optimize code based on the developer’s input and ongoing context, making them powerful companions in modern software development.
- There are several AI coding assistants abailable on the market, and they are designed to optimize your coding experience.
- To set up Codeium as your coding assistant you need to download and install the extension on our local PC.

::::::::::::::::::::::::::::::::::::::::::::::::
