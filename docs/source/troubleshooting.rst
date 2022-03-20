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
harpoon provides dynamic deployment of over a million container images from Docker Hub, but we don't
verify or validate anything about the container images you are choosing to deploy in your Kubernetes cluster.
Your mileage may vary when it comes to successfully deploying third-party container images that you are not
personally familiar with.

Deploying third-party git repositories from GitHub
--------------------------------------------------
There are over 120 million public repositories at your fingertips to search GitHub using harpoon, but much
like third-party container images from Docker Hub, many of these repositories require special configuration
to work correctly, some of them may not compile, or have other unknown issues. Additionally, at this time,
it is a requirement for a repository to have only one Dockerfile at the top level of the repository (best practice)
in order for harpoon to be able to deploy it dynamically.

Deployment times
----------------
Many container images and git repositories deploy in only a matter of seconds using harpoon, but some can take longer.
This could be because the repository or container image is especially large, or it could be related to an issue with
the container/software itself. If some software is taking a long time to deploy and then eventually turns red, it could
be timing out after a number of failed attempts to deploy the software.
