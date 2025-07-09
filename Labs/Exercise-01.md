# Lab 01: Understanding the Lifecycle of Flow Development (READ ONLY)

## Estimated Duration: 30 Minutes

## Lab Overview
In this lab, you will explore the lifecycle of developing AI applications using Azure AI Foundry's Prompt Flow. You'll start by understanding the structured process, including initialization, experimentation, evaluation, refinement, and production stages. You will learn about different flow types, such as Standard, Chat, and Evaluation flows, and how they cater to various application needs. You'll also delve into the concept of flows and nodes within Prompt Flow, which enables seamless data processing and task execution.

## Lab Objective

In this lab, you will perform the following:
- Task 1: Comprehend the Flow Development Lifecycle
     - Task 1.1: Understand the types of flows  
     - Task 1.2: Understand a flow  
     - Task 1.3: Explore the tools available in prompt flow
  
### Task 1: Comprehend the Flow Development Lifecycle

Prompt flow offers a well-defined process that facilitates the seamless development of AI applications. By using it, you can effectively progress through the stages of developing, testing, tuning, and deploying flows, ultimately resulting in the creation of fully fledged AI applications.

The lifecycle consists of the following stages:

- **Initialization**: Identify the business use case, collect sample data, learn to build a basic prompt, and develop a flow that extends its capabilities.
Experimentation: Run the flow against sample data, evaluate the prompt's performance, and iterate on the flow if necessary. Continuously experiment until satisfied with the results.
- **Evaluation and refinement**: Assess the flow's performance by running it against a larger dataset, evaluate the prompt's effectiveness, and refine it as needed. Proceed to the next stage if the results meet the desired criteria.
- **Production**: Optimize the flow for efficiency and effectiveness, deploy it, monitor performance in a production environment, and gather usage data and feedback. Use this information to improve the flow and contribute to earlier stages for further iterations.

  >**Note**: By following this structured and methodical approach, prompt flow empowers you to develop, rigorously test, fine-tune, and deploy flows with confidence, resulting in the creation of robust and sophisticated AI applications.

### Task 1.1: Understand the types of flows

In this task, you will explore different flow types in Azure AI Foundry
1. Navigate to Azure AI Foundry using the link below:
    ```
    https://ai.azure.com/
    ```
1. In Azure AI Foundry, click on `Prompt flow` in the left pane and then select `+ Create`. Here you can start a new flow by selecting a flow type or a template from the gallery.

  - **Standard flow**: Designed for general application development, the standard flow allows you to create a flow using a wide range of built-in tools for developing LLM-based applications. It provides flexibility and versatility for developing applications across different domains.
  - **Chat flow**: Tailored for conversational application development, the Chat flow builds upon the capabilities of the standard flow and provides enhanced support for chat inputs/outputs and chat history management. With native conversation mode and built-in features, you can seamlessly develop and debug their applications within a conversational context.
  - **Evaluation flow**: Designed for evaluation scenarios, the evaluation flow enables you to create a flow that takes the outputs of previous flow runs as inputs. This flow type allows you to evaluate the performance of previous run results and output relevant metrics, facilitating the assessment and improvement of their models or applications.

    ![](./media/image-48.png)

### Task 1.2: Understand a flow
In this task, you will explore **Prompt flow**, a feature within the Azure AI Foundry.

1. A flow in Prompt flow serves as an executable workflow that streamlines the development of your LLM-based AI application. It provides a comprehensive framework for managing data flow and processing within your application.

1. Prompt flow is a feature within the Azure AI Foundry that allows you to author flows. Flows are executable workflows that often consist of three parts:

    - **Inputs**: Represent data passed into the flow. Can be of different data types, such as strings, integers, or booleans.
    - **Nodes**: Represent tools that perform data processing, task execution, or algorithmic operations.
    - **Outputs**: Represent the data produced by the flow.

      ![](./media/image-49.png)
      
1. Within a flow, nodes take center stage, representing specific tools with unique capabilities. These nodes handle data processing, task execution, and algorithmic operations, with inputs and outputs. By connecting nodes, you establish a seamless chain of operations that guides the flow of data through your application.

1. To facilitate node configuration and fine-tuning, a visual representation of the workflow structure is provided through a DAG (Directed Acyclic Graph). This graph showcases the connectivity and dependencies between nodes, providing a clear overview of the entire workflow.

### Task 1.3: Explore the tools available in prompt flow

In this task, you will explore the tools available in Prompt Flow within Azure AI Foundry.

1. Tools are the fundamental building blocks of a flow.

1. Three common tools are:

    - **LLM tool**: Enables the creation of custom prompts utilizing Large Language Models.
    - **Python tool**: Allows the execution of custom Python scripts.
    - **Prompt tool**: Prepares prompts as strings for complex scenarios or integration with other tools.

      ![](./media/image-50.png)
   
1. Each tool is an executable unit with a specific function. You can use a tool to perform tasks like summarizing text or making an API call. You can use multiple tools within one flow and use a tool multiple times.

1. One of the key benefits of Prompt flow tools is their seamless integration with third-party APIs and Python open source packages. This not only improves the functionality of large language models but also makes the development process more efficient for developers.
   
## Review
In this lab, you have completed the following tasks:
- Comprehended the Flow Development Lifecycle

### You have successfully completed the lab.
Click on **Next >>** to proceed with the next Lab.

![](./media/9-7-next.png)
