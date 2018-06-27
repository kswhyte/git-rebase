# Git Rebase

### Simply put...

If you have differences that aren't on the origin branch, briefly put those aside, pull in the origin branch into your local branch, and then apply those changes that weren't on the origin branch. 

What this does is always apply your own changes on top of the (structure of) the origin branch, while leaving that stucture wholly intact.

Credit: https://dev.to/alainvanhout

### Why not?

The reason people shy away from rebase is because it rewrites history - meaning it changes the commit SHAs. So if you're sharing your work with others, that can be a problem.

It's likely this consultant was the victim of a force push and made a sweeping statement to never use rebase again. We've all been there. It's frustrating.

Being mindful of which commands, like rebase, can rewrite history resolves this issue. Then you can use it appropriately. For example, I use rebase often. But I do so at the end - right before merging - so I limit the chance for it to affect other developers.

Credit: https://dev.to/gonedark
