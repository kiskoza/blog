---
date: 2018-09-18
layout: post
title:  "The Riddles of Közösségi Qpaweb"
---

Hello there!

Recently I created a new Jekyll site out of mockery called [Közösségi Qpaweb](qpaweb-github). The purpose of this site was to show the organizers of Schönherz Qpa that it's very easy to create a webpage with all the functionality they need, so why they were not ready yet? (Hint: it has a lot of feature requests normally...)

I wanted to act as fast as I can, because they could have finished coding any minute and then my prank would have became outdated. I didn't have much time, so I started up a simple [Jekyll][jekyll-url] blog with my first "News". Then I started to add "fully functional features".

Usually there are riddles on the real Qpaweb which could be solved with you friends - this is my favourite part, so it was clear I wanted that working. However I had to face some serious problems: I don't have (and I don't want) authentication, authorization or even any server side code. So all of it should be happening in the client's browser.

Then I got a list what should be accomplished to feel like it is real:
1. need to check if the solution is okay
2. remember if the user already solved one of the riddles
3. do not make it easy to cheat

The first point is easy - just render the soluti... wait what? I realized I cannot send the solution to the client, I would be too easy. Somehow I have to tell if the user guessed it right, so my solution was to upload only hash of the solution instead of the solution itself. Problem solved: I can check if they're right but they cannot see the answer.

The second one was a little bit more tricky for me: I usually send everything to backend and save to a database - not this time. Then I realized there's a tool that was invented for this situation: [Local Storage][local-storage]. I ended up saving a key-value pair for every solved riddle. The key should tell us which riddle are we talking about and the value should contain if the current user has solved it.

And that's where the third point comes in: I wanted a system where a simple page reload could bust out cheaters. To accomplish that, I saved the guess to Local Storage before creating the hash, so it could be reevaluated every time we want to check if the user already solved the riddle. This way manipulating the Local Storage only works if the user knows a string which hash is the solution - and that's what the user is looking for.

[jekyll-url]: https://jekyllrb.com/
[local-storage]: https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage
[qpaweb-github]: https://github.com/kiskoza/qpaweb/
