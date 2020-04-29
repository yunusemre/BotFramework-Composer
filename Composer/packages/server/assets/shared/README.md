This folder contains a Bot Project created with Bot Framework Composer.

The full documentation for Composer lives here:
https://github.com/microsoft/botframework-composer

To test this bot locally, open this folder in Composer, then click "Start Bot"

## Provision Azure Resources to Host Bot

This project includes a script that can be used to provision the resources necessary to run your bot in the Azure cloud. Running this script will create all of the necessary resources and return a publishing profile in the form of a JSON object.  This JSON object can be imported into Composer's "Publish" tab and used to deploy the bot.

* From this project folder, navigate to the scripts/ folder
* Run `npm install`
* Run `node provisionComposer.js --subscriptionId=<YOUR AZURE SUBSCRIPTION ID> --name=<NAME OF YOUR RESOURCE GROUP> --appPassword=<APP PASSWORD> --environment=<NAME FOR ENVIRONMENT DEFAULT to dev>`
* You will be asked to login to the Azure portal in your browser.
* You will see progress indicators as the provision process runs. Note that it will take roughly 10 minutes to fully provision the resources.

It will look like this:
```
{
  "publishName": "<NAME OF YOUR RESOURCE GROUP>",
  "location": "westus",
  "subscriptionID": "<YOUR SUBSCRIPTION ID>",
  "appPassword": "<YOUR APP PASSWORD>",
  "luisAuthoringRegion": "westus",
  "environment": "<ENVIRONMENT>",
  "provision": {
    "applicationInsights": {
      "InstrumentationKey": "<SOME VALUE>"
    },
    "cosmosDb": {
      "cosmosDBEndpoint": "<SOME VALUE>",
      "authKey": "<SOME VALUE>",
      "databaseId": "botstate-db",
      "collectionId": "botstate-collection",
      "containerId": "botstate-container"
    },
    "blobStorage": {
      "connectionString": "<SOME VALUE>",
      "container": "transcripts"
    },
    "luis": {
      "endpointKey": "<SOME VALUE>",
      "authoringKey": "<SOME VALUE>",
      "region": "westus"
    },
    "MicrosoftAppId": "<SOME VALUE>",
    "MicrosoftAppPassword": "<SOME VALUE>"
  },
  "accessToken": "<SOME VALUE>"
}```

When completed, you will see a message with a JSON "publishing profile" and instructions for using it in Composer.


## Publish bot to Azure

To publish your bot to a Azure resources provisioned using the process above:

* Open your bot in Composer
* Navigate to the "Publish" tab
* Select "Add new profile" from the toolbar
* In the resulting dialog box, choose "azurePublish" from the "Publish Destination Type" dropdown
* Paste in the profile you received from the provisioning script

When you are ready to publish your bot to Azure, select the newly created profile from the sidebar and click "Publish to selected profile" in the toolbar.

## Refresh your Azure Token
