# Evaluation Flow Setup


### Prerequisites 

Create an AI hub and project in the Azure AI Studio

Deploy a GPT model

## Task 1: Set Up Evaluation Metrics

You can manually review model responses based on test data. Manually reviewing allows you to test different inputs one at a time to evaluate whether the model performs as expected.

1. In the **Chat playground**, select **Evaluate** from the top bar.
1. A new window opens with your previous system message already populated and your deployed model selected.
1. In the **Manual evaluation result** section, you'll add five inputs for which you will review the output. Enter the following five questions as five separate **Inputs**:

   `Can you provide a list of the top-rated budget hotels in Rome?`

   `I'm looking for a vegan-friendly restaurant in New York City. Can you help?`

   `Can you suggest a 7-day itinerary for a family vacation in Orlando, Florida?`

   `Can you help me plan a surprise honeymoon trip to the Maldives?`

   `Are there any guided tours available for the Great Wall of China?`

1. Select **Run** from the top bar to generate outputs for all questions you added as inputs.
1. You can now manually review the outputs for each question by selecting the thumbs up or down icon at the bottom right of a response. Rate each response, ensuring you include at least one thumbs up and one thumbs down response in your ratings.
1. Select **Save results** from the top bar. Enter `manual_evaluation_results` as the name for the results.
1. Using the menu on the left, navigate to **Evaluations**.
1. Select the **Manual evaluations** tab to find the manual evaluations you just saved. Note that you can explore your previously created manual evaluations, continue where you left of, and save the updated evaluations.

Task 2: Run and Analyze Evaluation Flows


1. Select the **Metric evaluations** tab and create a new evaluation with the following settings:
    - **Evaluation name**: *Enter a unique name*
    - **What kind of scenario are you evaluating?**: Question and answer without context
    - **Select the data you want to evaluate**: Add your dataset
        - Download the https://raw.githubusercontent.com/MicrosoftLearning/mslearn-ai-studio/main/data/travel-qa.jsonl JSONL file and upload it to the UI.
    - **Select metrics**: Coherence, Fluency
    - **Connection**: *Your AI Services connection*
    - **Deployment name/Model**: *Your deployed GPT-3.5 model*
1. Wait for the evaluations to be completed, you may need to refresh.
1. Select the evaluation run you just created.
1. Explore the **Metric dashboard** and **Detailed metrics result**.
