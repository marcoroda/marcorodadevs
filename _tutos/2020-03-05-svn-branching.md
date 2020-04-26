---
layout: post
title: SVN Branching
date: 2020-03-23
published: true
github_comments_issueid: "7"
---
<!-- # Add an extra blanc line 
<p>&nbsp;</p> -->

<small><i>Table of contents</i></small>
* Table of contents
{:toc}

# /brief
Sometimes you are forced to use Subversion... It happens specially when some repos on your company are tied to this old technology! 
After many attempts on trying to do branching in SVN, I finally came up with a workflow that seems to work. Here on this page I describe the branching workflow that works for me.

# Create a branch
I will be using Tortoise SVN.
Let us imagine that we have a src/ folder that all the changes on files we might do are within this folder. My trunk/ and src/ folders look like: 

<p align="left">
  <img width="350"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_trunk.png">
</p>

<p align="left">
  <img width="350"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_src.png">
</p>
<p>&nbsp;</p>

Now, let us create a branch ("cheap copy" really):
With the src/ folder selected, right click > tortoiseSVN > Branch/Tag, as following:
<p align="left">
  <img width="600"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch1.png">
</p>
<p>&nbsp;</p>

Now, we select to which branch folder we want the src/ folder to be "copied". I like to create a folder under /branch with a description of te feature to be developed:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch2.png">
</p>
<p>&nbsp;</p>
Add a commit message and press "Ok":
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch3.png">
</p>
<p>&nbsp;</p>

Now, we have a copy of the "HEAD revision" of the trunk/src folder under the branches/feature-xpto.
One could go to the branches/ folder and start working in the feature branch, however we would have to TortoiseSVN > Switch... (to switch the working directory). I prefer not to, and believe I tried. 
The way I prefer to do it would be to create another folder */_branching* on the root of the SVN repo, and create a folder with the name of the feature branch we just created "feature-xpto".
<p align="left">
  <img width="350"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch4.png">
</p>
<p>&nbsp;</p>

On this dir, let's do an SVN checkout of the create feature branch:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch5.png">
</p>
<p>&nbsp;</p>

Press "ok" and our feature branch folder should now contain the following files:
<p align="left">
  <img width="450"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch6.png">
</p>
<p>&nbsp;</p>
Now, work on your feature and when you are ready, commit to /branches/feature-xpto:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch7.png">
</p>
<p>&nbsp;</p>


# Merge the branch into trunk
When the new feature is ready for production, it needs to be merged into the trunk. To do so, navigate to trunk and right click under src/ folder > TortoiseSVN > Merge. The following window pops up:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch8.png">
</p>
<p>&nbsp;</p>
Here we select the branch to merge from and the specific revision to be merged:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch9.png">
</p>
<p>&nbsp;</p>
Press "Next" and press "Merge". Conflicts might appear if someone committed to the trunk while you were working on the feature branch. If all goes ok, you should see the following window:
<p align="left">
  <img width="500"  src="../../../../../assets/tuto_svn_branching/file_exp_svn_branch10.png">
</p>
<p>&nbsp;</p>

Finally, commit the trunk by right clinking > TortoiseSVN > Commit and write your merge commit message.

# Wrapping up
Branching on SVN can be a pain. This setup is not ideal but it works for me. Hope it's useful to someone out there.
Happy coding! *ah, use Git, Git is awesome!!!* 