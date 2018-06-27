# Git Rebase - The Essentials Consolidated

## Some Overhead

### Simply put...

If you have differences that aren't on the origin branch, briefly put those aside, pull in the origin branch into your local branch, and then apply those changes that weren't on the origin branch. 

What this does is always apply your own changes on top of the (structure of) the origin branch, while leaving that stucture wholly intact.

Ref/Credit: [Alain Van Hout - Dev.to](https://dev.to/alainvanhout)

### What's the hesitation?

The reason people shy away from rebase is because **it rewrites history - meaning it changes the commit SHAs. So if you're sharing your work with others, that can be a problem.**

It's likely this consultant was the victim of a force push and made a sweeping statement to never use rebase again. We've all been there. It's frustrating.

Being mindful of which commands, like rebase, can rewrite history resolves this issue. Then you can use it appropriately. For example, using rebase at the end - right before merging - to limit the chance for it to affect other developers.

Ref/Credit: [Jason McCreary - Dev.to](https://dev.to/gonedark)

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

**The rebase itself technically removes your old commits and makes new commits identical to them, rewriting the repo's commit history.** That means pushing the rebase to the remote repo requires another command. Using `git push --force` will do the trick fine, but a safer option is `git push --force-with-lease`. **The latter will alert you of any upstream changes you hadn't noticed and prevent the push. This way you avoid overwriting anyone else's work, so it's the safer option.**

## Of course, sometimes there will be conflicts...

Say your change to the app's account UI is at odds - there is a conflict - with a change another dev made to the same copy. The updated markups from both sets of change are in the same lines - **this means the rebase can't happen automatically.** Git won't know which parts of the changes to keep and which to remove. It must be resolved! 

Thankfully, git makes this very easy. **During the rebase, git adds each commit onto the new base one by one. If it reaches a commit with a conflict, it'll pause the rebase and resume once it's fixed.** Rebase conflicts are handled essentially the same way as merge conflicts. `git status` will tell you where the conflicts are, and the two conflicting sections of code will be next to each other so you can decide how to fix them.

Once everything is fixed, `git add` and `git commit` the changes like you would a normal merge conflict. Then run `git rebase --continue` so git can rebase the rest of your commits. It'll pause for any more conflicts, and once they're set you just need to `git push --force-with-lease`.

Two lesser-used options could also be handy. 
1. Go back to before you started the rebase. It's useful for unexpected conflicts that you can't rush a decision for:
`git rebase --abort` 
2. Skip over the commit causing the conflict altogether. Unless you know it's an unneeded commit, you probably won't want to use it much:
`git rebase --skip`

## Great power brings great responsibility - more control?

With what you know so far, rebasing will lend great power. To have even greater version control, add `--interactive`, or `-i`, flag in your command. For instance, `git rebase -i master` shows a list of all the commits you're about to rebase. You can choose which ones to stop and edit, which ones to skip, and even merge some together!



## Quick Tips

#### Rebases 'feature' to 'master' and merges it in to master:
`git rebase master feature && git checkout master && git merge -`

#### Always rebase instead of merge on pull:
`git config --global pull.rebase true`

#### Change previous two commits with an interactive rebase:
`git rebase --interactive HEAD~`

## Sources | Credit

[The Git Rebase Introduction I Wish I'd Had](https://dev.to/maxwell_dev/the-git-rebase-introduction-i-wish-id-had)

## Further Dive-in

[Git Interactive Rebase, Squash, Amend and Other Ways of Rewriting History](https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history)
