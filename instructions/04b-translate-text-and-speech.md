# Explore translation

One of the driving forces that has enabled human civilization to develop is the ability to communicate with one another. In most human endeavours, communication is key.

Artificial Intelligence (AI) can help simplify communication by translating text or speech between languages, helping to remove barriers to communication across countries and cultures.

To test the capabilities of the Translator service, we'll use a simple command-line application that runs in the Cloud Shell. The same principles and functionality apply in real-world solutions, such as web sites or phone apps.

## Task-1: Create a *Cognitive Services* resource

You can use the Computer Vision service by creating either a **Translator** resource or a **Cognitive Services** resource.

If you haven't already done so, create a **Cognitive Services** resource in your Azure subscription.

1. In the Azure Portal, Click the **&#65291;Create a resource** button, search for *Cognitive Services*, and create a **Cognitive Services** resource with the following settings:
    - **Subscription**: *Retain the Existing Subscription*.
    - **Resource group**: Select **AI-900-Module-04b-<inject key="DeploymentID" enableCopy="false"/>**.
    - **Region**: *Select the same region where your resource group got deployed.*.
    - **Name**: Enter **ai900cognitive-<inject key="DeploymentID" enableCopy="false"/>**.
    - **Pricing tier**: Standard S0
    - **By checking this box I acknowledge that I have read and understood all the terms below**: Select the checkbox.
    
      ![](media/read-text-computer-vision/lab3d-1.png)
    
      ![](media/read-text-computer-vision/lab3d-2.png)
    
      ![](media/read-text-computer-vision/lab3d-3.png)
    
1. Click on **Review + Create** and Click on **Create**, and wait for deployment to complete. Then go to the deployed resource.

1. View the **Keys and Endpoint** page for your resource. You will need the **location/region** and **key** to connect from client applications.

> **Note:**
> To use the Translator service you do not need to use the Cognitive Service endpoint. A global endpoint just for the Translator service is provided. 

## Task-2: Run Cloud Shell

To test the capabilities of the Translation service, we'll use a simple command-line application that runs in the Cloud Shell on Azure. 

1. In the Azure portal, select the **[>_]** (*Cloud Shell*) button at the top of the page to the right of the search box. This opens a Cloud Shell pane at the bottom of the portal.

    ![Start Cloud Shell by clicking on the icon to the right of the top search box](media/powershell-portal-guide-1.png)

1. The first time you open the Cloud Shell, you may be prompted to choose the type of shell you want to use (*Bash* or *PowerShell*). Select **PowerShell**. If you do not see this option, skip the step.  

1. If you are prompted to create storage for your Cloud Shell, ensure your subscription is selected and click on **show advanced settings**. Please make sure you have selected your resource group **AI-900-Module-04b-<inject key="DeploymentID" enableCopy="false"/>** and enter **blob<inject key="DeploymentID" enableCopy="true"/>** for the **Storage account name** and enter **blobfileshare<inject key="DeploymentID" enableCopy="true"/>** For the **File share name**, then click on **Create Storage**.

    ![Create storage by clicking confirm.](media/translate-text-and-speech/create-a-storage.png)

1. Make sure the type of shell indicated on the top left of the Cloud Shell pane is switched to *PowerShell*. If it is *Bash*, switch to *PowerShell* by using the drop-down menu. 

    ![How to find the left hand drop down menu to switch to PowerShell](media/powershell-portal-guide-3.png) 

1. Wait for PowerShell to start. You should see the following screen in the Azure portal:  

    ![Wait for PowerShell to start.](media/powershell-prompt.png)

## Configure and run a client application

Now that you have a custom model, you can run a simple client application that uses the Translation service.

1. In the command shell, enter the following command to download the sample application and save it to a folder called ai-900.

    ```PowerShell
    git clone https://github.com/MicrosoftLearning/AI-900-AIFundamentals ai-900
    ```

1. The files are downloaded to a folder named **ai-900**. Now we want to see all of the files in your Cloud Shell storage and work with them. Type the following command into the shell: 

     ```PowerShell
    code .
    ```

    Notice how this opens up an editor like the one in the image below: 

    ![The code editor.](media/powershell-portal-guide-4.png)

1. In the **Files** pane on the left, expand **ai-900** and select **translator.ps1**. This file contains some code that uses the Translator service:

    ![The editor containing code to use the Translator service](media/translate-code-4b.png)

1. Don't worry too much about the details of the code, the important thing is that it needs the region/location and either of the keys for your Cognitive Services resource. Copy these from the **Keys and Endpoints** page for your resource from the Azure portal and paste them into the code editor, replacing the **YOUR_KEY** and **YOUR_LOCATION** placeholder values respectively.

     ![Find the key and endpoint tab in your Cognitive Services resource's left hand pane.](media/lab4b-1.png)

    After pasting the key and location values, the first lines of code should look similar to this:

    ```PowerShell
    $key="1a2b3c4d5e6f7g8h9i0j...."
    $location="somelocation"
    ```

1. At the top right of the editor pane, use the **...** button to open the menu and select **Save** to save your changes. Then open the menu again and select **Close Editor**.

    The sample client application will use the Translator service to do several tasks:
    - Translate text from English into French, Italian, and Chinese.
    - Translate audio from English into text in French

    Use the video player below to hear the input audio the application will process:

     <div class="embeddedvideo"><iframe src="https://www.microsoft.com/videoplayer/embed/RWORN0" frameborder="0" allowfullscreen="true" data-linktype="external"></iframe></div>

    > **Note**: A real application could accept the input from a microphone and send the response to a speaker, but in this simple example, we'll use pre-recorded input in an audio file.
    
1. In the Cloud Shell pane, enter the following command to run the code:

    ```PowerShell
    cd ai-900
    ./translator.ps1
    ```

1. Review the output. Did you see the translation from text in English to French, Italian, and Chinese?  Did you see the English audio "hello" translated into text in French?

## Learn more

This simple app shows only some of the capabilities of the Translator service. To learn more about what you can do with this service, see the [Translator page](https://docs.microsoft.com/azure/cognitive-services/translator/translator-overview).
