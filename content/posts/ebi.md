---
title: "Ebi: The making of a GitHub search tool from three perspectives"
date: 2019-05-02T19:36:15+01:00
draft: false
---
This post was co-authored by Jennifer Shepherd and Tak Tran.

![](https://cdn-images-1.medium.com/max/2000/1*snNh6o12brXPomFCizq34A.png)

At the Financial Times, we often find ourselves having to update tens to hundreds of GitHub repositories at a time. For example, pinning a node version if there is a security patch. For work like this, we kept hitting the same problem — *how do you know which repositories need updating*?

This led to the development of [ebi](https://github.com/Financial-Times/ebi), a GitHub repository search tool. ebi(えび in Japanese, or 🦐 in emoji, pronounced *air-bi*), is Japanese for prawn/shrimp, and aims to be a small command line tool to crawl through your sea of code on GitHub.

In this blog we’ll hear three perspectives from three developers in the Enabling Technologies Group (ETG), who worked on this project at different points.

## Tak: Full time developer on the ETG team
### _Defining the problem_

Inspired by our team building more and [more](https://github.com/Financial-Times/tooling-helpers) [small](https://github.com/Financial-Times/tako) [tools](https://github.com/Financial-Times/github), doing [one thing, and one thing well](https://en.wikipedia.org/wiki/Unix_philosophy), ebi came out of a frustration with how awkward finding out the answers to simple questions like the following were:

* Are the name fields in package.json consistent?

* Which projects are on the current version of node?

* Which repos have an app.json?

The GitHub organisation search box (eg, [Financial Times GitHub page](https://github.com/Financial-Times/)) is surprisingly very powerful, especially with the [filename](https://help.github.com/en/articles/searching-code#search-by-filename) qualifier. However it’s awkward with some queries that require looking at all files and finding something very specific eg, the node version in all package.json files. Also, the [GitHub search API](https://developer.github.com/v3/search/) has the limitation that it [may not always return all results](https://developer.github.com/v3/search/#timeouts-and-incomplete-results) (to keep it fast).

Writing plain JavaScript to query GitHub ultimately did the job for one of the rounds of questions, but it was tedious having to set up a new JavaScript copy-pasta environment each time I had a different query.

Around this time, while mulling in mild frustration, a project of finding and pinning Node versions came along as well as an addition of bootcamper [Jennifer Johnson](https://medium.com/@jkerr321). With fresh eyes and a tangible project to work through the frustrations, we had some great non-coding exploration sessions to flesh out the problem and possible solutions.

## Jen J: Bootcamper
### _Working on a solution_

I joined the team on a two week ‘bootcamp’ — a wonderful FT initiative whereby a developer steps out of their comfort zone and joins a completely different team in order to learn new things and better understand what other teams do. I was a bit nervous as this was my first bootcamp, and with a team who did some pretty gnarly stuff, but Tak and the team put me right at ease and I was learning lots and contributing from the moment I got there.

This project was an excellent piece of work for a bootcamper to get stuck into, and I’ll definitely be using it as a guide when my team hosts bootcampers of their own:

* The problem had been well defined so I wasn’t starting from scratch

* On the other hand, I got involved early enough that I could still help design the solution

* The problem was small enough that it felt like I could make a tangible difference in my two weeks on the team

* I had a brilliant mentor and guide in Tak who would be working on the project alongside me so I wasn’t working in isolation

* We didn’t know this on day one, but the solution ended up being easily divisible into tasks that we could work on in parallel without stepping on each other’s toes

So how did we come up with a solution to the problem? We knew we’d use the [GitHub search api](https://developer.github.com/v3/search/) to return results, but how did we want users to specify their search parameters, and how did we want to present results to the user?

This was a fun chat, particularly because Tak and I hadn’t worked together before so we got to know each other as we came up with ideas! We spent quite a lot of time exploring options and allowed ourselves to be creative with our thinking. Some that we came up with were:

A simple web app interface, with a user input form and results in a table:

![](https://cdn-images-1.medium.com/max/2000/0*uuwFMVWuvXVKS8FT)

![](https://cdn-images-1.medium.com/max/2000/0*OoueHwrlfB2Wstew)

A command line tool where a user specifies search parameters and is returned results in various levels of detail in a JSON file:

![](https://cdn-images-1.medium.com/max/2000/0*dxIZGQ8757zV-o7y)

A slack bot where a user could ask a question such as “**@ebi** which Financial-Times repos use node 8.13?”

![](https://cdn-images-1.medium.com/max/2000/0*RDtlwTYKFGSaT1-V)

In the end we decided to [keep it simple](https://en.wikipedia.org/wiki/KISS_principle) and agreed on a command line tool where a user would provide the list of repos they wanted to search, specifying the file they wanted to search and a search term. The tool would return a list of repos where a match for the search term was found in a given file.

Some examples of how we envisioned this tool would be used are as follows, and you can see more in our [usage examples wiki](https://github.com/Financial-Times/ebi/wiki/Usage-Examples):

**A user could search a list of repos for whether the string forever exists in their package.json files with the command**

    <list_of_repos> | npx ebi package forever

**Or a user could search a list of repos for Procfiles which contain the string web using the command**

    <list_of_repos> | npx ebi contents Procfile web

A list of matching results, along with errors, will be logged to the terminal, which can then be manipulated by the user in any number of ways using different programs:

    ...
    Financial-Times/next-article
    Financial-Times/next-front-page
    Financial-Times/next-search-page
    INFO: ‘Procfile’ has no match for ‘web’ in ‘Financial-Times/next-signup’

We were able to come up with a basic specification which had a lot of scope for iterative enhancement. Some of the design decisions that came out of that definition were:

* **[Caching is hard](https://martinfowler.com/bliki/TwoHardThings.html), so let’s not do it** — when wanting to run queries on files, it’s very tempting as an engineer to store those files, so it’s more efficient for future queries. However, then we have to deal with all the problems of having a cache (storage, keeping up to date etc). GitHub does an excellent job of hosting the files for us, so for our use case it’s fine to stand on their shoulders.

* **Start off simple, and do one thing, and one thing well** (like Tako). Let GitHub do most of the work of hosting and caching our code. The ideal is something a developer can run as quickly as putting something in a text box in the GitHub search box.

* **Composable** with general command line tooling and the suite of tools the team were building.

* **Be a really great 80% tool**, and be content that people will figure out how to do the 20% themselves if they really want it that bad. Make it easy for them to do so if they so choose.

* **We have [Tako](https://github.com/Financial-Times/tako)** to give us all the repositories we have, so the next logical step is to ask questions about the repositories from that list.

I loved this project because I learnt so much: not only about the scope of the work of the ETG team, but also about functional programming which was a pet passion of Tak’s, and about Unix and the command line as this was the first time I wasn’t able to take for granted what the terminal did for me!

By the time my bootcamp was over we’d published the first version of ebi as an NPM package with a solid set of tests and a few built in tools to maintain code hygiene, so it was in a great place for a new developer to dive into.

## Jennifer S: New team member
### _Enhancing the product_

I’d been at the FT for ten months when I moved to ETG from the Cloud Enablement (CE) team. In CE I’d been coding in Python, and used GitHub, configuration files and the command line a lot. I wrote javascript back when I was learning to code at [Makers Academy](https://makers.tech/) and was looking forward to improving my proficiency with it. I felt excited but wary about joining a team where obviously their projects were new to me AND I needed to upskill my javascript for my new tasks.

ebi was the perfect project to get started with. I could use and play around with it because it had been released — and I could immediately see the use of the tool. I started to read through the code to immerse myself in javascript; I wanted to work through the entire program and trace it the whole way. Tak quickly encouraged me to get stuck in with a pull request (PR) instead. I was apprehensive and felt under-prepared but he was completely right. The PR awaiting me extended the functionality to output JSON if the — json flag is used. This was a great way to get stuck in: checking the readability of the new feature’s code and following how tests were set up.

Tak is awesome to pair with, and having reviewed and approved the PR we began to work on the next feature: passing in a list of repositories as an argument (rather than as a list into stdin). I was mostly driving so that I couldn’t feign understanding or avoid having to consciously process what I needed to do! New to the team, I thoroughly enjoyed this phase. As we progressed, it became apparent that we could improve my coding environment setup so that it was better suited to the projects I’d now be working on; I was incredibly enthusiastic for Tak’s suggestions for tools and shortcuts that he used frequently.

This included [GitX](http://gitx.frim.nl/) (a program that helps you to visualise your git working tree and carefully manage your commits, staging, rebasing etc), [nodemon](https://nodemon.io/) to automatically run jest and eslint after code changes (for quicker feedback), [Husky](https://www.npmjs.com/package/husky) to prevent staging improperly formatted code and even basic hacks like splitting my terminal into panels for better visibility of everything at once. I’ve noticed that most developers in Customer Products are particularly adept with git (and have been running highly acclaimed workshops to share that knowledge!), so I particularly enjoyed using GitX to visually support my developing knowledge of the many ways to manipulate a git history.

Pairing with a dev who used and valued an efficient setup was so much fun and my onboarding was greatly accelerated by having a clear project that I comfortably understood and could progress with. This freed my mind up to take in the new ways of working and handy hacks I picked up! Also, one of the great things about working at the FT is our approach to flexible working. I work from home one day a week and Tak and I continued to pair remotely by using [Visual Studio Code Live Share](http://visualstudio.microsoft.com/services/live-share/), which I had used regularly in my previous team and could return some tips to Tak. We also found this a great tool to use when sat in the office next to each other — it gave us more screen space and the ability to control which parts of the code each of us was viewing (a common source of frustration when I’m the navigator in a pair and can’t see what I want to in the code).

Another benefit of pairing with an experienced senior developer was the quality of the discussions we had on design decisions. Tak questioned me before sharing his own opinions or preferences, which forced me to think about the purpose of our tool, the people who would be using it and the ease of maintaining it. I didn’t have the option to shirk responsibility by agreeing to whatever he suggested! His mind seemed so well-organised when considering these things, and he modelled how to allow my mind to see into his and yet still have the freedom to differ. I got a great introduction to functional programming too — not just the how, but the why.

ebi was small enough in scope and cognitive load as a problem to solve that it provided a perfect onboarding exercise. I’ve seen that different teams have different ways of styling their commits and the tidiness/consistency of the Customer Products repositories was impressive. I wanted to be consistent too, so this project was an excellent opportunity to review our commit style guide and follow suit. Gradually, I was naturally exposed to more aspects of team life and convention without it needing to be contrived or scheduled.

After getting feedback on the new PR from the rest of our team, it was time to merge and release! We now have a tool that can run a search on a list of repositories stored in a file OR passed as arguments on the command line.

The role of ETG is to build tools that support the developers in FT.com, so ebi’s primary audience is ‘internal’ to our part of Product and Tech. However, having worked previously in Enterprise Services (the part of tech responsible for our infrastructure and monitoring) I knew the tool would be useful there so I chatted to an Infrastructure Delivery colleague who was immediately able to put ebi to good use and cut time off checking which of their team’s repositories had circle ci set up (by searching for the presence of a ~/.circleci/config.yml). It felt good to be able to share our time-saving tools with colleagues across the FT and because of its scope (one thing, and one thing well) it’s so easy to make use of straight out of the box.

## Wrap up

ebi was a lovely little project that brought together 3 different people, from 3 different backgrounds, cultivated by FT’s diversity and encouragement of [moving between teams](https://medium.com/ft-product-technology/what-happens-when-you-move-around-inside-a-company-99e83adf5144).

Starting out as trying to scratch a developer itch to search GitHub repositories, it organically grew into a very enjoyable social coding experience for all of us. We were able to get to know new teams and team members, new approaches to development, develop human skills in learning and teaching, come out of our comfort zones and just have some fun coding with others.

The command line tool that came out of it is something we’re very proud of. You can have a play with it on [ebi@npm](https://www.npmjs.com/package/ebi). Or if you want to see the code, check out [Financial-Times/ebi](https://github.com/Financial-Times/ebi) and the wiki for [usage examples](https://github.com/Financial-Times/ebi/wiki/Usage-Examples).

Much love,

ebi (🦐) team
