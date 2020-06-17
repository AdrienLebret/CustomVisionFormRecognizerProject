# Form Recognizer & Custom Vision Project

## Table of contents // TO UPDATE

- [Table of contents // TO UPDATE](#table-of-contents----to-update)
- [Description of the project](#description-of-the-project)
- [Presentation of the Azure Cognitives Services](#presentation-of-the-azure-cognitives-services)
  * [Form Recognizer](#form-recognizer)
  * [Custom Vision](#custom-vision)
- [Tutorial](#tutorial)
  * [Use the template](#use-the-template)


## Description of the project

The main goal of this project on *Microsoft Azure* is to be able to **sort** PDF files using Custom Vision and then **extract** the desired information using Form Recognizer.

PDF file is not supported by Custom Vision, you must therefore modify them beforehand by converting them to JPEG or PNG format. I recommend to create your own conversion function with Azure Function.


## Presentation of the Azure Cognitives Services

### Form Recognizer

[Click here more information about Form Recognizer](https://docs.microsoft.com/en-us/azure/cognitive-services/form-recognizer/)

### Custom Vision

[Click here more information about Custom Vision](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/)


## Edit and deploy the template

### Use the template deployment

The Azure portal can be used to perform some basic template editing. In this quickstart, you use a portal tool called Template Deployment. Template Deployment is used in this tutorial so you can complete the whole tutorial using one interface - the Azure portal.

> Template Deployment provides an interface for testing simple templates. It is not recommended to use this feature in production. Instead, store your templates in an Azure storage account, or a source code repository like GitHub.

Azure requires that each Azure service has a unique name. The deployment could fail if you entered a storage account name that already exists. To avoid this issue, you modify the template to use a template function call uniquestring() to generate a unique storage account name.


1.From the Azure portal menu or from the **Home** page, select **Create a resource**.

2.In **Search the Marketplace**, type **template deployment**, and then press **ENTER**.

3. Select **Template deployment**.

![alt text](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/media/quickstart-create-templates-use-the-portal/azure-resource-manager-template-library.png "Template Deployment")

4. Select **Create**.

5. Select **Build your own template in the editor**.

6. Select **Load file**, and then follow the instructions to load ***template.json*** you downloaded in the last section.

7. Change the name of all the parameters

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
