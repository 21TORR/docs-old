######
GitLab
######


Merge Request
#############

Please give your merge request descriptive titles. That includes merge request that just merge `develop` into `master`.

Merge Requests should have the following structure::

    Descriptive Title [req <GitLab Merge Request Numbers>] (<JIRA issue numbers>)


Some examples
=============

A merge request that has no JIRA issue and no other required merge request::

    This is my merge request


A merge request that is the implementation for JIRA issue ``ABC-123``::

    This is my merge request (ABC-123)


A merge request that is the implementation for JIRA issue ``ABC-123`` and ``DEF-234``::

    This is my merge request (ABC-123, DEF-234)


A merge request that requires the merge request ``!11`` to be merged first::

    This is my merge request [req !11]


A merge request that requires the merge requests ``!11`` and ``!12`` to be merged first::

    This is my merge request [req !11, !12]


A full example of a merge request with multiple dependencies and multiple JIRA issues::

    This is my merge request [req !11, !12] (ABC-123, DEF-234)


Updates
=======

As soon as the required other merge requests are merged, you should update your merge request title and remove every
merge request id, that is already merged in your target branch.


Why?
====

*   This convention makes merge requests more readable (as they all have the same structure)
*   However the base is always a descriptive title.
*   The dependencies of merge requests are immediately visible
*   We can link merge requests to JIRA issues. That enables us to see the context of a code change.
*   We can (through an automatic integration) see in a JIRA ticket the merge request / commit that implemented this change.


Commits
#######

You can also use JIRA issue numbers in your commit message. Keep the title as plain and descriptive text and add the
issue number in the description of the commit::

    Add frontend user authentication

    ABC-123
