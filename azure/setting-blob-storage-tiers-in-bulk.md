# Setting Azure Blob Storage Tiers In Bulk

When dealing with storage blob backups, and even when you have [lifecycle management policies](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-lifecycle-management-concepts) defined, you sometimes still need to set the storage tier in bulk _fast_.

The fastest way I found so far is to go to the Azure Portal, open a Cloud Shell running PowerShell and using these commands:

```powershell
# Get stroage account reference
$straccount = Get-A`ureRmStorageAccount -Name <storage name> -ResourceGroupName backups

# Get all the blobs inside a container
$blobs = Get-AzureStorageBlob -Container <container name> -Context $straccount.Context

# Set tier of all the blobs to Cool
$blobs.icloudblob.setstandardblobtier("Cool") 
```

You can do the same thing in `az` (which I actually prefer), but until Azure Storage Explorer supports changing tiers in an easy, graphical way, this is still the fastest way.