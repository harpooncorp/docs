Features
========

harpoon Features:

.. _elements:

Elements
--------

Every element depicted below has a visual representation of what state the element is in, excluding the link elements and log elements. Translucent represents the element has no state and is waiting to be activated. Yellow represents the element that is in the process of being deployed. Blue represents a successful deployment and is running successfully. Red represents a failed deployment and error state.





Examples of node, git, volume, secret, ingress, and configmap elements together

User interface components:

Main user interface page when no user is logged in

Description: Initial user interface when no user is logged in.



Main user interface page when user is logged in

Description: Initial user interface when a user has logged in.


Figure: 32
Registration

Description: Registration form for a new user to create an account with harpoon.


Figure: 33

Login

Description: Login form so a user can access their account.


Figure: 34
Search git repositories (public and private)

Description: Users can search for both public and private (refer to figure 36) git repositories. As depicted in Figure 35, a user has previously linked their Github account (a third-party provider) to harpoon using a token. When the user searches for a repository by typing in the text of their search term (string), the string is sent to the harpoon microservice where it is combined with the token to make a request to the Github API to find relevant repositories that match the string. When a response is received from the Github API, the harpoon microservice sends the response to the harpoon frontend to display with all the relevant data associated in JSON format that can be parsed into the display shown in Figure 35.


Figure: 35


Figure: 36





Search for container images
Description: Users can search for container images. As depicted in Figure 37, a user searches for a container image by typing in the text of their search term (string), the string is sent to the harpoon microservice to make a request to Docker Hub to find relevant container images that match the string. When a response is received from Docker Hub, the harpoon microservice sends the response to the harpoon frontend to display with all the relevant data associated in JSON format that can be parsed into the display shown in Figure 37.



Figure: 37


Link accounts

Description: Users have the ability to link their third-party accounts to harpoon in order to search for software to deploy using harpoon in a drag and drop fashion or connect to multiple cloud providers (Figure 44 and 45).


Figure: 44



Figure: 45

Copy Project

Description: Users have the ability to copy projects or create new blank projects.


Figure: 46


Figure: 47


Figure: 48


.. autosummary::
   :toctree: generated

   lumache
