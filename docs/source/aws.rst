=========================
Amazon Web Services (AWS)
=========================
If you want to deploy software on top of AWS, you will need to provide harpoon with an access key ID
and a secret access key. Since harpoon is deploying all of the necessary infrastructure in AWS in
addition to the Kubernetes cluster, we require fairly extensive access to the account in order to
successfully perform the provisioning of the environment. The following are the specific permissions harpoon needs
to successfully deploy a cluster:

* AmazonRDSFullAccess
* IAMFullAccess
* AmazonEC2FullAccess
* AmazonVPCFullAccess
* AmazonS3FullAccess
* AWSKeyManagementServicePowerUser

Also note that harpoon does provision virtual infrastructure in your AWS account, so while harpoon will
not interfere with any other virtual infrastructure in your AWS account, you could always potentially
run into hitting a resource limit that might require you to request a higher limit for a particular
resource.
