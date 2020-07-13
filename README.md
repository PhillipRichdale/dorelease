# dorelease
dorelease is a CLI Script that deploys a git version diff of files from current HEAD of a current
branch in a git versioned directory. To do this it utilises php-cli, git, cp and scp. dorelease automatically memorises releases on the current branch for future reference.

dorelease comes with some neat and useful features, such as revert, release-deploy and ignore and can also be used in projects where release branches aren't required. For convencience and ease of use dorelease tracks releases in its own tracking file "dorelease.releases".

dorelease is written in PHP but was built for any type of web project, not just PHP projects.
It also works great for static sites and other non-PHP projects.
 
A huge advantage of dorelease is that you don't need a CI or deployment host for deployments. dorelease is ment to be used on dev-team machines directly and is CI host independant.

 ___What dorelease is not___: dorelease is a release and deployment tool, *not* a build tool. Build, compile, transpile, minify, bundle, whatever your files with a seperate tool and track these artifacts in a seperate branch, then you can use dorelease as a release and deployment tool and also use <code>dorelease revert</code> for those artifacts.


**Requirements**
php-cli,
git,
cp,
rm,
scp (ssh) for remote deployments

**Installation**

Debian Linux Variants, including Ubuntu:
<code>apt install dorelease</code>

With composer (any platform):
<code>composer [bladiblah]</code>

For a direct global install on Linux or BSD copy and paste this command to the CLI and execute (sudo access required):

<code>curl https://bladiblah... && sudo mkdir /usr/share/dorelease && sudo mv dorelease /usr/share/dorelease/dorelease</code>
**Files**

dorelease.php, dorelease.ignore, dorelease.config, LICENSE, Readme.md (this file)

***Configuration & Setup***

**dorelease.config**

Configuration is stored in <code>dorelease.config</code>, in the git root of your project. If there is no sensitive information in dorelease.config it ___may___ be safe to version this file. If your unsure, gitignore dorelease.config and distribute it to your devteam using other means.

**dorelease.ignore**
<code>dorelease.ignore</code> is a list of files and their

**Commands**

<code>dorelease release [target (if other than default)] ["commen"]</code>

Deploys a release to the target.


<code>dorelease status</code>

Gives some status information on the current state of releases and how many commits away the last release was.


<code>dorelease revert</code>

Reverts the last release to the previous and removes the entry for the last release from the release file. This command will create the directory dorelease-filebuffer to check out the previous release and deploy those files. When finished it will remove the directory.


<code>dorelease --version</code>

Returns the version of dorelease.


<code>dorelease --help</code>
Returns a help list of commands.