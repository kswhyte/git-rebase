# Git Rebase

## Some Overhead

### Simply put...

If you have differences that aren't on the origin branch, briefly put those aside, pull in the origin branch into your local branch, and then apply those changes that weren't on the origin branch. 

What this does is always apply your own changes on top of the (structure of) the origin branch, while leaving that stucture wholly intact.

Credit: https://dev.to/alainvanhout

### What's the hesitation?

The reason people shy away from rebase is because **it rewrites history - meaning it changes the commit SHAs. So if you're sharing your work with others, that can be a problem.**

It's likely this consultant was the victim of a force push and made a sweeping statement to never use rebase again. We've all been there. It's frustrating.

Being mindful of which commands, like rebase, can rewrite history resolves this issue. Then you can use it appropriately. For example, using rebase at the end - right before merging - to limit the chance for it to affect other developers.

Credit: [Jason McCreary - gonedark](https://dev.to/gonedark)

### What's the benefit? | Why would I want to rebase something?

You update the beautiful front-end UI of your account login system, and unsurprisingly, other people were working on the site while you were making these changes.

1. One developer changed the flow of the login forms.
2. One adjusted the input fields in the profile.
3. Another added extra fields for info about providers that you save to your profile.

All these changes might be worrisome. What if someone merged a change that affects or overlaps with the ones you made? It could lead to bugs in your beautiful healthgrades website! If you look at the different changes made, one does cause some issues! 

**Is there a safe way to merge your changes without risking any conflicts, and missing out on all the other changes made?**

Sound the rebase sirens and call rebaseman. This is situation calls for a git rebase.

## How do I do it?

Let's say the branch your rebasing on is `master`. Make sure the local version is up to date wit the remote: 
`git checkout master`;
`git pull`;
`git checkout my-new-feature-branch`;

A straightforward rebase has a pretty simple command structure: `git rebase <branch>`, where `<branch>` is the one you're rebasing off of. So here, you'll run `git rebase master`. Assuming there's no conflicts, that's all the rebase needs!

## What does a rebase do?

**The rebase itself technically removes your old commits and makes new commits identical to them, rewriting the repo's commit history.** That means pushing the rebase to the remote repo will need some extra juice. Using git push --force will do the trick fine, but a safer option is git push --force-with-lease. The latter will alert you of any upstream changes you hadn't noticed and prevent the push. This way you avoid overwriting anyone else's work, so it's the safer option.

## Quick Tips

#### Rebases 'feature' to 'master' and merges it in to master:
`git rebase master feature && git checkout master && git merge -`

#### Always rebase instead of merge on pull:
`git config --global pull.rebase true`

#### Change previous two commits with an interactive rebase:
`git rebase --interactive HEAD~`

## Sources | Credit

[The Git Rebase Introduction I Wish I'd Had](https://dev.to/maxwell_dev/the-git-rebase-introduction-i-wish-id-had)
