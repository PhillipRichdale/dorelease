# dorelease
dorelease is a CLI tool that deploys a git version diff of files from current HEAD of a current branch in a git versioned directory. dorelease automatically memorises releases on the current branch for future reference. dorelease is programmed with web projects in mind, but can be used for anything with similar requirements for deployment and delivery.

dorelease comes with some neat and useful features, such as revert, release-deploy, include and ignore and can also be used in projects where release branches aren't required. For convenience and ease of use dorelease tracks releases in its own tracking file "dorelease.releases" and not with tags or git branches.
 
A huge advantage of dorelease is that you don't need a CI or deployment host for deployments. dorelease is ment to be used on dev-team machines directly and is independant of any auxiliary CI host.

 __What dorelease is not__\
 dorelease is a release and deployment tool, not a build tool. If you build, compile, transpile, minify, bundle, etc. your files with a seperate tool and track these artifacts in a seperate git branch, then you can use dorelease as a release and deployment tool and also use <code>dorelease revert</code> for those artifacts in that branch.

**Requirements**

dorelease is written in the PHP programming language. It requires <code>php-cli</code>, <code>git</code>, <code>cp</code>, <code>mkdir</code>, <code>rm</code>, <code>rmdir</code> and <code>scp</code> for all its features to work. dorelease does not require a webserver to function, it's a pure cli tool.

**Installation**

Debian Linux Variants, including Ubuntu:\
<code>apt install dorelease</code>

With composer (any platform):\
<code>composer [bladiblah]</code>

For a direct global install on Linux or BSD copy and paste this command to the CLI and execute (sudo access required):\
<code>curl https://bladiblah... && sudo mkdir /usr/share/dorelease && sudo mv dorelease /usr/share/dorelease/dorelease</code>

**Files:**\
<code>dorelease.php, dorelease.include, dorelease.ignore, dorelease.config, LICENSE, Readme.md (this file)</code>

*****Configuration & Setup*****

<code>**dorelease.config**</code>\
Configuration is stored in <code>dorelease.config</code>, in the git root of your project. If there is no sensitive information in <code>dorelease.config</code> it _may_ be safe to version this file. However, this is _not_ recommended if you're unsure about this. It is best to gitignore <code>dorelease.config</code> and distribute it to your devteam using other means, especially if you're using it in public projects or your team has varying auth/auth privileges for the deploy/release targets.

<code>**dorelease.include**</code>\
<code>dorelease.include</code> is a list of filepaths or globs/wildcard paths to be included in a release.

<code>**dorelease.ignore**</code>\
<code>dorelease.ignore</code> is a list of filepaths or globs/wildcard paths to be ignored. <code>dorelease.ignore</code> is applied after <code>dorelease.include</code> and represents the ignore subset of <code>dorelease.include</code>. 

**Commands**

<code>dorelease init</code>\
Initialises dorelease for usage in a git root of a project. Checks for presence of required tools, creates the required dorelease files and gives recommendations for the next steps.

<code>dorelease deploy _[target (optional, if other than default)] ["comment"]_</code>\
git diffs HEAD with last release and deploy to the (default) target. Requires an up-to-date working copy, with no lingering stashes or changes.

<code>dorelease status</code>\
Gives some status information on the current state of releases and how many commits away the last release was.

<code>dorelease revert</code>\
Reverts the last release to the previous and removes the entry for the last release from the release file. This command will create the directory dorelease-filebuffer to check out the previous release and deploy those files. When finished it will remove the directory.

<code>dorelease --version</code>\
Returns the version of dorelease.

<code>dorelease --help</code>\
Returns a help list of commands and gives some basic usage hints.