===============
Troubleshooting
===============

harpoon is made to be as intuitive as possible, but sometimes there are complexities with deploying and
manipulating software in general, and these complexities can sometimes be confusing. While we endeavor to
resolve this confusion and eliminate complexity from harpoon with great resolve, the following are some
examples of common scenarios that may cause some cognitive dissonance.

Starting a cluster
------------------
After providing your cloud service provider keys and hitting the "start" button on the cloud node element,
the node will turn yellow and provide a status indicator that harpoon is working. Unfortunately, this operation
is quite complex and is configuring your cloud service provider account with numerous infrastructure components
which are being provisioned and configured in real-time. Once the infrastructure layer has been provisioned,
harpoon then deploys a Kubernetes cluster on top and dynamically configures it to work specifically with your
cloud service provider account. It may seem like harpoon is being "slow" or "unresponsive" during this time.
The truth is, it is just delivering a massive amount of value to the end user, which can take a bit of time.
We find the average time to complete a cluster deployment is about 3 minutes.

Deploying third-party container images from Docker Hub
------------------------------------------------------




Deploying third-party git repositories from GitHub
--------------------------------------------------
