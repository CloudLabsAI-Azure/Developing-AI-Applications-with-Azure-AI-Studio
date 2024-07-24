# Ensuring Responsible AI with Content Safety Studio 


The Content Safety Resource is an Azure AI service. This service consists of machine learning assisted moderation APIs which detect material that is potentially offensive, risky, or otherwise undesirable, to assure the contents in community is safe. Follow the steps below to create a Content Safety Resource.


## Task 1: Implement Content Safety Measures

Content Safety resource in Azure to detect and manage harmful content. You'll create and configure the resource, assign the necessary roles, and ensure it's integrated with the Content Safety Studio. This setup allows you to use Azure’s AI tools to moderate content effectively.

1. Open a new tab, and navigate to the [Content Safety Studio](https://contentsafety.cognitive.azure.com/), select the **Settings** icon in the top navigation menu.

   ![](./media/image-51.png)

1. In the All resources section, select **+ Create a new resource**.

    ![](./media/image-52.png)

1. You will be directed to the **Azure portal**, and on the **Create Content Safety** page, specify the following and click on **Review + Create**.

   - Subscription – select your **Azure subscription**

   - Resource group – select the Resource Group **ODL-MEMT-<inject key="DeploymentID" enableCopy="false"/>**
  
   - Region – **East US**

   - Name – **Content-Safety-<inject key="DeploymentID" enableCopy="false"/>**

   - Pricing tier – Free

     ![](./media/image-53.png)

1. Review the settings and click **Create**.

     ![](./media/image-54.png)

1. Once deployement is successful click on **Go to resource**.

    ![](./media/image-57.png)

1. On **Content-Safety-<inject key="DeploymentID" enableCopy="false"/>** page from the left navigation pane, select  **Access Control (IAM) (1)** > **+ Add (2)** then choose **Add Role assignment (3)**

   ![](./media/image-58.png)

1. On **Add role assignment** page search and select  **Cognitive Services User** then click on **Next**.

1. On **Member** tab, make sure **User, group, or service principal** is selected then click on **+ Select members**  and search  then click **Select** 

1. Click on **Next** > **Review + assign**.

1. Back on **Content-Safety-<inject key="DeploymentID" enableCopy="false"/>** page,  from the left navigation pane, select  **Overview** and review the settings then click on Content Safety Studio link.

     ![](./media/image-59.png)
   
1. Your navigated to the [Content Safety Studio](https://contentsafety.cognitive.azure.com/), select the **Settings** icon in the top navigation menu.

    ![](./media/image-51.png)

1. Make sure Content Safety resources is created.

      ![](./media/image-55.png)

1. Select **Content-Safety-<inject key="DeploymentID" enableCopy="false"/>** and click on **Use resource**.

     ![](./media/image-(60).png)
   
## Task 2: Monitor and Analyze Content for Compliance

In this task, you will implement and evaluate content moderation for both images and text using Azure's Content Safety Studio. The goal is to ensure that content uploaded by users complies with safety standards by testing for harmful content and analyzing moderation results.

## Task 2. 1 : Moderate image content for singular isolated images.

1. On **Azure AI | Content Safety Studio** under **Safeguard your image content with built-in-features**, select **Moderate image content**.

     ![](./media/image-11.png)


1. On **Moderate image content** select **Run a simple test** tab, review the options note we have three set content  **Safe content**, **self- harm content** and **AI-generated sexual content**.

1. Safe content

1. Now lets use our image and test then check the result. **Moderate image content** select **Run a simple test** tab then click on **Browse for a file**

    ![](./media/image-61.png)

1. Within **file explorer** select and open **family-builds-campfire.jpg**

1. Review the image and click on **Run test**.

   ![](./media/image-68.png)
   
1. Review the result. As expected, this image content is Allowed, and the Severity level is Safe across all categories. 

   ![](./media/image-69.png)

   >**Note**: So far, we’ve tested image content for singular isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics based on the model’s performance.

1. Violent content

    We should also anticipate customers potentially posting harmful image content. To ensure that we account for such a scenario, let’s test the detection of harmful image content.

1. Select Browse for a file and upload the bear-attack-blood.JPG file.

1. Set all Threshold levels to Medium.
1. Select Run test.

   >**Note**: Rightfully so, the content is Blocked, and was rejected by the Violence filter which has a Severity level of High.

### Task 2. 2: Run a bulk test

So far, we’ve tested image content for singular isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics based on the model’s performance.

1. On **Moderate image content** select **Run a bulk test** tab then click on **Browse for a file**.

     ![](./media/image-12.png)

1. Within file explorer select and open **image_sample_dataset.zip**.

     ![](./media/image-13.png)

1. Under Test section review **Dataset preview** then select **Configure filters** tab review **Category** and **Threshold level** then click on **Run test**.

     ![](./media/image-14.png)

1. Review the result.

   ![](./media/image-15.png)

   ![](./media/image-16.png)

### Task 2.3 : Text moderation using Moderate text content 

We could leverage an AI model to detect whether the text input from our customers is harmful and later use the detection results to implement the necessary precautions.

1. Safe content

    - Let’s first test some positive customer feedback.

    - In Content Safety Studio, select **Moderate text content**.

       ![](./media/image-70.png)

    - On the **Moderate text content** page, select **Run a simple test** and choose **Safe content** under s**elect a sample or type your own** section.

        ![](./media/image-71.png)

1. In the Test box, enter the following:

     - I recently used the PowerBurner Camping Stove on my camping trip, and I must say, it was fantastic! It was easy to use, and the heat control was impressive. Great product!

     - Set all Threshold levels to Medium.

     - Select Run test.

       ![](./media/image-72.png)
     
1. Review the result.

   ![](./media/image-73.png)

    - The content is allowed, and the severity level is Safe across all categories. This was to be expected given the positive and unharmful sentiment of the customer’s feedback.


1. Harmful content

   But what would happen if we tested a harmful statement? Let’s test with negative customer feedback. While it's OK to dislike a product, we don't want to condone any name calling or 
   degrading statements.

1. In the Test box, enter the following:

    - I recently bought a tent, and I have to say, I'm really disappointed. The tent poles seem flimsy, and the zippers are constantly getting stuck. It's not what I expected from a high-end tent. You all suck and are a sorry excuse for a brand.

   - Set all Threshold levels to Medium.

   - Select Run test.

      ![](./media/image-75.png)
 
   - Although the content is Allowed, the Severity level for Hate is low. To guide our model to block such content, we’d need to adjust the Threshold level for Hate. A lower Threshold level would block any content that’s a low, medium, or high severity. There’s no room for exceptions!

   - Set the Threshold level for Hate to Low.

   - Select Run test.

     ![](./media/image-76.png)
    
   - The content is now Blocked and was rejected by the filter in the Hate category.

      ![](./media/image-77.png)

1. Violent content with misspelling

   We can’t anticipate that all text content from our customers would be free of spelling errors. Fortunately, the Moderate text content tool can detect harmful content even if the content has spelling errors. Let’s test this capability on additional customer feedback about an incident with a racoon.

1. Select Violent content with misspelling

    ![](./media/image-74.png)

1. In the Test box, enter the following:

    - I recently purchased a campin cooker, but we had an acident. A racon got inside, was shocked, and died. Its blood is all over the interior. How do I clean the cooker?

    - Set all Threshold levels to Medium.

    - Select Run test.

    - Although the content is Allowed, the Severity level for Violence is should be Low. You could adjust the Threshold level for Violence to try and block such content, however, should we? Consider a scenario where the customer is asking this question in a conversation with the AI-powered customer support agent in hopes of receiving guidance on how to clean the cooker. There may be no ill-intent in submitting this question and therefore, it may be a better choice not to block such content. As the developer, consider various scenarios where such content may be OK before deciding to adjust the filter and block similar content.
  
1. Run a bulk test

  - So far, we’ve tested image content for singular isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics 
     based on the model’s performance.

  - We have a bulk dataset of images provided by customers. The dataset also includes sample harmful images to test the model’s ability to detect harmful content. Each record in the 
    dataset includes a label to indicate whether the content is harmful. Let’s do another test round but this time with the data set!

1. Switch to the Run a bulk test tab.

1. Select Browse for a file and upload the **bulk-image-moderation-dataset.csv** file.

1. In the Dataset preview section, browse through the Records and their corresponding Label. A 0 indicates that the content is acceptable (not harmful). A 1 indicates that the content is unacceptable (harmful content).

1. Set all Threshold levels to Medium.

1. Select Run test.
   
    ![](./media/image-78.png)

1. Review the result.

    ![](./media/image-79.png)

    ![](./media/image-80.png)
   

