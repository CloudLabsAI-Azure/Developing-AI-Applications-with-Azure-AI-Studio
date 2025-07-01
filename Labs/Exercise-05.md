# Lab 05: Implementing Chat Flow and Tool Integration

## Estimated Duration: 60 minutes

## Lab Overview
In this lab, you will be designing and implementing a chat flow to interact with a deployed language model. You'll start by creating a basic chat flow using Azure AI foundry, which includes integrating inputs, an LLM node, and configuring the output to reflect chat responses. You will then test the chat flow, ensure it functions correctly, and deploy it to a production environment. The final steps involve verifying the deployment, testing the deployed flow with sample queries, and exploring options for integrating the chat flow into applications as a custom copilot.

## Lab Objectives
In this lab, you will perform the following:
- Task 1: Design and Implement a Chat Flow
- Task 2: Use LLM and Prompt Tools in Flows

## Task 1: Design and Implement a Chat Flow

In this task, you will design and implement a chat flow using Azure AI Foundry to interact with a deployed language model. You will test its functionality to ensure accurate and relevant responses, and prepare the chat flow for deployment in a production environment.

1. From the left navigation menu, under **My assets**, select **Model + endpoints (1)**.

1. On the **Manage deployments of your models, apps, and services**, under **Model deployments** tab, select **+ Deploy model (2)** and then select **Deploy base model (3)** from the dropdown.

   ![](./media/DAI-image2-1.png)

1. On the **Select a model** page, search for **gpt-35-turbo (1)**, select **gpt-35-turbo (2)**, select **Confirm (3)** under the **gpt-35-turbo**.

   ![](./media/model-1.png)

1. On **Deploy model gpt-35-turbo**, click on **Customize**.

   ![](./media/customize.png)

1. On **Deploy model gpt-35-turbo** follow these instructions to create the deployment:
   
   - Deployment Name : **gpt-35-turbo (1)**
   - Deployment type: **Standard (2)**
   - Model version: **0125 (Default) (3)**
   - Connected AI resource: select the resource which we created in earlier task **(4)**
   - Tokens per Minute Rate Limit: **10K (5)**
   - Content filter: **DefaultV2 (6)**
   - Enable dynamic quota: **Enabled (7)**
   - Select **Deploy (8)**

     ![](./media/l5.task1.1.png)
     
1. On the [Azure AI foundry](https://ai.azure.com/?tid=f9733b59-6ed1-4cb1-a5c4-55f5c0d6ad6f), under **My assets**, select **Model + endpoints (1)**. On the **Model + deployments** page select **gpt-35-turbo (2)** then click **Open in playground (3)**

    ![](./media/playground-1.png)

1. In the chat window, enter the query **What can you do?**.

   >**Note:** The answer is generic because there are no specific instructions for the assistant. To make it focused on a task, you can change the system prompt.
   > Wait for 2-3 mins if you get an error while querying.
   
     ![](./media/chatwindow.png)

   >**Note:** The output will be different; it will not be the same. However, it will look similar to the screenshot.

1. Update the **Give the model instructions and context (1)** to the following:-

   ```
   **Objective**: Assist users with travel-related inquiries, offering tips, advice, and recommendations as a knowledgeable travel agent.

   **Capabilities**:
   - Provide up-to-date travel information, including destinations, accommodations, transportation, and local attractions.
   - Offer personalized travel suggestions based on user preferences, budget, and travel dates.
   - Share tips on packing, safety, and navigating travel disruptions.
   - Help with itinerary planning, including optimal routes and must-see landmarks.
   - Answer common travel questions and provide solutions to potential travel issues.
    
   **Instructions**:
   1. Engage with the user in a friendly and professional manner, as a travel agent would.
   2. Use available resources to provide accurate and relevant travel information.
   3. Tailor responses to the user's specific travel needs and interests.
   4. Ensure recommendations are practical and consider the user's safety and comfort.
   5. Encourage the user to ask follow-up questions for further assistance.

   ```
   
1. Select **Apply changes (2)** and when **Update system message?** pop-up appears, click on **Continue**.

     ![](./media/d33.png)   

1. In the chat window, enter the same query as before: **What can you do?**. Note the change in response.

     ![](./media/changes.png)

     >**Note:** The output will be different; it will not be the same. However, it will look similar to the screenshot.

1. From the left navigation pane, select **Prompt flow (1) > + Create (2)** to add the Prompt tool to your flow.

   ![](./media/prompt_flow1.png)

1. On **Create a new flow** blade, under **Chat flow**, click on **Create (1)**, then enter **Travel-Chat (2)** for Folder name, then click on **Create (3)** 

   ![](./media/1dex4.png)

1. A simple chat flow is created for you. Note there are two inputs (**chat history and the user’s question**) **(1)**, an LLM node that will connect with your deployed language model, and an output to reflect the response in the chat **(2)**.

   ![](./media/1dex8.png)

1. To be able to test your flow, you need compute. Select **Start compute session** from the top bar.

   ![](./media/startcompute-1.png)
   
   >**Note:** The compute session will take 1-3 minutes to start.
   
1. Select the LLM node named **chat**. Update the system message like below:

   ```
   system:
   **Objective**: Assist users with travel-related inquiries, offering tips, advice, and recommendations as a knowledgeable travel agent.
   
   **Capabilities**:
   - Provide up-to-date travel information, including destinations, accommodations, transportation, and local attractions.
   - Offer personalized travel suggestions based on user preferences, budget, and travel dates.
   - Share tips on packing, safety, and navigating travel disruptions.
   - Help with itinerary planning, including optimal routes and must-see landmarks.
   - Answer common travel questions and provide solutions to potential travel issues.
   
   **Instructions**:
   1. Engage with the user in a friendly and professional manner, as a travel agent would.
   2. Use available resources to provide accurate and relevant travel information.
   3. Tailor responses to the user's specific travel needs and interests.
   4. Ensure recommendations are practical and consider the user's safety and comfort.
   5. Encourage the user to ask follow-up questions for further assistance.
   
   {% for item in chat_history %}
   user:
   {{item.inputs.question}}
   assistant:
   {{item.outputs.answer}}
   {% endfor %}
   
   user:
   {{question}}
   ```

   ![](./media/chatllm-1.png)

1. Select **Save**.

   ![](./media/1dex10.png)

1. You still need to connect the LLM node to your deployed model. In the top of the**LLM node** section, you need to select the connection from the drop down list and proceed as below.

   - **Connection**: Select the connection that was newly created for you when you created the **gpt-35-turbo** **(1)** deployment. 
   - **Api**: Select **chat (2)**.
   - **deployment_name**: Select the **gpt-35-turbo (3)** model you deployed.
   - **response_format**: Select **{“type”:”text”} (4)**.

     ![](./media/gpt-35-turbo-deplyment.png)
   
## Task 2: Use LLM and Prompt Tools in Flows

In this task, you will use the chat window to test the developed flow by leveraging built-in LLM and prompt tools within Azure AI Foundry. This will help you validate the flow's behavior, experiment with prompt tuning, and ensure the language model responds accurately within the defined interaction patterns.

1. Ensure the compute session is running. Select **Save (1)**. Select **Chat (2)** to test the flow.

   ![](./media/chatflow-1.png)

1. Enter the query: **I have one day in London, what should I do?** and review the output.

   ![](./media/d37.png)

   >**Note:** The output will be different; it will not be the same. However, it will look similar to the screenshot.

1. Select **Deploy** to deploy the flow with the following settings:

   ![](./media/deploy.png)
   
   - Basic settings:
     - Endpoint: **New (1)**
     - Endpoint name: **modelendpoint-<inject key="DeploymentID" enableCopy="false"/> (2)**
     - Deployment name: **modeldeploy-<inject key="DeploymentID" enableCopy="false"/> (3)**
     - Virtual machine: **Standard_DS3_v2 (4)**
     - Instance count: **3 (5)**
     - Inferencing data collection: **Enabled (6)**
     - Select **Review + Create (7)**

         ![](./media/1dex14.png)

1. Review the configurations and then select **Create**.

   ![](./media/1dex15.png)

1. In Azure AI foundry, from the left navigation pane, under **My assets**, select **Model + endpoints**

   >**Note:** Select **Save** if your flow is not saved.

1. Select the **Model deployments (1)** tab to find your deployed flow. It may take some time before the deployment is listed and successfully created. When the deployment has succeeded, select the newly created deployment **(2)**.

   ![](./media/1dex16.png)

   > **Note:** It might take 3-5 minutes to deploy.

1. Wait untill the **Provisioning state** become **Succeeded (1)**, then only you will get the **Test (2)** tab.

   ![](./media/d39.png)

1. Navigate to **Test** tab, enter the prompt **What is there to do in San Francisco?** in the input question (string) section and review the response.

     ![](./media/testdeploy-1.png)

     >**Note:** If the **Test** tab is not opening, wait for 3-5 minutes, refresh the page and try again. 

     >**Note:** The output will be different; it will not be the same. However, it will look similar to the screenshot.

1. Enter the prompt **Where else could I go?** and review the response.

     ![](./media/image-33-1.png)

     >**Note:** The output will be different; it will not be the same. However, it will look similar to the screenshot.

1. View the **Consume** page for the endpoint, and note that it contains connection information and sample code that you can use to build a client application for your endpoint - enabling you to integrate the prompt flow solution into an application as a custom copilot.

   ![](./media/modelendpoints-1.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task.
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.
<validation step="157c6872-a66d-4125-babc-7975ad31603b" />

## Review
In this lab you have completed the following tasks:
- Designed and Implement a Chat Flow
- Used LLM and Prompt Tools in Flows

### You have successfully completed the lab. Click on **Next >>** to procced with next exercise.
