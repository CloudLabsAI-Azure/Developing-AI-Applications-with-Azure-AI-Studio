# Fine-Tuning the Model 

## Task 1: Perform Iterative Prompt Tuning and Variant Comparison 

1. Open the sample flow and remove the prepare_examples node as a start.
1. Under Tools select Prompt flow.
1. Select Create to open the flow creation wizard.
1. In the flow gallery under Explore gallery in the "Web Classification" box select Clone.
1. Use the following prompt as a baseline prompt in the classify_with_llm node.

   ```
   Your task is to classify a given url into one of the following types:
   Movie, App, Academic, Channel, Profile, PDF or None based on the text content information.
   The classification will be based on the url, the webpage text content summary, or both.

   For a given URL : https://www.youtube.com/channel/UC_x5XG1OV2P6uZZ5FSM9Ttw, and text content: NFL Sunday Ticket is a service offered by Google LLC that allows users to watch NFL games on YouTube. It is available in 2023 and is subject to the terms and privacy policy of Google LLC. It is also subject to YouTube's terms of use and any applicable laws.
   Classify above url to complete the category and indicate evidence.

   ```

1. Review the output.

   ![](./media/image-34.png)
    
## Deploy the finetuned model

When finetuning has successfully completed, you can deploy the model.

1. Select the finetuned model. Select the **Metrics** tab and explore the finetune metrics.
1. Deploy the finetuned model with the following configurations:
    - **Deployment name**: *A unique name for your model, you can use the default*
    - **Deployment type**: Standard
    - **Tokens per Minute Rate Limit (thousands)**: 5K
    - **Content filter**: Default

## Task 2: Optimize Flow Performance for Production 

## Test the finetuned model

Now that you deployed your finetuned model, you can test the model like you can test any other deployed model.

1. When the deployment is ready, navigate to the finetuned model and select **Open in playground**.
1. In the chat window, enter the query `What can you do?`
    Notice that even though you didn't specify the system message to instruct your model to answer travel-related questions, the model already understands what it should focus on.
1. Try with another query like `Where should I go on holiday for my 30th birthday?`
