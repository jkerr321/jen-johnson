---
title: "This week I learnt… that sharing is caring!"
date: 2019-01-07T19:36:15+01:00
draft: false
---
## A little idea that got a bit bigger and more fun in 2018

![](https://cdn-images-1.medium.com/max/2000/0*VIReZdHXSVD5ctMK.png)

This post is a loose follow up to [one I wrote a year ago](https://codeburst.io/one-year-on-as-a-new-developer-ebed0a36692) about recording what I was learning each day as a new developer — at the time some of my teammates and I were keeping a record for ourselves whenever we came across something new. Soon after, in one of our retrospective meetings, we discussed that although it’s brilliant that we all learn so much all the time it would be great if we could make it a more shared experience.

And so was born the creatively titled ‘**This week I learnt**’, which was quickly and snappily abbreviated to **TWIL**: a team effort to keep a note of new things we’d learnt and let everyone in the team share in that learning.

The rules were simple:

* Every Friday each team member would post a list of the things they’d learnt that week in the team Slack channel

* The whole team was encouraged to take part — it wasn’t just a dev thing, and the things that were learnt didn’t have to be work related

* The only stipulation was that the post was preceded by ‘**TWIL**’

Without further ado, here are some of our favourites from 2018*:

* **TWIL** You can use dynamic key names within JS Object literals:

    var customKey = ‘foo’;
    var obj = { [customKey]: ‘bar’ };
     
    console.log(obj); // { foo: ‘bar’ }

* **TWIL** that Oxford university is older than the Aztec Empire.

* **TWIL** that self is a better way of accessing global context (it translates to non-web-based JS a lot easier for example): [https://stackoverflow.com/a/36854071/113721](https://stackoverflow.com/a/36854071/113721)

* **TWIL** that you can call .filter(v => v) on arrays and it will filter out null values (or anything that returns non truthy, so 0 and ”” would get filtered out too). For example: [‘foo’, null, ‘bar’].filter(v => v) will become [‘foo’, ‘bar’].

* **TWIL** that promises can be explained using burgers: [https://kosamari.com/notes/the-promise-of-a-burger-party](https://kosamari.com/notes/the-promise-of-a-burger-party)

* **TWIL** that flamingos are pretty badass… they can sleep standing in water that freezes their legs in position, can survive in water so salty it would strip your skin off, and can drink boiling water (without dying, I should add): [http://www.dw.com/en/flamingos-are-tough-as-hell/a-39552441](http://www.dw.com/en/flamingos-are-tough-as-hell/a-39552441)

* **TWIL** that when you push a new branch to GitHub from the command line, you’ll now notice a URL within the output which you can copy in order to quickly open a new pull request: [https://blog.github.com/changelog/2018-09-10-pull-request-url-output-in-the-command-line/](https://blog.github.com/changelog/2018-09-10-pull-request-url-output-in-the-command-line/)

* **TWIL** that the FTSE used to be owned by the FT.

* **TWIL** that body = “subscriptionSelection=Premium Digital” can be used instead of body = { subscriptionSelection: ‘Premium Digital’ }. The former is form encoded, the latter is JSON encoded. This was really useful for me when mocking form content sent in a post request for a unit test. The test wasn’t working when I used the JSON encoded format because Express needs a JSON parser to handle it. Using form encoding meant that I didn’t have to require in more stuff just for the sake of testing.

* **TWIL** that “Achoo!” is particular to English speakers. It’s “achoum” in French, “hakashun” in Japanese, and “deaf people just make the sounds associated with the movement of air a sneeze represents”: [https://www.popsci.com/science/article/2013-07/why-deaf-people-dont-achoo-when-they-sneeze](https://www.popsci.com/science/article/2013-07/why-deaf-people-dont-achoo-when-they-sneeze)

* **TWIL** that If you don’t provide an initialValue to a reduce function, it uses the firstValue of the array instead. Lead me to question my sanity when I was reducing an array with 3 values and my log was only being printed twice.

* **TWIL** that the http code 307 for temporary redirect cannot be automatically redirected to using a different request method than the original request — so if the original request was a POST the redirect must also be a POST. Unlike 303 see other for example.

* **TWIL** that I really love roasted cauliflower.

* **TWIL** that an autoprefixer is a MAGICAL thing that prefixes your CSS with the relevant — webkit etc prefixes so that it works optimally in all browsers. Learning this saved me so much pain!

* **TWIL** that you can specify multiple fonts in your CSS font-family selector. The browser will try the first one, if that one isn’t available the second, and so forth. In this example: font-family:”Lucida Console”, “Courier New”, monospace; the browser will try and use Lucinda Console, then Courier New if that fails, then lastly any monospace font it has available. This is good if you’re using a funky font that isn’t supported in all browsers, but you want to preserve the essence of the style (serif etc) in the browsers that don’t support it.

* **TWIL** why you shouldn’t use target=_blank and it’s really interesting: [https://mathiasbynens.github.io/rel-noopener/](https://mathiasbynens.github.io/rel-noopener/)

* **TWIL** that ‘ft.com/foo’ redirects to ‘ft.com/bar’ (causing very confusingly failing tests!).

* **TWIL** (courtesy of [colleagues in a different slack channel]) that using a for..in is quicker than using Object.assign for merging object properties. Also, the object spread operator ({… foo}) uses Object.assign under the hood.

* **TWIL** that TWIL stands for ‘This Week I Learnt’ and not ‘This Wot I Learnt’.

* **TWIL** that Favicon is short for ‘Favourites Icon’. The name is derived from the bookmark list for Microsoft Internet Explorer which is called Favourites list. When you add a site to your Favourites list, Internet Explorer (version 5 and above) asks the server if it has a file called favicon.ico. If present, this file will be used to provide an icon that is displayed next to the bookmark text.

* **TWIL** that opacity set using the opacity property in css is always inherited by children (it’s like the display property in this regard). To avoid this happening, use RGB values with transparency instead(e.g. background-color: rgb(0,0,0,0.5)).

* **TWIL** that the concept of sharding originally comes from a game called Ultima: [https://youtu.be/KFNxJVTJleE?t=306](https://youtu.be/KFNxJVTJleE?t=306)

* **TWIL** that the handlebar plugin {{debug}} is great for writing unit tests.

* **TWIL** that if you want to figure out if any number is divisible by another, add up the individual digits and if that number is divisible, then the initial one is too. e.g.: For 117 / 3: 1 + 1 + 7 = 9 which is divisible by 3, therefore 117 is divisible by 3 as well.

* **TWIL** ADAM introduced a BUG and BROKE EVERYTHING.

* **TWIL** that ‘Mr. Brightside’ by The Killers never left U.K. charts. In fact, it was among the top 50 in 2017: [https://noisey.vice.com/en_us/article/pg78ky/the-killers-mr-brightside-not-left-uk-charts-since-2004](https://noisey.vice.com/en_us/article/pg78ky/the-killers-mr-brightside-not-left-uk-charts-since-2004)

* **TWIL** that CSS specificity is not just a black hole of dark magic. Some things have more weight than others (principally IDs getting the most importance) WHO KNEW?! (I see now that everyone knew, but I missed this entirely). Also, for bonus awesomeness I learned this via our own Gabi VK: [https://medium.com/@frontendium/css-the-cascade-specificity-7f4ad354e58c](https://medium.com/@frontendium/css-the-cascade-specificity-7f4ad354e58c)

* **TWIL** that Cloudflare uses lava lamps to come up with random seeds for encryption hashes: [https://www.youtube.com/watch?v=1cUUfMeOijg](https://www.youtube.com/watch?v=1cUUfMeOijg)

* **TWIL** that A really good way to get your head round CSS grid is with [http://cssgridgarden.com/](http://cssgridgarden.com/)

* **TWIL** that attaching a huge kite on cargo ships can decrease fuel consumption by 30%: [https://en.wikipedia.org/wiki/Kite_applications#Cargo](https://en.wikipedia.org/wiki/Kite_applications#Cargo)

— — —

There are a few things that I really liked about doing **TWIL** posts:

* Writing a note for someone else is different to writing a note for yourself — a hastily scribbled few words to yourself has to be expanded and fully explained if someone else is going to understand it. In writing points out in actual English sentences I often found gaps in my own knowledge which I had to fill in, and I ended up with better notes for myself by default

* Sometimes we learn things incorrectly — sharing points with the team is a great way to validate what we’ve learnt and get corrected in a safe environment

* The posts often spark a conversation — either because we’re impressed or excited about what our team mates have learnt and we want to tell them so, or because the points touch on our shared interests, or because they’re just downright interesting or hilarious

* Seeing a ‘**TWIL**’ pop up in the channel makes everyone happy — they’re fun!

Perhaps surprisingly, the original purpose of our **TWIL** posts — taking what our teammates learn and adding it to our own knowledge — has ended up being a secondary benefit. It’s really interesting seeing those snippets of knowledge each week but it’s also impossible to retain all that information and I promptly forget (and often relearn later!) many of the points that are shared.

Like all things we try as a team, It’s not a perfect system — over the course of the year we’ve posted less and less often, sometimes only once a month, and the posts probably became too code heavy to the detriment of the non developers on the team. But on balance the benefit of taking a few minutes each week to reflect and chat with our colleagues about what we’ve learnt has definitely had a positive impact, including those benefits we hadn’t intended at all when we set out; we’d recommend any team have a go at something similar.

*FT folk — if you’d like to see a full list of what we learnt in 2018 [you can do so here](https://docs.google.com/document/d/1WvCCNGyOMsZlHMtOz8iMtmZw2RoP9Y2x9seUISjNz6E/edit?usp=sharing)
