# Fine-Tuning the Model 

## Task 1: Perform Iterative Prompt Tuning and Variant Comparison 

1. On the Azure AI Studio, under Tools select Prompt flow.
1. Select **+ Create** to open the flow creation wizard.
1. In the flow gallery under Explore gallery in the "Web Classification" box select Clone.
1. Use the following prompt as a baseline prompt in the classify_with_llm node.

   ```
   Your task is to classify a given url into one of the following types:
   Movie, App, Academic, Channel, Profile, PDF or None based on the text content information.
   The classification will be based on the url, the webpage text content summary, or both.

   For a given URL : https://www.youtube.com/channel/UC_x5XG1OV2P6uZZ5FSM9Ttw, and text content: NFL Sunday Ticket is a service offered by Google LLC that allows users to watch NFL games on YouTube. It is available in 2023 and is subject to the terms and privacy policy of Google LLC. It is also subject to YouTube's terms of use and any applicable laws.
   Classify above url to complete the category and indicate evidence.

   ```

1. Select Show variants button on the top right of the LLM node. The existing LLM node is variant_0 and is the default variant.
1. Select the Clone button on variant_0 to generate variant_1, then you can configure parameters to different values or update the prompt on variant_1.
1. Repeat the step to create more variants.
1. Select Hide variants to stop adding more variants. All variants are folded. The default variant is shown for the node.

   For classify_with_llm node, based on variant_0:
      
     - Create variant_1 where the temperature is changed from 1 to 0.
     - Create variant_2 where temperature is 0 and you can use the following prompt including few-shots examples.

    Examples

      - URL: https://play.google.com/store/apps/details?id=com.spotify.music 
Text content: Spotify is a free music and podcast streaming app with millions of songs, albums, and original podcasts. It also offers audiobooks, so users can enjoy thousands of stories. It has a variety of features such as creating and sharing music playlists, discovering new music, and listening to popular and exclusive podcasts. It also has a Premium subscription option which allows users to download and listen offline, and access ad-free music. It is available on all devices and has a variety of genres and artists to choose from. 

     - URL: https://arxiv.org/abs/2303.04671 
Text content: Visual ChatGPT is a system that enables users to interact with ChatGPT by sending and receiving not only languages but also images, providing complex visual questions or visual editing instructions, and providing feedback and asking for corrected results. It incorporates different Visual Foundation Models and is publicly available. Experiments show that Visual ChatGPT opens the door to investigating the visual roles of ChatGPT with the help of Visual Foundation Models.


1. Select the Run button on the top right.
1. Select an LLM node with variants. The other LLM nodes use the default variant.
1. Submit the flow run.
1. After the flow run is completed, you can check the corresponding result for each variant.
1. Submit another flow run with the other LLM node with variants, and check the outputs.
1. You can change another input data (for example, use a Wikipedia page URL) and repeat the steps above to test variants for different data.
1. Review the output.

   ![](./media/image-34.png)
    

## Task 2: Optimize Flow Performance for Production 

No content found yet
