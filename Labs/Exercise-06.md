# Lab 06: Ensuring Responsible AI with Content Safety Studio 

## Lab Scenario
In this lab, you will learn about the Content Safety Studio, a powerful tool for managing user-generated content. It features Text Moderation to detect and filter harmful text, such as hate speech and violence, and Image Moderation to analyze and block unsafe or offensive images. This comprehensive solution ensures that all user contributions are safe and appropriate across platforms.

## Lab Objectives

In this lab, you will perform the following tasks:

- **Task 1:** Implement Content Safety Measures
- **Task 2:** Monitor and Analyze Content for Compliance
  
## Task 1: Implement Content Safety Measures

Content Safety resource in Azure to detect and manage harmful content. You will create and configure the resource, assign the necessary roles, and ensure it's integrated with the Content Safety Studio. This setup allows you to use Azure’s AI tools to moderate content effectively.

1.  Open a new tab and navigate to the [Azure AI | Content Safety Studio](https://contentsafety.cognitive.azure.com/) page. If you are not logged in, click on the **Sign in** option from the top right corner and select the **user**. Then click on the **Settings** icon in the top navigation menu.

     ![](./media/image-51.png)

1. In the **Resource** section, select **+ Create a new resource**.

     ![](./media/image-52.png)

1. You will be directed to the **Azure portal**. Specify the following on the **Create Content Safety** page and click on **Review + create (6)**.

     - Subscription: Select your **Azure subscription (1)**.
  
     - Resource group: Select the Resource Group **ODL-MEMT-<inject key="DeploymentID" enableCopy="false"/> (2)**
    
     - Region: **East US (3)**
  
     - Name: **Content-Safety-<inject key="DeploymentID" enableCopy="false"/> (4)**
  
     - Pricing tier: Free **(5)**
  
       ![](./media/image-53.png)

1. Review the settings and click on **Create**.

     ![](./media/image-54.png)

1. Once deployment is successful, click on **Go to resource**.

     ![](./media/image-57.png)

1. Back on the **Content-Safety-<inject key="DeploymentID" enableCopy="false"/>** page,  from the left navigation pane, select **Overview (1)** and review the settings. Then click on the **Content Safety Studio (2)** link.

      ![](./media/image-59.png)
   
1. You will be navigated to the [Azure AI | Content Safety Studio](https://contentsafety.cognitive.azure.com/) page. Select the **Settings** icon located in the top navigation menu.

     ![](./media/image-51.png)

1. Make sure the **Content Safety resources** are created.

      ![](./media/image-55.png)

1. Select **Content-Safety-<inject key="DeploymentID" enableCopy="false"/> (1)** and click on **Use resource (2)**.

     ![](./media/image-(60).png)

> **Congratulations** on completing the task! Now, it is time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at **labs-support@spektrasystems.com**. We are available 24/7 to help you out.
<validation step="a76d4e32-03f7-494b-9427-63f1702eff54" />
   
## Task 2: Monitor and Analyze Content for Compliance

In this task, you will implement and evaluate content moderation for both images and text using Azure's Content Safety Studio. The goal is to ensure that content uploaded by users complies with safety standards by testing for harmful content and analyzing moderation results.

## Task 2. 1: Moderate image content for singular isolated images.

1. On the **Azure AI | Content Safety Studio** page, select **Moderate image content** under **Safeguard your image content with built-in features**.

     ![](./media/image-11.png)

1. On the **Moderate image content** page, click on the **Run a simple test** tab and review the options. Note we have three sets of content. **Safe content**, **self-harm content**, and **AI-generated sexual content**.

#### Safe content

1. Now let's use our image and then check the result. In the **Moderate image content** page, click on the **Browse for a file (1)** option and then choose **Safe content (2)** under the **Run a simple test** tab. 

     ![](./media/image-61.png)

1. Within **file explorer**, navigate to **C:\LabFiles\Model-Evaluation-and-Model-Tunning\Labs\data\image_sample_dataset**. Then select and open **family-builds-campfire.jpg**.

1. Review the image and click on **Run test**.

    ![](./media/image-68.png)
   
1. Review the result. As expected, this image content is **Allowed**, and the **Severity level** is **Safe** across all categories. 

    ![](./media/image-69.png)

   >**Note**: So far, we have tested image content for singular isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics based on the model’s performance.

#### Self-harmed content

We should also anticipate customers potentially posting harmful image content. To ensure that we account for such a scenario, let’s test the detection of harmful image content.

1. Select **Browse for a file** and upload the **bear-attack-blood.JPG** file.
1. Set all **threshold levels** to **Medium**.
1. Select **Run test**.

    >**Note**: Rightfully so, the content is blocked and was rejected by the **Violence** filter, which has a **Severity level** of **High**.

### Task 2.2: Run a bulk test

So far, we have tested image content for singular, isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics based on the model’s performance.

1. On the **Moderate image content** page, click on the **Run a bulk test (1)** tab and then choose **Browse for a file (2)**.

     ![](./media/image-12.png)

1. Within **file explorer**, navigate to **C:\LabFiles\Model-Evaluation-and-Model-Tunning\Labs\data\image_sample_dataset**. **Select (1)** and **open (2)** the **image_sample_dataset.zip** folder.

    ![](./media/image-81.png)
   
1. Under the **Test** section, review the **Dataset preview (4 records) (1)**. Moving on, review **Category** and **Threshold level** options under the **Configure filters (2)** tab. Finally, click on **Run test (3)**.

     ![](./media/image-14.png)

1. Review the result.

   ![](./media/image-15.png)

   ![](./media/image-16.png)

### Task 2.3: Text moderation using moderate text content 

We could leverage an AI model to detect whether the text input from our customers is harmful and later use the detection results to implement the necessary precautions.

#### Safe content

Let us first test some positive customer feedback.

1. In the **Azure AI | Content Safety Studio** page, select **Moderate text content**.

   ![](./media/image-70.png)

1. On the **Moderate text content** page, select **Run a simple test (1)** and choose **Safe content (2)** under the **Select a sample or type your own** section.

   ![](./media/image-71.png)

1. In the **Test box (1)**, enter the following:

     - I recently used the PowerBurner Camping Stove on my camping trip, and I must say, it was fantastic! It was easy to use, and the heat control was impressive. Great product!

     - Set all **Threshold** levels to **Medium (2)**.

     - Select **Run test (3)**.

       ![](./media/image-72.png)
     
1. Review the result.

    ![](./media/image-73.png)

    >**Note**: The content is Allowed, and the Severity Level is Safe across all categories. This was to be expected given the positive and unharmful sentiment of the customer’s feedback.


#### Harmful content

But what would happen if we tested a harmful statement? Let's test with negative customer feedback. While it is OK to dislike a product, we don't want to condone any name-calling or degrading statements.

1. In the **Test box (1)**, enter the following:

    - I recently bought a tent, and I have to say, I'm really disappointed. The tent poles seem flimsy, and the zippers are constantly getting stuck. It's not what I expected from a 
       high-end tent. You all suck and are a sorry excuse for a brand.

    - Set all **Threshold levels** to **Medium (2)**.

    - Select **Run test (3)**.

      ![](./media/image-75.png)
 
   - Although the content is allowed, the Severity level for hate is low. To guide our model to block such content, we would need to adjust the **Threshold level** for **Hate**. A lower Threshold level would block any content that is low, medium, or high severity. There’s no room for exceptions!

   - Set the **Threshold level** for **Hate** to **Low (2)**.

   - Select **Run test (3)**.

     ![](./media/image-76.png)
    
   - The content is now **Blocked** and was rejected by the filter in the **Hate** category.

      ![](./media/image-77.png)

#### Violent content with misspelling

We cannot anticipate that all text content from our customers would be free of spelling errors. Fortunately, the Moderate text content tool can detect harmful content even if the content has spelling errors. Let’s test this capability on additional customer feedback about an incident with a racoon.

1. Select **Violent content with misspelling**.

    ![](./media/image-74.png)

1. In the **Test box (1)**, enter the following:

    - I recently purchased a campin cooker, but we had an accident. A racon got inside, was shocked, and died. Its blood is all over the interior. How do I clean the cooker?

    - Set all **Threshold levels** to **Medium (2)**.

    - Select **Run test (3)**.

    - Although the content is allowed, the severity level for violence should be Low. You could adjust the Threshold level for Violence to try and block such content. However, should we? Consider a scenario where the customer is asking this question in a conversation with the AI-powered customer support agent in hopes of receiving guidance on how to clean the cooker. There may be no ill intent in submitting this question, and therefore, it may be a better choice not to block such content. As the developer, consider various scenarios where such content may be OK before deciding to adjust the filter and block similar content.
  
#### Run a bulk test
So far, we have tested image content for singular, isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics 
based on the model’s performance.

We have a bulk dataset of images provided by customers. The dataset also includes sample harmful images to test the model’s ability to detect harmful content. Each record in the 
dataset includes a label to indicate whether the content is harmful. Let’s do another test round, but this time with the data set!

1. Switch to the **Run a bulk test** tab.

1. Select **Browse for a file**, and within **file explorer** navigate to **C:\LabFiles\Model-Evaluation-and-Model-Tunning\Labs\data\image_sample_dataset**. **Select (1)** and **upload (2)** **bulk-image-moderation-dataset.csv** file.

     ![](./media/image-82.png)
     
1. In the **Dataset preview** section, browse through the **Records** and their corresponding **labels**. A 0 indicates that the content is acceptable (not harmful). A 1 indicates that the content is unacceptable (harmful 
   content).

1. Set all **Threshold levels** to **Medium**.

1. Select **Run test**.
   
    ![](./media/image-78.png)

1. Review the result.

    ![](./media/image-79.png)

    ![](./media/image-80.png)

## Review

In this lab, you have completed the following tasks:

- Implemented content safety measures.
- Monitor and analyze content for compliance.

### You have successfully completed the lab. Click on **Next >>** to proceed with the next exercise.
