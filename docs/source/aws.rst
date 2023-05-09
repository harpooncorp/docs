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

How to create a Amazon Web Services account and IAM user 
------------------

.. raw:: html

    <video width="320" height="240" controls>
      <source src="https://docker-desktop-screenshots.s3.us-west-2.amazonaws.com/createAwsAccountAndUser.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>

How to retrieve AWS IAM User Access keys
------------------

.. raw:: html

    <video width="320" height="240" controls>
      <source src="https://docker-desktop-screenshots.s3.us-west-2.amazonaws.com/getAccessKeys.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
