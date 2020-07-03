![FR_CV_Bannière](https://user-images.githubusercontent.com/39364576/86483109-9fd9ae80-bd53-11ea-9429-a9611740324a.jpg)

# Form Recognizer & Custom Vision Project

## Table of contents

	* [Table of contents](#table-of-contents)
  * [Description of the project](#description-of-the-project)
  * [Presentation of the Azure Cognitives Services](#presentation-of-the-azure-cognitives-services)
    + [Form Recognizer](#form-recognizer)
      - [What is Form Recognizer?](#what-is-form-recognizer-)
      - [Using Form Recognizer in the project](#using-form-recognizer-in-the-project)
    + [Custom Vision](#custom-vision)
      - [What is Custom Vision?](#what-is-custom-vision-)
      - [Using Custom Vision in the project](#using-custom-vision-in-the-project)
  * [Azure Function](#azure-function)
  * [Edit and deploy the template with template deployment in less than 15 min](#edit-and-deploy-the-template-with-template-deployment-in-less-than-15-min)
  * [Any questions? Any comments?](#any-questions--any-comments-)

 

> Important information: this is my first template sharing project, thank you for your indulgence. I am open to questions, remarks and comments. I'll consider them by modifying my github.


## Description of the project

The main goal of this project on *Microsoft Azure* is to be able to **sort** PDF files using [Custom Vision](#custom-vision) and then **extract** the desired informations using [Form Recognizer](#form-recognizer).

Example: You want information from an invoice such as the invoice number, invoice amount etc... However, since there are several **types of invoices**, you have to create several Form Recognizer templates. To automate this process, you want a preliminary step to **sort** these invoices using Custom Vision.

> PDF file is not supported by Custom Vision, you must therefore modify them beforehand by converting them to JPEG or PNG format. I recommend to create your own conversion function with [Azure Function](#azure-function).

To link these 2 Cognitive Services, I used the **Logic Apps** tool that allows me to automate this process. It is this template that you will use in the chapter [Edit and deploy the template with template deployment](#edit-and-deploy-the-template-with-template-deployment).



## Presentation of the Azure Cognitives Services

### Form Recognizer

#### What is Form Recognizer?

Click [here](https://docs.microsoft.com/en-us/azure/cognitive-services/form-recognizer/) for more information about Form Recognizer

> Important, at this moment, Form Recognizer is always in ***Public Preview***

#### Using Form Recognizer in the project 

[Here](https://docs.microsoft.com/en-us/azure/cognitive-services/form-recognizer/quickstarts/label-tool) the tutorial that I used to create different models of Form Recognizer for the different type of files that you want to extract some information.
Indeed, it is important to clearly differentiate between the different types of files (e.g. invoices) so that the Cognitifi Service can extract information in the best possible way.
So, the important step when adding a new file is to sort your files with another Cognitive Service: Custom Vision


### Custom Vision

#### What is Custom Vision?

Click [here](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/) for more information about Custom Vision

#### Using Custom Vision in the project

This tool is used to sort your files before using Form Recognizer.



## Azure Function

*The Azure Function to help you to convert your PDF file to JPEG is coming soon*




## Edit and deploy the template with template deployment in less than 15 min

We talked about Azure Function (to convert your files), Custom Vision (to sort your files) and Form Recognizer (to analyze your files). To use automate all this services, I used the Logic Apps tool and I put everything in this template that I will explain how to install on the Azure Portal.

The Azure portal can be used to perform some basic template editing. In this quickstart, you use a portal tool called Template Deployment. Template Deployment is used in this tutorial so you can complete the whole tutorial using one interface - the Azure portal.

> Template Deployment provides an interface for testing simple templates. It is not recommended to use this feature in production. Instead, store your templates in an Azure storage account, or a source code repository like GitHub.

Azure requires that each Azure service has a unique name. The deployment could fail if you entered a storage account name that already exists. To avoid this issue, you modify the template to use a template function call uniquestring() to generate a unique storage account name.


1. From the Azure portal menu or from the **Home** page, select **Create a resource**.

2. In **Search the Marketplace**, type **template deployment**, and then press **ENTER**.

3. Select **Template deployment**.

![alt text](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/media/quickstart-create-templates-use-the-portal/azure-resource-manager-template-library.png "Template Deployment")

4. Select **Create**.

5. Select **Build your own template in the editor**.

6. Select **Load file**, and then follow the instructions to load ***template.json*** you downloaded in the last section.

7. Change the name of **all the parameters**

> This part is very important because at this moment all the parameters names are alredy used by me. So you will have to update the name below.

```json
"parameters": {
        "connections_plumsail_name": {
            "defaultValue": "plumsail",
            "type": "String"
        },
        "connections_azureblob_name": {
            "defaultValue": "azureblob",
            "type": "String"
        },
        "workflows_alebrelogicapp_name": {
            "defaultValue": "alebrelogicapp",
            "type": "String"
        },
        "connections_formrecognizer_name": {
            "defaultValue": "formrecognizer",
            "type": "String"
        },
        "connections_formrecognizer_1_name": {
            "defaultValue": "formrecognizer-1",
            "type": "String"
        },
        "connections_formrecognizer_2_name": {
            "defaultValue": "formrecognizer-2",
            "type": "String"
        },
        "connections_formrecognizer_3_name": {
            "defaultValue": "formrecognizer-3",
            "type": "String"
        },
        "accounts_alebrecustomvision_name": {
            "defaultValue": "alebrecustomvision",
            "type": "String"
        },
        "connections_cognitiveservicescustomvision_name": {
            "defaultValue": "cognitiveservicescustomvision",
            "type": "String"
        },
        "accounts_alebreformrecognizer_name": {
            "defaultValue": "alebreformrecognizer",
            "type": "String"
        },
        "storageAccounts_alebrestorageaccountform_name": {
            "defaultValue": "alebrestorageaccountform",
            "type": "String"
        },
        "accounts_alebrecustomvision_Prediction_name": {
            "defaultValue": "alebrecustomvision-Prediction",
            "type": "String"
        }
    }
```	

8. Select **Save**.

9. Select **Purchase**.

10. Select the bell icon (notifications) from the top of the screen to see the deployment status. You shall see **Deployment in progress**. Wait until the deployment is completed.

![alt text](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/media/quickstart-create-templates-use-the-portal/azure-resource-manager-template-tutorial-portal-notification.png "Deployment succeeded")

11. **Finish**


## Any questions? Any comments?

Send me an e-mail: adrienlebret@gmail.com
