######
GitLab
######


Merge Request
#############

*   Merge Requests should have no more than 1000 changed lines (total of removed + added). Otherwise reviewing them gets really hard. You can always split your large change in several consecutive merge requests.


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


Review Workflow / Labels
########################

A set of common labels is used, to mirror the review workflow.

Labels
======

There are 4 labels in total and they tell you about the status of the merge request. Every merge request should only have a single one of these labels at any given time.

Needs Review
------------

.. image:: img/needs-review.png

The merge request is ready to be reviewed.
Every new merge request should get this label by default.

If you fixed all issues that were found in the review (i.e. all conversations were resolved), you should
add this label again.


Needs Work
----------

.. image:: img/needs-work.png

The review is finished and there is something that needs to be changed.
The things that need to be changed were commented in the merge request.


Waiting for Dependencies
------------------------

.. image:: img/waiting-for-dependencies.png

This merge request is based on another (open) merge request. It is not reviewed until the other merge
request is merged. You should also not the merge request dependencies with the ``[req !123, !234]`` fragment
in the merge request title (see above).

After the other merge request is merged, you should rebase this merge request, remove the title fragment and
change the label to ``needs-review`` (if this merge request is ready).


Suspended
---------

.. image:: img/suspended.png

This label marks a merge request as suspended. It should not be reviewed, not be worked and not be merged.
It is only kept for historical reasons or if some feature is postponed to a later release.


Typical Situations
==================

**I created a new pull request:**

    Just add the label ``needs-review`` (and possibly send the URL to the MR as a friendly ping in Slack
    to the reviewer) and assign the reviewer.

**The merge request was marked as ``needs-work``:**

    There are some things in the merge request that need to be fixed. Maybe some bugs, code style issues,
    you need to rebase or something else. You can learn more about what needs to be changed in the comments
    in the merge request.

**I have finished working on all commented issues:**

    Resolve all conversations, remove the ``needs-work`` label and re-add the ``needs-review`` label.

**I am currently working on the issues, but need to track my progress but don't want to confuse the reviewer:**

    Just mark all conversations as resolved, as soon as you have fixed them (like typing the fix in your IDE).
    You don't have to push them to mark the conversation as resolved. The reviewer will restart their review
    as soon as you changed the label, so as long as you keep the ``needs-work`` label, you are free to do whatever
    works for you.

**I am not yet finished, but have a question about some of the review comments:**

    As you are not yet finished, keep the ``needs-work`` label on the merge request. Ask your question in the comments,
    the reviewer will respond to it. If they don't, send them a friendly ping in Slack.
