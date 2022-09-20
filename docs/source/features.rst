========
Features
========

.. _elements:

Elements
========
Every element depicted below has a visual representation of what state the element is in, excluding the link
elements and log elements. Translucent represents the element has no state and is waiting to be activated.
Yellow represents the element that is in the process of being deployed. Blue represents a successful deployment
and is running successfully. Red represents a failed deployment and error state.

Node Element
------------
The node element is a visual representation of a virtual machine running inside a user's cloud
service provider account. Multiple nodes represent a cluster. The cluster can be scaled up by dragging out more
available nodes if the user has any available. Starting the cluster with the play button will initiate terraform
scripts that will build a given cluster in the users chosen cloud service provider, or on-prem environment.
Stopping the cluster with the power button will initiate terraform scripts that will tear down the given cluster
and any resources associated with it. Up to 3 elements may be attached to a given node at one time. The frontend
calls a backend service which contains the underlying logic required to execute and fulfill the requests input by
the user. The node element is mapped to a set of machines that represent a Kubernetes cluster. The backend service
manages these machines, and their supporting infrastructure,using Hashicorp Terraform. The backend service dynamically
generates the required inputs for terraform based on the requested state from the user. These inputs are injected
into the Terraform execution environment using environment variables. The backend service then executes Terraform
within this environment by copying the generated terraform files into a temporary directory, injecting the saved
state for Terraform, setting up the environment variables, and executing Terraform. The backend service then
captures all output from Terraform to watch for errors and to communicate progress to the frontend. Once Terraform
completes, the backend service saves any required outputs including secrets and state for use when another set of
changes need to be made. The deployed cluster has a set of base services deployed and is configured to dynamically
interact with the underlying cloud provider to allow for automated provisioning of volumes, services, and other
cloud-native services directly from within the cluster. This also enables features such as autoscaling and other
features that require integration between the cloud provider and the Kubernetes cluster managed by harpoon.

Git Element
-----------
The git element is a visual representation of a git repository which can be either a public or private repository.
A given git repository can be built with a pre-existing docker file or write their own build commands and choose
their own operating system to build the repository. Git elements can only be attached to nodes.

Container Element
-----------------
The container element is a visual representation of a container image that can be deployed to a cluster.
Container elements can only be attached to nodes. When a user calls for the deployment of a container on the frontend,
a backend service is called to process the request. The frontend passes the image and configuration information to
the backend for the creation of the container. harpoon stores the kubeconfig required to connect and interact with
a cluster so that requests can be made directly to the cluster. The backend service takes the information provided
by the frontend and dynamically generates a set of Kubernetes manifests to allow for the deployment of the container
to the running cluster. The exact manifests generated vary based on the exact nature of the request from the frontend
but generally, a Kubernetes Deployment object is created to instruct the cluster to deploy the container.
The backend service then deploys these manifests to the cluster using its API and then watches for a successful or
unsuccessful deployment of the container. The state and status of the deployment is communicated to the frontend
to show the user what the state of their request is.

Link Element
------------
The link element is a visual representation of a link between elements on the graph.
Links are attached by dragging from one element to another until the second element is selected.
A link represents a relationship between elements and how they are deployed in Kubernetes. Each element is
outlined below.

ConfigMap Element
-----------------
The config map element is a visual representation of Kubernetes ConfigMaps. A ConfigMap in Kubernetes
is a Key/Value pair. ConfigMap elements can only be attached to git or container elements.
When a ConfigMap element is attached to a git or container element, it modifies the deployment descriptor for the
relevant Kubernetes pod that is already deployed in the Kubernetes cluster and then executes a command in Kubernetes
to update the configuration for that deployment using the Kubernetes API. Much like the Container deployments,
the frontend makes a call to the backend which generates the required manifests and pushes them to Kubernetes
dynamically on behalf of the user. The backend service also modifies the associated container deployment to
expose the created ConfigMap, in the user-specified manner, to the running container deployment.

Volume Element
--------------
The Volume element is a visual representation of a Kubernetes Persistent Volume Claim (PVC) for a
given git or container element. Users can input the volume directory location inside a Kubernetes Pod where the
data will be replicated to a distributed volume in the cloud.  Volume elements can only be
attached to git or container elements. When a Volume element is attached to a git or container element, it modifies
the deployment descriptor for the relevant Kubernetes pod that is already deployed in the Kubernetes cluster and then
executes a command in Kubernetes to update the configuration for that deployment using the Kubernetes API. The PVC in
Kubernetes that is deployed will be dynamically linked to the distributed volume in the cloud. Much like the Container
deployments, the frontend makes a call to the backend which generates the required manifests and pushes them to
Kubernetes dynamically on behalf of the user. The backend service also modifies the associated container deployment
to expose the created Volume, in the user-specified manner, to the running container deployment.

Ingress Element
---------------
The ingress element is a visual representation of a Kubernetes Ingress Route for the deployed git or container element.
Users can directly input the port number that will be used to open the port for the relevant Pod in Kubernetes.
Clicking the lock image on an ingress element will open the lock and open the attached Container/Pod to
the internet. Ingress elements can only be attached to git or container elements. When an Ingress element is attached
to a git or container element, it modifies the deployment descriptor for the relevant Kubernetes pod that is already
deployed in the Kubernetes cluster and then executes a command in Kubernetes to update the configuration for that
deployment using the Kubernetes API. Depending on the exact cloud provider and ingress plane configured by the
Kubernetes deployment, harpoon will generate the required manifests to configure Ingress at the Kubernetes level.
For some Service Mesh based deployments, the harpoon backend services will deploy a loadbalancer using the same
Terraform mechanism used for the rest of the cluster. This is then configured to interact with the Service Mesh
within the cluster to allow for automated configuration of ingress into the cluster. The backend service will then
monitor the standup of the route both internally and externally to inform the user that the route is ready for use.
This can include monitoring DNS servers to watch for when names propagate and are ready for use by users.

Secret Element
--------------
The secret element is a visual representation of Kubernetes secrets storage for a given git or container element.
Secret elements can only be attached to git or container elements. A secret element also takes a key/value pair,
much like a ConfigMap, but offers more security/encryption through the Kubernetes secrets storage capability.
When the Secret element is attached to a git or container element, it enables the relevant Kubernetes Pod to
then use the key associated with the secret as a reference to the value of the secret, thereby obfuscating the
true value of the secret in any source code or variables in use by the Pod and giving the option to dynamically
modify the secret value without updating the software running in the Pod. Much like the Container deployments,
the frontend makes a call to the backend which generates the required manifests and pushes them to Kubernetes
dynamically on behalf of the user. The backend service also modifies the associated container deployment to
expose the created Secret, in the user-specified manner, to the running container deployment.

Pod Log Element
---------------
The log element is a visual representation of logs outputted by the deployed Kubernetes Pods giving users the
ability to see what is happening inside their deployed container image. When a user clicks the log button on a
specific container or git element that is already deployed (via the Deploy button), a request is made to harpoon’s
deployment microservice to retrieve the logs. The deployment microservices calls the Kubernetes API to return the
logs for the specified pod ID within the relevant namespace. The deployment service waits for Kubernetes to return
the response and then forwards that response to the harpoon frontend to display the relevant log data to the user.
The harpoon backend services connect directly to the Kubernetes API for the user cluster,
using the same dynamic mechanism as the other Kubernetes objects, to pull logs for the user deployments. These
are then sent to the frontend for visualization by the user.

.. _search:

Search
======

Search git repositories (public and private)
--------------------------------------------
Users can search for both public and private git repositories. A user links their Github account
(a third-party provider) to harpoon using a token from GitHub. When the user searches for a
repository by typing in the text of their search term (string), the string is sent to a harpoon microservice
where it is combined with the token to make a request to the Github API to find relevant repositories that
match the string. When a response is received from the GitHub API, the harpoon microservice sends the response
to the harpoon frontend to display with all the relevant data associated in JSON format that can be parsed into
the display.

Search for container images
---------------------------
Users can search for container images. A user searches for a container image by typing in the text of
their search term (string), the string is sent to a harpoon microservice to make a request to Docker Hub
to find relevant container images that match the string. When a response is received from Docker Hub, the
harpoon microservice sends the response to the harpoon frontend to display with all the relevant data
associated in JSON format that can be parsed into the display.

.. _third-party integration:

Third-party Integration
========

Link accounts
-------------
Users have the ability to link their third-party accounts to harpoon in order to search for
software to deploy using harpoon in a drag and drop fashion or connect to multiple cloud providers. The list of
third-party providers is currently:

* :doc:`aws`
* :doc:`vmware`
* :doc:`github`
* :doc:`dockerhub`
* :doc:`harbor`

.. _other:

Other
=====

Projects
------------
Users have the ability to separate deployments into different Projects. Projects are physically on the same
cluster but logically isolated. In this way, Project A cannot talk to Project B. Users can create a project from
scratch or copy existing projects into a workspace.


.. autosummary::
   :toctree: generated
