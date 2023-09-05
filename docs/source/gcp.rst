=========================
Google Cloud Platform (GCP)
=========================
If you want to deploy software on top of GCP, you will need to provide harpoon with a credentials file
and project ID. Since harpoon is deploying all of the necessary infrastructure in GCP in
addition to the Kubernetes cluster, we require fairly extensive access to the account in order to
successfully perform the provisioning of the environment. The following are the specific project APIs harpoon needs
to successfully deploy a cluster:

* Compute Engine API
* Kubernetes Engine API

Also note that harpoon does provision virtual infrastructure in your GCP account, so while harpoon will
not interfere with any other virtual infrastructure in your GCP account, you could always potentially
run into hitting a resource limit that might require you to request a higher limit for a particular
resource.

How to create a Google Cloud Platform account and project 
------------------

* Coming soon

How to retrieve GCP credentials file
------------------

* Coming soon
