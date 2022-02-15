# EventhubADXCustomProps

Azure function to read data from Azure Function, retrieve data from both body and propperties.

A [Service Principal](https://docs.microsoft.com/en-us/azure/data-explorer/provision-azure-ad-app) is needed for the SDK to authenticate towards the cluster
and the SP need the "ingestors" access on the Database:

```
.add database DatabaseName ingestors ('aadapp=<appID>;<SubscriptionID>');
```

Fuction need OS enviroment variables, for testing these data can be provided in a local.settings.json in the root of the project.
```
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "python",
    "kaareseraseventhubcustomprops_test_EVENTHUB": "Endpoint=sb://xxxxxxxxxxxxx.servicebus.windows.net/;SharedAccessKeyName=yyyyyyy;SharedAccessKey=kkkkkkkkkkkkkkkk=;EntityPath=ccccc",
    "cluster_ingest_uri":  "Ingest URI of Cluster",
    "database": "Database name in cluster",
    "table": "Tablename in Database",
    "client_id": "Service principal ID",
    "client_secret": "Secrect Value",
    "tenant_id": "Teanat/Subscription ID",
    "ingestion_mapping_reference": "Refrence to mapping on table in ADX cluster"
  }
}
```
