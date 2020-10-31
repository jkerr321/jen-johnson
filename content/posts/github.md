---
title: "A Guide to GitHub for Non-Developers"
date: 2020-10-05T19:36:15+01:00
draft: false
---
### What does it mean when someone says they ‘merged the code’?

I wrote this blog post because one day the designer on my team said to one of the developers: “in the Stand Up today, you said that you’d merged the code, but what does that actually mean?”

I didn't used to be a developer but I've always worked in development teams and hearing that question took me back to my non-development days: having a pretty good idea of how things were going on a piece of work by hearing words like **merge**, **pull request** and **deploy**, and understanding their approximate order in the way of things, but not really knowing what they meant.

It reminded me how little understood some common development processes are beyond the developers who use them, probably for no other reason than there is so much that developers talk about that’s a bit obscure, and getting to the bottom of all of it is an impossible task.

So here is the plain English translation of the words and phrases we use for for getting the code we've written on our computers (**local**) to the place we store it for future referece (**source control**, in our case **repositories** on **GitHub**), before we make it live on the website (**deploy** it to **production**). In a few words we could call this our **source control** and **deployment** process.

![A Guide to Customer Products GitHub Parlance for non developers (1)](https://user-images.githubusercontent.com/17846996/93846937-68690700-fc9d-11ea-9dca-1734df0547c1.png)
_The whole glorious process_

### GitHub

![github](https://user-images.githubusercontent.com/17846996/93847123-f7761f00-fc9d-11ea-8f77-f40e8b4bb8f3.png)

Let's start with the big guns: **GitHub**. GitHub is where we keep all of our code. Code is split into **repositories** (or **repos**) which are akin to folders on your computer. Most of the time a distinct app or service has its own repo. E.g. the `next-article` repo for the article page app.

> Things a developer might say:
>_something's broken but I haven't figured out which repo it's in_ 🧐

If you look at a repo in GitHub the code you will see is called the **`main`** **branch**. A branch is a bit like a sub-folder, and the `main` branch contains the code that exists in production, i.e. if you look at the main branch on the `next-article` repo you will see the code that gets run when you load an article page on FT.com.

### Working locally

![working locally](https://user-images.githubusercontent.com/17846996/93847218-3dcb7e00-fc9e-11ea-95d3-2af3d45c9770.png)

A repo will usually have other branches too; these are copies of the main branch which have been edited in some way, usually because a developer is in the process of adding, fixing, or otherwise changing something.

When a developer wants to make any changes to the production code they do so on their own laptop on a copy of the repo they have **cloned** there. This is called working **locally**. They do this work on a branch so that their changes aren't reflected in the production code until they're happy with them.

Multiple times a day a developer will **commit** and **push** the changes they've made locally to github (there are some nuances to this process but I won't go into them here). This saves the changes to GitHub and these are the branches you'd see if you looked at a GitHub repo.

>_which branch is that on?_ 🤔

>_whyyyyy can't I get this running locally?!!!_ 😩

>_let me just commit these changes before I go_ 🍺

### Merging

![merging](https://user-images.githubusercontent.com/17846996/93847283-7408fd80-fc9e-11ea-91e8-d733d235b783.png)

When a developer is happy with their code they will create a **pull request** (PR) asking for it to be reviewed. In a pull request a developer explains the changes they've made in the code. Other team members review the changes and approve the PR or leave comments asking for changes.

Creating and reviewing pull requests is the part of this process where there's a dependency on other people and can be time consuming, although it's very worthwhile. Good pull requests make it as easy as possible for people looking at the code in the future to understand what decisions were made to get it to that point.

Once the PR has been approved it can be **merged** into the main branch.

>_My PR is almost ready to go_ 🙌 (i.e. almost ready to be reviewed)

>_Pleeeeeeeeeease can someone review my PR?_ 🙏

### Deploying

![deployment](https://user-images.githubusercontent.com/17846996/93847378-aadf1380-fc9e-11ea-9d08-0225ecdc46fd.png)

Once a PR has been merged the code from the developer's branch will be contained in the `main` branch, but it won't yet show up on the website. For that to happen it needs to be **deployed**.

Deploying means getting the code from where it's stored, in GitHub, onto the servers that host the site, in our case on a platform called `Heroku`.

Because of some wonderous thinking by the FT developers of yore about how to make deployment as easy as possible, the deployment process starts automatically when a PR is merged in GitHub. We use another tool called CircleCI to manage our deployments. 

CircleCI takes the code from github and **builds** and **deploys** it.

In building the app, Circle takes the code that's in the repo and does a load of _stuff_ to it that makes it ready to run in production. (Like all development, this process is like fractals - you can get more and more in depth about what it entails until you're just dealing with the zeros and ones, but I think for the purposes of this blog '_stuff_' will do).

Circle then runs a final set of tests on the code and deploys it by saving it to the relevant app on Heroku. Once the code has successfully been deployed it will be visible in production within minutes.

> _Argh i've merged the changes but now Circle is failing / my build is failing / the deploy step is failing / a test is failing that was definitely working locally_ 🤯

-------------

Some of the stuff developers talk about is unfortunately obscure to non-developers because it is pretty technical or about code _stuff_, but a lot of it needn’t be, and hopefully this post has helped clear the mist about some of the words you’ll hear every day about GitHub and the deployment process.