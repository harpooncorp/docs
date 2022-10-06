=============
Using harpoon
=============

Registration
------------

Linking a Cloud Service Provider Account
----------------------------------------
See :doc:`aws`

Starting a cluster
------------------
Once you've linked your cloud service provider account, you just click the "start" button on the
cloud/node element in the workspace. That's it. No, really! The cloud/node element will turn yellow
and provide a little spinny wheel to entertain you. When the cluster is running, the cloud will return
and the element will glow a happy blue color.

Tearing down a cluster
----------------------
Don't need your cluster running all the time? No problem! Hit the "shutdown" button on the cloud/node
element in the workspace. This will automatically tear down all the infrastructure harpoon was using
in your cloud service provider account

.. raw:: html

    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
        <video width="320" height="240" controls>
        <source src="../_static/cluster-teardown.mp4" type="video/mp4">
        </video>
    </div>

.. important::
**WARNING: This will really destroy all of the infrastructure in your cloud service provider account
that was provisioned by harpoon. You can't come back from this aside from starting over, so make sure
you really do want to make everything go away.**

Scalling up a cluster
----------------------
Once you've already started your cluster scalling up is as easy as dragging another node element onto
the graph. That's it. No really! The cloud/node element will turn yellow and provide a little spinny wheel
to entertain you. When the cluster has completed the scale up, the cloud will return and the element will 
glow a happy blue color. To get access to more nodes you will need to upgrade your harpoon account if you
have not already. 

Scalling down a cluster
----------------------
Don't need all the nodes in your cluster anymore? No problem! Just hit the "delete" button on the
cloud/node element in your workspace. You can not delete the base node (the first node that was auto placed
on registration) but ever other node is able to be deleted/removed. Deleting a node will start the scale down 
process, no visual representaiton is shown becuase your cluster is still fully operational during this process.

.. important::
**WARNING: If you have any running containers or services attached to this node they will be destroyed.
You can't come back from this aside from starting over, so make sure you really do want to delete the node.**