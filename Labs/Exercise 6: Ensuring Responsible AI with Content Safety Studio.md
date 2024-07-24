# Ensuring Responsible AI with Content Safety Studio 


The Content Safety Resource is an Azure AI service. This service consists of machine learning assisted moderation APIs which detect material that is potentially offensive, risky, or otherwise undesirable, to assure the contents in community is safe. Follow the steps below to create a Content Safety Resource.


## Task 1: Implement Content Safety Measures

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

## Task 2. 1 : Moderate image content for singular isolated images.

1. On **Azure AI | Content Safety Studio** under **Safeguard your image content with built-in-features**, select **Moderate image content**.

     ![](./media/image-11.png)


1. On **Moderate image content** select **Run a simple test** tab, review the options note we have three set content  **Safe content**, **self- harm content** and **AI-generated sexual content**.

1. Simply by selecting any of the content we can use smaple image to test.

     ![](./media/image-65.png)

1. Review the image and click on **Run test**.

     ![](./media/image-66.png)

    > **Note**: The image used for testing contains a graphic detection of a bear attack. The image will be blurred by default in the Image preview. However, you’re welcome to use the Blur image toggle to change this setting.
   
1. Review the result and in same way we can test for rest content.

   ![](./media/image-67.png)

1. Now lets use our image and test then check the result. **Moderate image content** select **Run a simple test** tab then click on **Browse for a file**

    ![](./media/image-61.png)

1. Within **file explorer** select and open **family-builds-campfire.jpg**

1. Review the image and click on **Run test**.

   ![](./media/image-68.png)
   
1. Review the result. As expected, this image content is Allowed, and the Severity level is Safe across all categories. 

   ![](./media/image-69.png)


So far, we’ve tested image content for singular isolated images. However, if we have a bulk dataset of image content, we could test the bulk dataset at once and receive metrics based on the model’s performance.

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

    - In Content Safety Studio, select Moderate text content.

1. In the Test box, enter the following:

   - I recently used the PowerBurner Camping Stove on my camping trip, and I must say, it was fantastic! It was easy to use, and the heat control was impressive. Great product!

   - Set all Threshold levels to Medium.

   - Select Run test.

   - The content is allowed, and the severity level is Safe across all categories. This was to be expected given the positive and unharmful sentiment of the customer’s feedback.

