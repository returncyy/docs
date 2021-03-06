# Seattle SVN Repository

Our project uses SVN for our version control. This page describes our configuration.

----

----

## Configuration
----

 * Our SVN is installed in /var/local/svn/
 * We do not use SVN built-in groups/users for authentication
 * Our SVN allows read-only anonymous access via HTTP (to everything in the SVN except for the /seattle/trunk/assignments directory)
 * Anyone who has SSH access to seattle.cs is automatically granted read-write access to the entire repository
 * We do ''not'' run the svnserve daemon (which speaks the svn:// protocol)



## SVN Hooks
----

SVN hooks allow one to run arbitrary scripts whenever some action is taken by a user. We have a single SVN hook: post-commit hook file which runs whenever a user successfully commit to the SVN.

This hook is located here in our repository: /trunk/svn-hooks/post-commit

The hook is deployed/installed here: /var/local/svn/hooks/post-commit

This hook is used to run the unit-testing suite over the new version of the repository, and generates an email if any of the unit-tests fail for some reason.