# Lab 04: Fine-Tuning Prompts for Optimal Performance

## Lab scenario
In this hands-on lab, you will explore fine-tuning prompts for optimal performance, learning how to craft precise and effective input queries that maximize the accuracy, relevance, and efficiency of AI-generated responses. You will experiment with structuring prompts to guide AI behavior, incorporating context, constraints, and desired output formats to achieve more consistent results. By iterating on prompt design and analyzing AI responses, you will develop best practices for refining inputs to suit various use cases, from summarization and data extraction to creative writing and technical problem-solving.

## Lab Objectives
In this lab, you will perform the following:
- Task 1: Perform Iterative Prompt Tuning and Variant Comparison
- Task 2: Optimize Flow Performance for Production

### Task 1: Perform Iterative Prompt Tuning and Variant Comparison 

In this task, you will refine model responses by adjusting prompts over successive iterations. This process enables systematic evaluation and comparison of output variants, helping to ensure that each iteration leads to improved performance and more accurate, relevant responses.

1. On the [Azure AI foundry](https://ai.azure.com/?reloadCount=1), under **Build and customize** section select **Prompt flow (1)**. Select **+ Create (2)** to open the flow creation wizard.

   ![](./media/dex42.png)

1. In the **Create a new flow** under **Explore gallery** in the **Web Classification** box select **Clone**.

     ![](./media/image-35.png)

1. On the **Clone Flow** page, enter name **Web Classification-<inject key="DeploymentID" enableCopy="false"/> (1)** and click on **Clone (2)**.

      ![](./media/image-366.png)

1. Scroll down to **classify_with_llm (1)** node and select the following:

    - Connection : Select the connection **ai-modelhub<inject key="DeploymentID" enableCopy="false"/>xxxxxxxx_aoai (2)**

    - deployment_name : **gpt-4o (3)**

      ![](./media/dex43.png)

1. Replace the existing prompt with the following prompt as a baseline prompt in the classify_with_llm node **(1)**.

   ```
   # system:
   Your task is to classify a given URL into one of the following types:
   Movie, App, Academic, Channel, Profile, PDF, or None based on the text content information.
   The classification will be based on the URL, the webpage text content summary, or both.

   # user:
   For a given URL: https://www.youtube.com/channel/UC_x5XG1OV2P6uZZ5FSM9Ttw, and text content: NFL Sunday Ticket is a service offered by Google LLC that allows users to watch NFL games 
   on YouTube. It is available in 2023 and is subject to the terms and privacy policy of Google LLC. It is also subject to YouTube's terms of use and any applicable laws.
   Classify the above URL to complete the category and indicate evidence.
   
   ```

1. Select **Show variants (2)** button on the top right of the LLM node. The existing LLM node is variant_0 and is the default variant.

    ![](./media/msid-image11.png)

1. Select the **Clone** button on variant_0 to generate variant_1, then we can configure parameters to different values on variant_1

     ![](./media/gpt-4-demo21.png)
   
1. On the variant_1 replace the existing prompt with the following prompt:

    ```  
    # system:  
    Your task is to classify a given URL into one of the following types:
    Movie, App, Academic, Channel, Profile, PDF, or None based on the text content information.
    The classification will be based on the URL, the webpage text content summary, or both.

    # user:
    For a given URL: https://play.google.com/store/apps/details?id=com.spotify.music, and text content: Spotify is a free music and podcast streaming app with millions of songs, albums, 
    and original podcasts. It also offers audiobooks, so users can enjoy thousands of stories. It has a variety of features such as creating and sharing music playlists, discovering new 
    music, and listening to popular and exclusive podcasts. It also has a Premium subscription option which allows users to download and listen offline, and access ad-free music. It is 
    available on all devices and has a variety of genres and artists to choose from.
    Classify the above URL to complete the category and indicate evidence.

    ```

    ![](./media/gpt-4-demo22.png)
     
1. Select **Hide variants** to stop adding more variants. All variants are folded. The default variant is shown for the node. For classify_with_llm node, based on variant_0:

    ![](./media/dex45.png)

1. Scroll up to **summarize_text_content** node and Select the following 

     Connection : Select the connection **ai-modelhub<inject key="DeploymentID" enableCopy="false"/>xxxxxxxx_aoai (1)**

     deployment_name : **gpt-4o (2)**

1. Replace the existing prompt with the following prompt as a baseline prompt in summarize_text_content node, based on variant_0, you can create variant_1 **(3)**.  
     
   ```  
   # system:
   Please summarize the following text in one paragraph. 100 words.
   Do not add any information that is not in the text.

   # user:
   Text: The history of the internet dates back to the early 1960s, when the idea of a global network of computers was first proposed. In the late 1960s, the Advanced Research Projects 
   Agency Network (ARPANET) was developed by the United States Department of Defense. It was the first operational packet-switching network and the precursor to the modern internet. The 
   1970s and 1980s saw the development of various protocols and standards, such as TCP/IP, which allowed different networks to communicate with each other. In the 1990s, the invention 
   of the World Wide Web by Tim Berners-Lee revolutionized the internet, making it accessible to the general public. Since then, the internet has grown exponentially, becoming an 
   integral part of daily life for billions of people around the world.

   assistant:
   Summary:
   ```

1. Select **Show variants (4)** button on the top right of the LLM node. The existing LLM node is variant_0 and is the default variant.

    ![](./media/dex46.png)
   
1. Select the **Clone** button on variant_0 to generate variant_1, then we can configure parameters to different values on variant_1

1. On the **variant_1** replace the existing prompt with the following prompt:

   ```
   # system:
   Please summarize the following text in one paragraph. 100 words.
   Do not add any information that is not in the text.

   # user:
   Text: Artificial intelligence (AI) refers to the simulation of human intelligence in machines that are programmed to think and learn. AI has various applications in today's society, 
   including robotics, natural language processing, and decision-making systems. AI can be categorized into narrow AI, which is designed for specific tasks, and general AI, which can 
   perform any intellectual task that a human can. Despite its benefits, AI also poses ethical concerns, such as privacy invasion and job displacement.

   assistant:
   Summary:

   ```

    ![](./media/dex47.png)

1. Select **Save (1)** button from the top menu, and click on **Start compute session (2)**.

    ![](./media/image-87.png)

     >**Note:** It might take 10-15 minutes to start the session. Wait till compute session starts.
     
1. Select the **Run** button on the top right.

    ![](./media/webclassfication.png)
     
1. On the Submit flow run window open under **Select the LLM node with variants that you want to run** choose **Select a node to run variants** then select **summarize_text_content (1)**, and click on **Submit (2)**. 

   ![](./media/image-41.png)
   
1. Once the session runs successfully, review the output by selecting each variant.

1. In top menu select **Variant 0 (1)** from the drop down and select **view full output (2)** for **summarize_text_content** for variant 0. Now, review the output of the variant, that you selected.

   ![](./media/dex48.png)

   ![](./media/image-40.png)

    >**Note:** The output shown in the image may differ in your lab.   
  
## Task 2: Optimize Flow Performance for Production 

In this task, you will analyze and refine workflow processes to ensure maximum efficiency and minimal downtime. This includes identifying bottlenecks, applying best practices, and leveraging advanced tools and technologies to streamline operations. You will also implement continuous monitoring and iterative improvements to maintain high performance and adapt to evolving production demands, ultimately enhancing productivity and reducing operational costs.

1. Under **Inputs**, click on **+ Add input** then add **category** and **text-context**. 

    ![](./media/dex49.png)

1. Under **Output**, click on **+ Add output** then add **category** and **evidence** **(1)**. Click on **Save (2)**.

    ![](./media/dex50.png)

     >**Note:** In the Output section, if the outputs are already added, please check for the **values** and then select **Save**.
   
1. Select **Evaluate (1)** > **Custom Evaluation (2)**.

   ![](./media/evaluation(3).png)

1. On the **Batch run & Evaluate** give **Run display name** as **classify-<inject key="DeploymentID" enableCopy="false"/> (1)**, then under **Variants** select **classify_with_llm (2)**, and click on **Next (3)**.

   ![](./media/batchrun.png)

1. On the **Batch run settings** select **+ Add new data**.

   ![](./media/dex51.png)

1. On the **Add new data** window open, enter name  **classify_with_llm_data_set (1)** select **Upload from local file (2)** and click on **Browse (3)**.

   ![](./media/dex52.png)

1. Navigate to `C:\LabFiles\Developing-AI-Applications-with-Azure-AI-Studio\Labs\data` press **Enter** **(1)**, then select **classify.jsonl (2)** file and click on **Open (3)**.

     ![](./media/dex53.png)

1. Click on **Add**.

     ![](./media/dex54.png)

1.  Select **${data.text-context} (1)** for **text-context** and select **Next (2)**.

     ![](./media/dex55.png)     

1. On the **Select evaluation** page, select **Classification Accuarancy Evaluation (1)** and click on **Next (2)**.

   ![](./media/batchrunclassifiation.png)

1. On the **Configure evaluation** page, expand **Classification Accuracy Evaluation (1)** and select **classify_with_llm_data_set (2)**. For the **ground truth** data source, select **category (3)** under the **Data input**, and for **prediction**, select **category (4)** under the **Flow output**, then select **Next (5)**.

     ![](./media/dex56.png)

1. On **Review** page review the settings and click on **Submit**.

     ![](./media/dex57.png)

1. Back on Prompt flow page and from top click on **View run list** link.

    ![](./media/image-43.png)
   
1. After the batch run and evaluation run **complete**, in the run detail page, **multi-select the batch runs for each variant (1)**, then select **Visualize outputs (2)**. You will be able to see the metrics of 2 variants for the classify_with_llm node and LLM, along with predicted outputs for each recorded data.

   ![](./media/msid-image13.png)

1. After you identify which variant is the best, you can go back to the flow authoring page and set that variant as default variant of the node

1. Now will evaluate the variants of **summarize_text_content** node as well.

1. Back on the **Prompt flow** page, under the **Input** section, remove all inputs except **url**, then click on **+ Add input** and enter **Text**. 

   ![](./media/dex58.png)

1. Under the **Outputs** section, delete the existing outputs, click on **+ Add output**, then add **Summary** and set the value as **${summarize_text_content.output}**. Also, add **url** and set the value as **${inputs.url}** **(1)** and then click on **Save (2)**

   ![](./media/dex59.png)

1. Select **Evaluate (1)** > **Custom Evaluation (2)**.

   ![](./media/evaluation(3).png)

1. On the Batch run & Evaluate give **Run display name** as **summarize_text_content-<inject key="DeploymentID" enableCopy="false"/> (1)**, then under variants select **Use default variants for all nodes (2)**, and select **summarize_text_content (3)** click on **Next (4)**.

   ![](./media/summarizetextcontent.png)

1. On the Batch run settings, under **Data** enter **summarize_text_content (1)**, and then select **+ Add new data (2)**.

   ![](./media/version1.png)

1. In the new data window, enter name  **summarize_text_content_data_set (1)** select **Upload from local file (2)** and click on **browse (3)**.

   ![](./media/dex60.png)

1. Navigate to  `C:\LabFiles\Developing-AI-Applications-with-Azure-AI-Studio\Labs\data` **(1)**, then select **summarize.jsonl (2)** file  and then click on **Open (3)**.

   ![](./media/dex61.png)

1. Click on **Add**.

   ![](./media/dex62.png)

1. Under **Input mapping** for **url** select **${data.text} (1)**, and for **text** select **${data.text} (2)**. Select **Next (3)**.

   ![](./media/inputmapping.png)

1. On the **Select evaluation** page select **Classification Accuarancy Evaluation (1)** and click on **Next (2)**.

   ![](./media/classification.png)

1. On the **Configure evaluation** page, expand **Classification Accuracy Evaluation (1)**, select **summarize_text_content_data_set (2)**, and ensure that the **groundtruth** data source is set to **summary (3)** under the **Data input** section. For **prediction**, select **summary (4)** under the **Flow output**, and then click on **Review + submit (5)**.

    ![](./media/dex63.png)

1. On **Review** page review the settings and click on **Submit**.

   ![](./media/submit(1).png)

1. Back on Prompt flow page and from top click on **View run list** link.

   ![](./media/viewrunlist.png)
   
1. After the batch run and evaluation run **complete**, in the run detail page, **multi-select (1)** the batch runs for each variant, then select **Visualize outputs (2)**. You will see the metrics of 2 variants for the summarize_text_content node and LLM predicted outputs for each record of data.

   ![](./media/msid-image14.png)

1. After you identify which variant is the best, you can go back to the flow authoring page and set that variant as default variant of the node

## Review
In this lab you have completed the following tasks:
- Performed Iterative Prompt Tuning and Variant Comparison 
- Optimized Flow Performance for Production

### You have successfully completed the lab. Click on **Next >>** to procced with next exercise.
