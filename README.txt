READ ME 
------------------------------------------------

Step 1 
================

Before creating the Data Gen 2 Lake Storage, i created the resource group first to hold all the preceeding resources that i will be creating for the solution.After creating the resource group, Storage account follows.
Guessing, the data in storage account will be accessed frequently since the web application to be hosted for instance is Core Banking Application , Standard Type is chosen (being the best in that compare to Premium).
Replication Type determines the durability and avaiablity at all times without going down.RA-GRS was chosen as Replication type .
Name of resource group : sentia-sample-group


Other notes : 
Account Kind (StorageV2-General purpose v2) :General Purpose storage accounts provide storage for blobs,files,tables and quences in an unified account. (There is a great need for this type of storage because it will be able to handle alot of data types,files,images etc.)

Access Control (IAM) Creation : Role - Storage Blob Data Contributor is chosen because it's gives access to read,write and delete access to the Azure Storage blob containers and data.

Time Taken to finished : 10 mins


Account Kind (StorageV2-General purpose v2) :General Purpose storage accounts provide storage for blobs,files,tables and quences in an unified account. (There is a great need for this type of storage because it will be able to handle alot of data types,files,images etc.)

Access Control (IAM) Creation : Role - Storage Blob Data Contributor is chosen because it's gives access to read,write and delete access to the Azure Storage blob containers and data.

Step 2 : Key Vault Creation
=============================

Azure Key Vault enables Azure subscribers to safeguard and control cryptographic keys and other secrets used by cloud apps and services.

Specifies whether Azure Virtual Machines are permitted to retrieve certificates stored as secrets from the key vault.


Specifies whether Azure Resource Manager is permitted to retrieve secrets from the key vault.

Specifies whether Azure Disk Encryption is permitted to retrieve secrets from the vault and unwrap keys.

 Access Ploicy was created because allows you to grant permissions for a user, an app, or a security group to perform operations with this vault.

Key vault name
sentia-sample-keyvault


Time taken : 15 mins


Step 3 - Virtual Network
=================
Virtual Network Name : sentiaSampleVirtualNetwork

Address space 10.1.0.0/16 was given because wanted to get 256 subnets which will give wide range of IPs to be connected around 131,070 hosts.

Also Subnet range of 10.1.0.0/24 was given to get a host of 254 useable addresses host.	

8 mins taken for completion .

Then proceeded to creating 2 Virtual Machines to host the application on main VM and load balance the 2 VMs for availiability and excellent performance at all time.


Virtual Machine creation 
================
machine1 :  sampleVirMac1    sentiasampleuser / sentiasampleuser1!

machine2 :  sampleVirMac2    sentiasampleuser / sentiasampleuser1!


Availiabilty set : sampleAvailable1

Image : Windows Server 2016 Datacenter

Storage name : sentiastoragesample

Public IP was given so to externally access the application as well as internally.


Time taken to finish : 30 mins

Step 4 DEPLOYING THE WEB APP
==========================
First created app service (sentiasampleapp) and then used local git to pulled the source code.I pushed the sample to GitHub and then grant Azure authorization to it wanting to achieve CI/CD. 
The App Service Kudu was selected to allow automatic build my code when changes are added, wanting to adopt Continuous (CI/CD) technique.

Selected Application Insigths for monitoring the performance,network and infastrutural of the app so if anything go bad i can easily detect and fix it .

URL to link : https://sentiasampleapp.azurewebsites.net/

For the app to access Key Vault ,Identity was enabled,which enables Azure resources to Azure Key Vault without storing the credentials in the source code.

 ----I reliazed that in order to connect to the Azure Storage gen2 you will need Azure Active Directory  Web Application so i created that afterwards i couldnt connect to the Storage . -----(https://sentiasampleapp.azurewebsites.net/sentiaadapp) But it was not successful too.



Time take to finish : 45 mins




Created Git Lab : Name :sentiagitVir Username : sentiausertest  Password : Sentia1UserTest!



Step 5 Load Balancer Creation
=========================
I choose Public IP to make it accessible externally (that is via internet)



Step 6 Tags to group the resources
============================
Tags let you categorize the Azure resources according to whichever patterns make sense for your organization’s needs
You apply tags to your Azure resources giving metadata to logically organize them into a classification.After applying tags,it makes it easy to retrieve all the resources in your subscription with just the tag name and tag value.The following are the Resource Name,Name and Value Tags.

Resoure Name : sentiasampleapp (Web App - App Service)
Tag Name :sentiaapptag
Tag Value :sentia1


Resoure Name : SentiaSample-LB (Load Balancer)
Tag Name :sentialbtag
Tag Value :sentia2

Resoure Name : sampleVirMac1nsg816 (Network Security group) 
Tag Name :sentiavmtag
Tag Value :sentia3

Resoure Name : sampleVirMac1 (Virtual Machine 1) 
Tag Name :virtualMac1
Tag Value :sentia5

Resoure Name : sampleVirMac2 (Virtual Machine 2) 
Tag Name :virtualMac2
Tag Value :sentia6


Resoure Name : sentiastoragesample (Gen 2 Storage) 
Tag Name :storagetag
Tag Value :sentia7

Resoure Name : sentiastoragesample (Storage Group) 
Tag Name :storagegrouptag
Tag Value :sentia8


Resoure Name : sentia-sample-keyvault (Key Vault) 
Tag Name :keytag
Tag Value :sentia9

Resoure Name : sentia-sample-group (Resource Group) 
Tag Name :grouptag
Tag Value :sentia10


Time taken to finish : 45 mins