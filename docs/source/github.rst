======
GitHub
======
harpoon can connect to your GitHub account with as little as the click of a button. Once your GitHub
account is attached to harpoon, you can search for any public or private repository you have access to.
To make it easier to find your own or your organizations' private repositories, we provide a toggle button
so that you can switch back and forth between public and private repository search. When toggled to
"private" search, only the private repositories you have access to will be returned in the search.

Once you find the repository you're looking for, you can drag and drop it onto the workspace. You'll
know that an element in the workspace is a GitHub repository because it will have the Octocat logo
in the bottom right corner of the element.

In order for harpoon to successfully build a GitHub repository, we currently require the repository
to have a top-level Dockerfile, which is industry best practice. If the Dockerfile is there, once you
click the "Build" button, harpoon will automatically find it and build a container image that gets
pushed to a private container registry only harpoon has access to. After a successful build, the
"Deploy" button will become enabled, and you can deploy the software directly.

If you're running into issues building or deploying any particular GitHub repository, remember you can
always click on the log button to see what is going on under the covers.
