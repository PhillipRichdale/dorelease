# dorelease
dorelease is a CLI Script that deploys a git version diff of files from current HEAD of a current
branch in a git versioned directory. dorelease automatically tags current and the last 5 past releases
on the current branch and force-pushes these tags and their changes to origin.

dorelease comes with some neat and useful features, such as revert release-deploy and ignore and is
meant to be used in projects where release branches aren't required, since it simply tags releases anyway.

dorelease is written in PHP but was built for any type of web project, not just PHP projects.
It also works great for static sites and other non-PHP projects.

A huge advantage of dorelease is that you don't need a CI or deployment host for deployments.

**Requirements**
php cli,
git,
ssh & scp for remote deployments

**Installation**

Debian Linux Variants, including Ubuntu:
<code>apt install dorelease</code>

With composer (any platform):
<code>composer [bladiblah]</code>

**Files**

dorelease.php, dorelease.ignore, dorelease.config

**Configuration**