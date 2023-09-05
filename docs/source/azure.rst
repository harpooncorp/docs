=========================
Azure
=========================
If you want to deploy software on top of Azure, you will need to provide harpoon with a subscription ID,
tenant ID, client ID, and client secret (value). Since harpoon is deploying all of the necessary infrastructure in Azure in
addition to the Kubernetes cluster, we require fairly extensive access to the account in order to
successfully perform the provisioning of the environment. The following are the specific subscription resource providers harpoon needs
to successfully deploy a cluster:

* Microsoft.Compute
* Microsoft.Network
* Microsoft.ContainerService
* Microsoft.Resources
* Microsoft.Authorization

Also note that harpoon does provision virtual infrastructure in your Azure account, so while harpoon will
not interfere with any other virtual infrastructure in your Azure account, you could always potentially
run into hitting a resource limit that might require you to request a higher limit for a particular
resource.

How to create a Azure account and Subscription 
------------------

* Coming soon

How to retrieve Azure credentials 
------------------

* Coming soon
