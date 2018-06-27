# Git Rebase

### Simply put...

If you have differences that aren't on the origin branch, briefly put those aside, pull in the origin branch into your local branch, and then apply those changes that weren't on the origin branch. 

What this does is always apply your own changes on top of the (structure of) the origin branch, while leaving that stucture wholly intact.

Credit: https://dev.to/alainvanhout

### What's the hesitation?

The reason people shy away from rebase is because it rewrites history - meaning it changes the commit SHAs. So if you're sharing your work with others, that can be a problem.

It's likely this consultant was the victim of a force push and made a sweeping statement to never use rebase again. We've all been there. It's frustrating.

Being mindful of which commands, like rebase, can rewrite history resolves this issue. Then you can use it appropriately. For example, I use rebase often. But I do so at the end - right before merging - so I limit the chance for it to affect other developers.

Credit: https://dev.to/gonedark

### What's the benefit? | Why would I want to rebase something?

You update the beautiful front-end UI of your account login system, and unsurprisingly, other people were working on the site while you were making these changes.

One developer changed the flow of the login forms.
One adjusted the input fields in the profile.
Another added extra fields for info about providers that you save to your profile.

All these changes might be worrisome. What if someone merged a change that affects or overlaps with the ones you made? It could lead to bugs in your beautiful healthgrades website! If you look at the different changes made, one does cause some issues! 

**Is there a safe way to merge your changes without risking any conflicts, and missing out on all the other changes made?**

Sound the rebase sirens and call rebaseman. This is the kind of context that calls for a git rebase.

---

