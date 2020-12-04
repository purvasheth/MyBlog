---
title: "Git: Correcting mistakes (stashing)"
date: "2020-12-04"
description: Git is daunting when you get started with it. You tend to face a fear of messing up like never before. This blog series will help you fight that fear.
---

Git is daunting when you get started with it. You tend to face a fear of messing up like never before. This blog series will help you fight that fear.

![image](https://imgs.xkcd.com/comics/git.png)

When we go wrong, we follow the procedure mentioned in the meme. Save our work and download a fresh copy. While this is a good "jugaad" (hack), it becomes tedious, and of course, there is a better solution.

Let's start with a simple command which will be useful in some scenarios.

### Stash

A glance at what the [Pro Git](https://git-scm.com/book/en/v2) book written by Scott Chacon and Ben Straub says

> Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged
> changes — and saves it on a stack of unfinished changes that you can reapply at any time (even on a different > branch).

Right. Okay. So what does this mean? 🤔

Well, a real-world analogy would help here.

Think of stashing as placing all your valuable changes safely in a box.
When filling a box, you'll add new items on top. Similarly, changes of subsequent stashes get added on top like a stack.

![image](https://media1.giphy.com/media/YhlZFaFx04fYY/giphy.gif)

We tend to cram stuff when packing.🙂 However, everything in a stash is neatly stacked and indexed in a well-organized manner. You can pull out changes from any index without affecting the rest.

Cool. Right? 🤩

Let's look at the commands in action. I urge you to try these out on a local repo to get a better understanding. Except for git, no installations are necessary.

1. Create a folder. And a demo file with some initial text.
2. Open git bash or terminal in that folder and run `git init` in the folder to initialize a git repository.
3. Add and commit changes.

   <img src="stash-1.png" alt="screenshot of steps so far">

4. Time for stashing now. Add some new text in your file.

   <img src="stash-2.png" alt="screenshot of new step">

5. Run `git stash` to stash the changes.
6. Create a new file with some text and add it for git to track it.

   <img src="stash-3.png" alt="screenshot of new steps">

7. Stash using `git stash save "named stash"` to save the stash with a name this time.

8. Now view a list of stashes made with guess what? 🙃 `git stash list`.

   <img src="stash-4.png" alt="screenshot of new steps">

9. Get more details of each stash with `git stash show stash{1} -p`.

   <img src="stash-5.png" alt="screenshot of new steps">

10. Run `git stash apply` to apply the most recently saved changes on your working directory.

    <img src="stash-6.png" alt="screenshot of new steps">

11. Changes will still be present on the stash. Run `git stash drop` to drop them. Alternately, `git stash pop` can be used to apply and drop changes using a single command.

12. Use `git stash clear` to remove all changes from the stash without applying them.

    <img src="stash-7.png" alt="screenshot of new steps">

**Note:** Index can be specified as `stash@{1}` with `apply` and `drop`. By default, they operate on the most recent stash present on the top.
