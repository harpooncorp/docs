=============
Using harpoon
=============

Registration
------------

Linking a Cloud Service Provider Account
----------------------------------------
See :doc:`aws`
See :doc:`azure`
See :doc:`gcp`

Starting a cluster
------------------
Once you've linked your cloud service provider account, you just click the "start" button on the
cloud/node element in the workspace. That's it. No, really! The cloud/node element will turn yellow
and provide a little spinny wheel to entertain you. When the cluster is running, the cloud will return
and the element will glow a happy blue color.

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/cluster-startup.mp4" type="video/mp4">
        </video>
    </div>

Tearing down a cluster
----------------------
Don't need your cluster running all the time? No problem! Hit the "shutdown" button on the cloud/node
element in the workspace. This will automatically tear down all the infrastructure harpoon was using
in your cloud service provider account

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/cluster-teardown.mp4" type="video/mp4">
        </video>
    </div>

.. important::
**WARNING: This will really destroy all of the infrastructure in your cloud service provider account
that was provisioned by harpoon. You can't come back from this aside from starting over, so make sure
you really do want to make everything go away.**

Scalling up a cluster
----------------------
Once you've already started your cluster, scalling up is as easy as dragging another node element onto
the graph. That's it. No really! The cloud/node element will turn yellow and provide a little spinny wheel
to entertain you. When the cluster has completed the scale up, the cloud will return and the element will 
glow a happy blue color. To get access to more nodes you will need to upgrade your harpoon account if you
have not already. 

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/scale-up-cluster.mp4" type="video/mp4">
        </video>
    </div>

Scalling down a cluster
----------------------
Don't need all the nodes in your cluster anymore? No problem! Just hit the "delete" button on the
cloud/node element in your workspace. You can not delete the base node (the first node that was auto placed
on registration) but every other node is able to be deleted/removed. Deleting a node will start the scale down 
process, no visual representaiton is shown becuase your cluster is still fully operational during this process.

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/scale-down-cluster.mp4" type="video/mp4">
        </video>
    </div>

.. important::
**WARNING: If you have any running containers or services attached to this node they will be destroyed.
You can't come back from this aside from starting over, so make sure you really do want to delete the node.**

Deploying Containers
----------------------
Deploying containers is as easy as hitting the deploy button. Github containers will require you to build the 
repository first. In order for harpoon to successfully build a GitHub repository, we currently require the repository
to have a top-level Dockerfile, which is industry best practice. If the Dockerfile is there, once you click the “Build”
button, harpoon will automatically find it and build a container image that gets pushed to a private container registry
only harpoon has access to. After a successful build, the “Deploy” button will become enabled, and you can deploy the 
software directly.

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/deploy-docker.mp4" type="video/mp4">
        </video>
    </div>
Docker container deploy

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/github-build.mp4" type="video/mp4">
        </video>
    </div>

Github container build

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/github-deploy.mp4" type="video/mp4">
        </video>
    </div>

Github container deploy

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/harbor-deploy.mp4" type="video/mp4">
        </video>
    </div>

Harbor container deploy

Container Logs
----------------------
Getting a containers logs once it has been deployed is as easy as hitting the logs button located on the top right of the container.

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/docker-logs.mp4" type="video/mp4">
        </video>
    </div>

Linking Elements
----------------------
Linking container elements to volumes, ingress routes, secrets and config maps is as easy as hovering over the element
and dragging a link to the intended target element.

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/volume-attach.mp4" type="video/mp4">
        </video>
    </div>

Volume link

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/ingress-attach.mp4" type="video/mp4">
        </video>
    </div>

Ingress link

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/secret-attach.mp4" type="video/mp4">
        </video>
    </div>

Secret link

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/config-attach.mp4" type="video/mp4">
        </video>
    </div>

Config Map link

Linking Container registry accounts
----------------------
Linking your github and harbor accounts will allow you to search through your github repositories and harbor images. 

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/link-github.mp4" type="video/mp4">
        </video>
    </div>

Link Github Account

.. raw:: html

    <div>
        <video width="320" height="240" controls>
        <source src="_static/link-harbor.mp4" type="video/mp4">
        </video>
    </div>

Link Harbor Account
