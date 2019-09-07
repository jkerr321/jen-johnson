---
title: "One year on as a new developer"
date: 2017-12-17T19:36:15+01:00
draft: true
---

# One year on as a new developer

Or, Comparing what I learned in December two years in a row

![A mountain. We’ll get to this metaphor eventually.](https://cdn-images-1.medium.com/max/5120/1*NfMUeB-bODLAXRxsOP5fag.jpeg)*A mountain. We’ll get to this metaphor eventually.*

In May 2016 I started learning JavaScript with [freeCodeCamp.org](https://www.freecodecamp.org/). In December 2016, with the help and support of some incredible colleagues (and I could write essays and essays on that, but another time) I entered our organisation’s annual hackathon and committed my first code to the FT codebase.

Fast forward a year and I’m now officially spending 50% of my time developing for the FT, and soon I hope that will be 100%.

Around the time I joined the hackathon in 2016, when I was completely overwhelmed by all the new things I was coming across every day and feeling like I might drown in it all, [Simon Legg](https://twitter.com/simonleggsays) suggested that every day I write down something new that I’d I learned so that I could see my progress day by day.

Well, a year later, and that document is 101 pages long, and this is what’s at the very start and the very end of it:

**There was a lot of stuff on these lists about development and build specific to the FT’s way of doing things, which I’ve removed to make more it generally understandable*

***The items on these lists are almost exactly as they appear on my original document, I’ve added some comments in for this post using the standard // format*

## What I learned in December 2016

1. What headers do

1. How to use a text editor and the terminal

1. Linting; convention is that leaving console.log() in your code is badddd! Oops.

1. What SASS and Babel do ***// lies. I’m still not really sure what Babel does. Points for bravado though 2016 Jen***

1. What npm is for, what a dependency is, how to clone a project locally using git and the terminal, how to use the device emulator in Chrome dev tools

1. Got my head round node.js as async language and wrote my first async function ***// more lies. I may have written an async function but ‘got my head round JS as an asynchronous language’.. nooope!***

1. Github — the difference between a commit and a pull request ***//the essentials!***

1. Created a repo, committed my first code via the command line (personal, not ft, alas), discovered HOW VERY LONG it takes to figure out random errors, deployed an app to Heroku

1. My first hacky FT code. Copied an [Origami](http://origami.ft.com/) component and smushed it into an FT app. The styling didn’t come through, so followed 20mins of figuring out why. Imported the component to the CSS file, still didn’t work. Added bower dependency with help from Theo. Success. Felt like a hero!

1. The concept of overflow in CSS

1. That if you change code in main files they will all be overwritten by content of sub-files when you build :( :( ***// this was a sad day***

1. My first commit of FT code! And it won a hackathon prize!

1. Why I don’t need jQuery (***//bold!***). What React and Bower are (kinda). That ‘transpiles’ is a real word

1. How useful README’s are

1. Deployed my own app on Heroku! Found out how to stub a server app if app only contains client side code. How to look at Heroku logs. How to find out where errors are in json. How to put a breakpoint in code using sources in Chrome dev tools.

1. My first FT pull request and merge to production. And my first time breaking production :( ***// had to happen some time, shame it was my first ever merge***

1. The difference between queryselector and queryselectorall

1. ‘Minify’ — what happens to all code when it’s compiled(?) — variables are renamed with one letter, all white space is removed — it becomes essentially unreadable

1. To get around async JavaScript you need to use a promise or callback ***// told you I was lying when I said I’d ‘got my head round JS as an async lang’ at the start of this list***

1. Why it’s good to declare variables first (if it can’t be avoided), then functions, then code where something happens at the bottom. It’s better to pass variables between functions by serving them as arguments then calling functions with no arguments

1. ::after can be used for tooltips. Hide elements using the hidden attribute in html or visibility property in css

1. How to set an event listener for multiple elements

1. When declaring CSS styles, a space between an element and class means it behaves differently: H1.new-class styles h1 if it has the new-class class, whereas H1 .new-class (with space) styles any element within the h1 element which has .new-class class ***// this blew my tiny mind; CSS is ridiculous enough and now you’re telling me that something as inconsequential as a space changes what it does?!***

1. CSS vs Sass nesting ***// also mind blowing***

1. What ‘semantic’ means in the context of html. That I shouldn’t use ids for styling cos of specificity issues. What different http methods do

1. The map() method creates a new array with the results of calling a provided function on every element in this array ***// I copied this from the internet. I only really understood what map does 3 months ago***

1. YOU CAN COMMIT CONSTANTLY AND PUSH INFREQUENTLY. DON’T ONLY COMMIT ONCE A DAY THEN GET MAD WHEN YOU LOSE IT ALL. ***//another sad day***

1. Make clean and install again if fonts not loading ***//and this was the exact moment I became a developer***

## What I learned in December 2017

(Disclosure — this list is a lot less entertaining than the last one)

1. <sup> = superscript tag

1. git cherry-pick [commit_id]

1. > is the descendent selector in CSS and only applies styles to an immediate child. So declaring a style for > ul will only apply styles to a <ul> that’s an immediate child

1. parentNode.querySelector() as opposed to document.querySelector() — looks just within the parent node rather than the whole DOM — great for when there are lots of repeat elements on page and you only want to interact with one of them

1. If you need to remove a timeout that you’ve previously set, you need to assign it to something when you set it, so that the clearTimeout has a reference: 
so set the timeout with:
const autoCloseTooltip = setTimeout(() => {this.tooltip.close()}, 2000);
Then clear it with:
clearTimeout(autoCloseTooltip);

1. Canned queries, sometimes known as corporate reports or documents, are predefined queries. In most instances, canned queries contain prompts that allow you to customise the query for your specific needs*** // back to the old copy paste from google… I don’t actually have a clue what a canned query is***

1. Introduction to CSS grid using [Grid Garden](http://cssgridgarden.com/)

1. __dirname = back to project root (directory name of current module)

1. Path = list of locations on your machine that you want files to be installed to. Strings separated by colons

1. Async await function, instead of a promise with multiple .then, it uses try catch blocks ***// just as I feel pretty comfortable with promises, JS switches up on me***

1. ***// A load of MongoDB stuff that is too dry to list individually***

1. Using {{#each}} in handlebars; when iterating over properties {{@key}} refers to property name, and {{this}} refers to property value

1. Returning a console.log() will always return undefined

1. white-space: nowrap in CSS stops items wrapping when resized responsively (e.g. preventing “Financial Times” breaking onto separate lines)

1. FLEXBOX. IT KINDA MAKES SENSE.

1. Getting more comfortable with destructuring

1. To only add parts of your changes to github do: git add -p, then respond y or n for each bit

1. CSS specificity is not just a black hole of dark magic. Some things have more weight than others (principally IDs getting the most importance) WHO KNEW?! ***// I learned this one thanks [to an awesome post](https://medium.com/@frontendium/css-the-cascade-specificity-7f4ad354e58c) by my colleague Gabi. Also interestingly, number 25 in my 2016 list was the first step in understanding this so we have come delightfully full circle!***

## What I learned about learning

A few things jumped out at me as I was reading back through my list of learning, and I’m glad you like lists cos here’s another one:

1. At least as much of what I’ve learned over the last year is around tooling and dev processes as it is about actual code — git, for example, is referenced 120 times in my list.

1. It’s funny how interchangeable those lists look — I learned some pretty gnarly stuff a year ago, and I’ve learned some really basic stuff in the last 30 days. And it’s not just me — my brilliant tech lead, who has years of experience on me, looked over my shoulder the other day as I was adding something to the list and said ‘funny, I just learned that yesterday too!’

1. Which leads me onto my next point — this list covers a lot of the things I’ve learned over the last year, but it doesn’t *really* represent my progress as a developer. The list is made up of little snippets of knowledge, but their accumulated weight is much more significant. To me, progress is much more about my confidence and comfort with code and starting to recognise patterns in development than it is about learning a new fact every day.

1. Lastly, those first few months of learning were amazing — I remember saying to someone jokingly ‘right now, every day is the best day of my life’, and it was kind of true, because every day I would come across a seemingly insurmountable code based obstacle, and by the end of the day I’d solved it, and that felt so great. 
The flip side of that feeling is that every time I opened up a new directory, waves of fear and panic washed over me because I recognised hardly any of the JavaScript in the files (or even how to navigate the files) and that left me in a constant state of anxiety.
I don’t feel like I’m scaling mountains every day now, but I’m also not constantly on the edge of a nervous breakdown, so that’s an ok trade off.

**P.S.**

They really weren’t lying about naming stuff being the most difficult part of development. My first Medium post and the hardest bit was coming up with the title…
