# Fine-Tuning the Model 

## Task 1: Perform Iterative Prompt Tuning and Variant Comparison 


## Finetune a GPT-3.5 model

Before you can finetune a model, you need a dataset.

1. Save the training dataset as JSONL file locally: https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-studio/main/data/travel-finetune.jsonl
1. Navigate to the **Model catalog** page under the **Get started** section, using the menu on the left.
1. Search for and select the `gpt-35-turbo` model, don't deploy the model yet!
1. From the model overview, **Finetune** the model using the following configuration:
    - **Model version**: *Select the default version*
    - **Model suffix**: `ft-travel`
    - **Azure OpenAI connection**: *Select the connection that was created when you created your hub*
    - **Training data**: Upload files
    - **Upload file**: Select the JSONL file you downloaded in a previous step.
    - **Validation data**: None
    - **Task parameters**: *Keep the default settings*
1. Finetuning will start and may take some time to complete.

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
