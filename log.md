# 100 Days Of Code - Log

Hi, I'm Julie and I'm writing a text-based, thinly-disguised trivia game in PHP. This is my 100 Days of Code log.

#### Blog: [https://digitalurbanite.net](https://digitalurbanite.net)

### Day 1: September 4, 2018
#### Hours spent coding: ~1

**Today's Progress**: Tackled true email uniqueness, including dealing with an issue where my email stuff was coming in from POST as null. Fun fact: that was my renaming a variable to email1 and not changing it elsewhere. Also made a note to make PHP check errors look like JS check errors for consistency.

**Thoughts:** It was tough to deal with PDO errors and array errors and missing variable errors before 9am, not being a morning person and all. Still, I put in a good hour and solved one of the issues I'd been facing. Will definitely need to double-check that I haven't broken anything, though.

**Link to work:** [Instagram post](https://www.instagram.com/p/BnTf_bCBMOP/)

### Day 2: September 5, 2018
#### Hours spent coding: ~3

**Today's Progress:** Despite not being able to integrate SendGrid at this time (401 errors -- maintenance at SendGrid? Will revisit this.), I am super proud that I was able to create a validation flow. User clicks on the link in their email (the email I couldn't send out because SendGrid isn't integrated yet, but I cheated and created a clickable link post-user registration) and gets taken to a validation page. On the validation page, which has the token and user ID in the URL as parameters, the code will:

- check to verify that the token and the user ID match
- if they match, it will change the verified column from 0 to 1 (false to true)
- if they match, it will also generate a new token and update the token field for the user, forcing an expiry of the emailed token

**Thoughts:** I do not know nearly enough about Composer to be messing around with it. I don't know if my `vendor` folder will persist once I bring my containers down (unlikely) and I don't know how to make sure it gets installed upon bringing up my containers. Further research is needed here. I also need to get SendGrid to work, which is sort of intimidating because it's relying on the whole Composer thing. I mean, I don't technically *need* Composer, I could just try to install it singly or whatever, but that seems silly. Hence, more research needed.

The annoying thing is that getting these errors and such really took the wind out of my sails. At least I had the actual validation workflow to fall back on. MySQL issues ran rampant, but I fixed them all. Should probably look at refactoring the validation process -- can I make it more efficient? It feels inefficient right now. Still, I got the thing to work and that feels awesome!

**Link to work:** [Instagram post](https://www.instagram.com/p/BnX0M2wBDsl/)

### Day 3: September 6, 2018
#### Hours spent coding: ~4

**Today's Progress:** The registration process is essentially finished. All the JavaScript and PHP checks are complete, there's even some CSS to style things sort of nicely. I do need to revisit the PHP error checks to make them look consistent with the JavaScript ones, though. Still, the big thing tonight was finally properly integrating with SendGrid! I sent emails! And it was actually pretty easy! I ended up having to define my API key as a global variable, though, which I am not thrilled about, so I'm going to have to revisit that at some point.

While I'm still not sure what I'm doing with Composer, I made some edits to my `composer.json` file and that seems to be working. So... yay? hahaha, more things to review eventually.

The voluntary blacklist function wasn't bad either. There was just a lot to pack into the function. I had to snag the email address (the unique one) from the user by virtue of the user ID. Then I had to insert it into the blacklist. Then I had to delete the user from the user table. Then I had to delete the token from the tokens table, lest someone somehow use it for a nefarious purpose. I definitely need to add an expiry to tokens of like, 24 hours.

I should also probably ask them if they're absolutely certain they want to delete their account, but the basic functionality works and that's amazing.

**Thoughts:** I have never been so thrilled as to receive email from myself as I was on the various occasions tonight when I managed to get SendGrid to send the emails I was attempting to send out. Phenomenal. I am super psyched about this on so many levels. I have a lot to revisit and clean up, but I can _do_ this! When I think back to where I was in January, just messing around with the Q&A portion of things and struggling to get it to work with PDO later in the year... I've come a long way. I've learned a ton. And this is just Day 3 of #100DaysOfCode. This is going to be an amazing process. I know I won't accomplish a lot the way I did tonight _every_ time I sit down to code. But that I can make even incremental progress is awesome.

Next up is the login process, which, to be honest, is terrifying to me. But I'll have the whole weekend to play with that. :D

**Link to work:** [Instagram post](https://www.instagram.com/p/Bnaf94khJUS/)

### Day 4: September 7, 2018
#### Hours spent coding: ~3

**Today's Progress:** Registration was finished, right? I said so myself yesterday.

Fun fact: it wasn't exactly finished.

I spent at least two hours trying to figure out why my passwords weren't matching.

The issue was that I'd renamed my `password` field to `password1`. Did I change that when I set the variables from the `$_POST` data? No. No, I did not. So it was taking an empty password and hashing that, which is why my password_verify attempts kept failing.

_*sigh*_ Live and learn, I guess.

Speaking of learning, even though I learned about sessions and cookies in my PHP I and PHP II courses last year, I'm still uber fuzzy on them. But I set up a session for logged-in users and non-logged-in users go back to login. So all of that works and I can log in successfully. Still a lot to do to clean up this functionality and make it look pretty and such. Also, like, what can a logged-in user even do? I'm going to have to set up admin flags too. So it's far from finished, but it's functional, and I feel like that's the toughest part of this login thing. Everything else should be tweaking and refining.

**Thoughts:** All day long, I was really, really excited to get to code. And then I sat down to do it and I was like "ehhhhhhh." But I persevered and soon got really into it. My 3 hours of coding took place over about five hours, so I took a few breaks here and there, but definitely was heads-down on this stuff for at least 90m straight at one point.

The password thing is so infuriating to me. That it took me over two hours to figure that out is maddening. Everything I'd been doing was fine, didn't need changes, etc, it was that what was being stored in the database was not what the user entered. Ugh. So glad to have found the bug.

Also, it still makes me excessively happy to have email delivered to me by SendGrid. :D

Gonna work on refining things here -- and that includes not accidentally adding my vendor directory to GitHub. I suppose I should investigate .gitignore, eh?

Oh, AND! And. It was super exciting to merge my registration branch to master and then create a new branch for login.

That is all. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/BndXW9qBWdx/)

### Day 5: September 8, 2018
#### Hours spent coding: ~2

**Today's Progress**: Kind of a one step forward, two steps back kind of day. I added a check to make sure a token isn't generated for a user who hasn't properly been inserted into the database and also send the user a message asking them to contact us.

What I got hung up on was a check verifying that:
a) a user exists
b) they're a verified user
c) their password matches

I have a) and c) down, but I can't figure out how or where to add the verified check. I need to let this one percolate a bit.

I also got a lot of planning done, feeling better about having some kind of "energy" that various player actions use. I suspect I'll need to math some stuff out, which I'm not particularly looking forward to.

I did plan out what should be accessible to various users (normal users vs. admins) and so coding those functions for both shouldn't be terribly difficult. My planning today has meant that I should be able to code without too much more planning for the next week.

**Thoughts:** I posted to [the blog](https://digitalurbanite.net/so-much-progress) today, so you can check that out for more thoughts. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/BnfgOJlBKFa/)

### Day 6: September 9, 2018
#### Hours spent coding: ~1

**Today's Progress**: Oops, totally forgot that my _original_ goal today was to make sure I have a validate check on login. I want users to validate their email address before they can log in. That took me maybe 20 minutes, hah, so I then decided to fix token generation and implement the expiry of tokens and make sure that tokens updated properly. I wanted to implement a 24h expiry on all tokens and I wanted to update tokens when:

- a user validates their email address
- a user logs in

I also had a bit of a wonky function wherein the validation link was sending the _token's_ ID rather than the associated _user_id_, so I fixed that up, too, to ensure validation mails worked regardless of how many token records there are as compared to user records.

**Thoughts:** Short day today, only about an hour or so on the items in question, but I set out to accomplish those very specific things and I did it.

**Link to work:** [Instagram post](https://www.instagram.com/p/BnhelKBhmC6/) - note that token id 7 (aka user_id 9) has three separate tokens in the shot, queried pre-validation, post-validation and post-login.

### Day 7: September 10, 2018
#### Hours spent coding: ~3

**Today's Progress**: Was up too early with a headache, so I decided to code. I coded for about an hour and inserted last login to the user table for the login flow. This is important because I'll have a maintenance routine at some point that will delete users after 45 days of inactivity. And will email them at 30 days and at 44 days of inactivity. So having the last login date will be pretty handy!

Planned out and started implementing the change email function. It's definitely not done yet -- it's not yet functional -- but I'm sure that's just because I'm too tired to see the mistakes that must be in there.

**Thoughts:** I definitely don't like coding in the morning, but it was nice to know that I didn't _need_ to code this evening for the challenge, even though I did anyways.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bnkv7SehW2l/) - this is where I currently error out on the change email workflow. Something to dig into tomorrow or later this week.

#### ETA: Week 1 complete and with about 17 hours of coding done. That's like a part-time job. On top of my actual job. I'm kind of impressed, honestly, and the week flew by.

### Day 8: September 11, 2018
#### Hours spent coding: ~1

**Today's Progress**: Tonight was all about the change email function. It's not at all working, but the foundation for it is there. The issue is that I'm getting errors, so tomorrow, I'll want to debug and see what's going wrong. Made a lot of progress, though, and learned how to send to multiple recipients with SendGrid.

**Thoughts:** Wasn't really feeling like coding after I napped on my couch this evening, but I forced myself to get up and get going. Once I started, I got into it pretty quickly!

**Link to work:** [Instagram post](https://www.instagram.com/p/BnnWiDxBkql/)

### Day 9: September 12, 2018
#### Hours spent coding: 1h15m

**Today's Progress**: Finally tracked down my issues with my change email functionality and now it all seems to work. The code is definitely ugly and could be a lot nicer, but refactoring that is a headache for later. (I did put it down in my task manager software, so I won't forget about how ugly it is.)

**Thoughts:** I've had a low-grade headache all day, slept like crap last night and it's 1:39am as I write this, but I'm glad I got an hour and a bit done tonight. If nothing else, figuring out my change email functionality was totally worth my time. I'm really not great at the whole "consistency" thing -- my nature is to procrastinate and then do All The Things At Once -- but this challenge obviously doesn't lend itself to "code once for 14 hours every two weeks". And I'm glad it doesn't. Also, the fact that I only started coding after midnight on the 13th but am still counting it for the 12th is pretty cool. I really do take it as "between waking up and sleeping" and that works so well for me. I never think "oh, it's too late, I've missed a day!", which is vital to me not being discouraged.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bnp54TyhFyh/)

### Day 10: September 13, 2018
#### Hours spent coding: 1.5h

**Today's Progress**: Used my extremely ugly change email code as a base for the change password function. It works! Should refactor, but it works.

**Thoughts:** The headaches and poor sleep continue. Hoping tonight will be better, because I think I could have achieved this functionality in half the time, if my brain were properly rested.

That said, I'm pretty pleased with the progress I've made so far. Should probably do the log out functionality next and then... maybe... I can start in on _the game itself_?!

**Link to work:** [Instagram post](https://www.instagram.com/p/BnsVrK0B6fu/)

#### Blog: [https://digitalurbanite.net](https://digitalurbanite.net)

### Day 11: September 14, 2018
#### Hours spent coding: ~1.5h

**Today's Progress**: Added logout function, made the login page pretty, added some profane names, added some session checks, created a script to run on the MySQL CLI to create three test users as needed. Then, merged the login branch to master. No big deal...

**Thoughts:** Huge deal. I have the question functionality working, I have registration, login, logout, change password and change email functions working. We're fast-approaching the point where I'm going to actually be coding _the game itself_. :O Very pleased with the more than 22 hours I've put into this over the last 11 days. Things are paying off. Additionally, I no longer feel as though I'm entirely unqualified to code this. :D

**Link to work:** [Instagram post](https://www.instagram.com/p/BnvHq4FhsJ6/)

### Day 12: September 15, 2018
#### Hours spent coding: ~2

**Today's Progress**: Did a lot of planning things out on paper! I really need to organize my tasks (either pick Trello or the other task-tracker I'm using). I also started the gameplay, working out that people will need a check to not see the game intro if they've already seen it, so that's starting off okay.

**Thoughts:** It's challenging to write creatively as well as write code. Must confer with my friend L about the story stuff when I get a chance. Still, right now, it's all placeholdery stuff. Also, it's equal parts terrifying and exhilirating to have a branch called `gameplay`.

**Link to work:** [Instagram post](https://www.instagram.com/p/BnxwJKChb4W/)

### Day 13: September 16, 2018
#### Hours spent coding: ~1

**Today's Progress**: Realized I could use AJAX calls to pull in the introduction content without needing to create like six or eight or ten separate pages, so I did that.

**Thoughts:** Wasn't really feeling it today, couldn't really get anything started, but was glad I was able to implement AJAX to pull text on the click of a button. What's kind of neat is that I'm using parts of five of my six classes from my diploma. HTML 5 and CSS 3, of course. SQL? Constantly. PHP I and PHP II? Yep. JavaScript for all kinds of form validation and now AJAX for the calls for the text. The only thing I need to incorporate is Java to have all six of my classes represented in this project. But, since Java was my first real programming language, I suspect that each time I do an `if` statement or a `while` loop, Java's getting represented anyway. ;)

**Link to work:** [Instagram post](https://www.instagram.com/p/Bn0EcQihj1b/)

### Day 14: September 17, 2018
#### Hours spent coding: ~1

**Today's Progress**: Was up inexplicably early, so decided to code a bit. Didn't get too much done, just added more intro stuff and prepared my old test PDO question file to be thoroughly rewritten to work with the intro.

**Thoughts:** I just want to go back to bed, hahaha. Did not have the brain power to sit there and rewrite all that needs rewriting. It'll percolate, though, and I'll come back to it tomorrow or something. In the meantime, this completes Week 2 of #100daysofcode! Done about 25 hours of coding in that time, which is substantially less than what I was on pace for after Week 1. Still, I've made a lot of progress and done a fair bit of planning. Things are going well, if a little slowly.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bn1F3PZBrtb/)

### Day 15: September 18, 2018
#### Hours spent coding: ~2.5

**Today's Progress**: Worked on intro stuff, specifically getting my question/answer functions to actually work within the context of the intro. Like, it all needs to be rewritten because I just scripted it freehand and I should really, you know, use a separate file where I store my classes and functions. Of course, I feel dumb, because I spent so much time tonight wondering why the MySQL calls wouldn't work. Well, as it turns out, I was querying the database with my USER user, not my QUESTIONS user, so of course the USER user doesn't have access to the QUESTIONS database. Fun fact, this tripped me up in July, too. I'm grateful it took me less than an actual week to figure it out this time. That said, I smacked my forehead with my palm so hard that it still smarts, even several minutes later.

**Thoughts:** I hate that I made the same mistake and didn't immediately realize it. Ugh. Also, this is vaguely annoying stuff, but I know it needs to be done. Getting ever-closer to getting the intro to work. Once that works, then we can actually launch into real gameplay, which will require another version of the Q&A system I'm writing now. It's all gonna be finicky stuff, but once it works, that's like, half the battle. (Insert GI Joe motto here.)

**Link to work:** [Instagram post](https://www.instagram.com/p/Bn5JaMMhChE/)

### Day 16: September 19, 2018
#### Hours spent coding: ~2

**Today's Progress**: Figured out the database stuff and permissions through what seems like a lot of trial and error, but now my data is trapped in an array and I can't pull it back through the damn return statement, because it nulls out _and I don't know why_. Ugh.

**Thoughts:** So frustrated to have worked through the DB user permission issues and be faced with what is likely something very easy to fix but I can't find the solution. Yet. I'm looking forward to taking most of next week off while I'm out of town on a work trip. I really need to clear my head, I think.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bn70tWEBZxf/)

### Day 17: September 20, 2018
#### Hours spent coding: ~1

**Today's Progress**: Discovered how to use `list` to rescue my data that was trapped in an array that kept nulling out on return! YAY! Then discovered that I basically need to rewrite a bunch of stuff on the `POST` version of my questions. Well, that'll be this weekend's project, I guess.

**Thoughts:** Felt great to figure it out with the `list` thing. Didn't feel so great when I realized I'm super rusty at even writing a simple `while` loop. I need to give things more thought, so I'm calling it for the night and can tackle it on the weekend.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bn-WyZfBwR-/)

### Day 18: September 21, 2018
#### Hours spent coding: ~1

**Today's Progress**: Struggling with getting the right question ID passed back and forth through things. I couldn't iterate it since it was a string, so I juggled the type to an integer and that seemed to work, but it only works for the first go around on the `POST`. I'll figure it out, I'm sure. But probably not at 3:45am.

**Thoughts:** I feel like I'm close to getting this. But what's discouraging is that I need to modify this to make it work for the actual game and not just the intro. It feels kind of silly to kind of do it twice? We'll see. Maybe it won't be so big of a difference.

**Link to work:** [Instagram post](https://www.instagram.com/p/BoBTtc3hQUJ/)

### Day 19: September 23, 2018
#### Hours spent coding: ~2.5

**Today's Progress**: Took yesterday off, even though I'm taking most of this week off while I'm out of town for a work thing. It really helped me be able to take a step back and better figure out what was going on with my code. Tonight, I continued to work on my introduction section and I'm pleased to say you can now get through that section. If the user fails that section, well, that still needs work. More thought, then more work.

**Thoughts:** I felt badly taking yesterday off, but it ended up being really good for me. When I sat down to code tonight, I was more energized than I had been in recent days. Gotta do some planning next!

**Link to work:** [Instagram post](https://www.instagram.com/p/BoGGRedB-zf/)

### Day 20: October 1, 2018
#### Hours spent coding, er, researching: ~1.5

**Today's Progress**: Well, that was a long break. Work trip was great, but I came back and had no idea what the hell I was doing in terms of my code. I had no idea where I'd left off. So I took time tonight to re-acquaint myself with my code and figure out what I need to do next. And then researching that a bit. I'm going to have to use cookies to store question ID values to help try to prevent duplicates. I have no idea if this is going to work and, worse, I have no idea where to start. But I'm relatively certain I'll have to use cookies to achieve this.

**Thoughts:** I should have coded last night, but I didn't. And I should have done more tonight, but I didn't. Still, I at least know what I need to research and play with for the next few days. I'm hopeful I can actually start playing with cookies tomorrow night. I'm really making use of _all the things_ I learned in my PHP classes. Which, on the one hand is great, but on the other is scary, because some of the stuff we touched on was, well, super basic. Like, oh, I don't know, _cookies_.

**Link to work:** No link tonight, since I don't really have anything to show.

### Day 21: October 2, 2018
#### Hours spent coding: ~2

**Today's Progress**: Figured out that I'm definitely going to use sessions to hold the question ID values (and possibly category names?) in array format and check against that when drawing questions. The goal is just no dupes for like, 50, possibly 100 questions. MAYBE we'll just settle for nothing from the same category for like, 10 questions. There will be some repeat questions, I know there will be, but hopefully with the 4000 or so questions I'm hoping to start with, it won't be so bad? I also wrote up more text as to what the hell happens when you get the intro questions right. Then that sequence will end and will run a series of modifications on the user table:

- flag user as having done the intro
- flag user's location as being 0km on the river
- change the user's energy to be 100

Thereafter, the user won't have to go through the intro again and should be brought back to their same location -- I'll rewrite the location every question they get right as they advance.

**Thoughts:** It's definitely feeling like a slog, but I feel like I figured a couple things out tonight. I'm definitely worried about all the backend stuff that needs to happen on each question, but it's probably way too early for me to worry too much about too many DB calls.

Probably.

**Link to work:** [Instagram post](https://www.instagram.com/p/BodZBUVh0Tx/)

### Day 22: October 5, 2018
#### Hours spent coding: ~2

**Today's Progress**: I've been sick for the past few days, which has not helped me in my endeavour. Still, I felt somewhat human tonight and so I was able to stare at my code. What probably should have taken me something like 45m took me around two hours. And I spent a ridiculous amount of time trying to find a syntax error in my SQL statement that was caused by an errant comma. Alas, the woes of illness. Still, people should now be able to go through the intro and get to the proper game. Which I haven't exactly created yet. But that's coming next.

**Thoughts:** I'm glad I sat down to code tonight, despite the frustation and the congestion and the sneezing. I feel like I accomplished something.

**Link to work:** [Instagram post](https://www.instagram.com/p/BolW-BPhon-/)

### Day 23: October 6, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Didn't feel like doing much of anything, but sat down, reorganized some files and got started on what will be the very start of the game. The intro leaves you to make camp at the riverside and gives you a choice to fish for food or to try to gather food. Next up on the list: coding those functions. The fun bit will be using randomness to decide whether or not you get any fish or can find enough food while gathering to sustain you!

**Thoughts:** Still not feeling 100%, but glad I got some coding in. Thanksgiving with family tomorrow, but I've got Monday off, so more coding for sure!

**Link to work:** [Instagram post](https://www.instagram.com/p/Bon1CdGBsh_/)

### Day 24: October 7, 2018
#### Hours spent coding: ~3? 3.5?

**Today's Progress**: I got the fishing function to mostly work! We're talking:
- checkEnergy()
- checkFishSkill()
- goFish()
- updateEnergy()

It's not totally done, yet. I still need to update total fish caught, plus fish on hand, then need to make sure it doesn't yell at you about not having enough energy when, in fact, you **do** have enough energy, but that can wait until tomorrow.

**Thoughts:** I was... shall we say, not the most confident I've ever been when it came time to tackle the fishing functionality, but I am SO SUPER PROUD of myself and what I accomplished tonight. So psyched to have written a valid switch statement (first time since something like last December!) and so pleased I could mess around with my own user in MySQL so I could test the different breakpoints of the fishing skill multiplier.

This is definitely something I really enjoy about coding -- I often just break everything down into bits, which you kind of have to do in terms of functions, so my goal tonight was the `goFish()` function. And I got to it. And it works. And I feel phenomenal.

**Link to work:** [Instagram post](https://www.instagram.com/p/BoqsUoLBzzA/)

### Day 25: October 8, 2018
#### Hours spent coding: ~1

**Today's Progress**: Reworked the fishing experience a little. I do a specific call to grab the number of fish on hand before I even fish so that I can display the right number of fish on hand after a fishing attempt, regardless of whether or not it's successful. I also store the energy value in a variable, so I can display that and offer users a choice as to what to do next, given X energy and X fish on hand. I need to cap the number of fish at like, 5 or something, I think, so I'll have to edit that at some point. Will probably also have to create a `fishAge` variable or something. Because, uh, you probably don't want to eat a fish ten days from when you first caught it without refrigeration...

**Thoughts:** Feeling awesome. The math works, the logic works and I just need to think a bit more about the above scenario (too many fish, fish expiring, etc) and then fishing is totally done. Next up, gathering, which should be pretty simple now that fishing has been hammered out.

**Link to work:** [Instagram post](https://www.instagram.com/p/BoswXiGBvae/)

### Day 26: October 9, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: I worked on refining the fishing experience. You now see your fishing skill and your skill can update when you fish (12% chance, not dependent on actually catching a fish). I think something is wonky in my logic when you don't have enough energy, so I'll need to puzzle that out In The Future (tm).

**Thoughts:** And the second quarter of `#100daysofcode` starts! Can't believe I'm already a quarter of the way there. I almost didn't code tonight because I'd fallen asleep on my couch and I REALLY just wanted to go to bed, but I am definitely running out of days. I have 82 days until the new year and 74 more days of coding, so my "days off", so to speak, are super limited. I have no idea how I'm going to code *and* write *and* work during November...

**Link to work:** [Instagram post](https://www.instagram.com/p/BovvTeMBXkR/)

### Day 27: October 10, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Feels like a three steps forward and two steps back kind of day, in that I'm slightly ahead of where I was, but I can *see* and *feel* the technical debt starting to pile up. Really, I should just completely rewrite the fishing experience, but it all *works* right now, though it's kind of patched together. Definitely not my finest day of coding, but it does work. So there's that.

**Thoughts:** Sometimes, when I don't look at the very next thing to do in isolation, I get super discouraged. Like, all the checks I need to do at various parts of the game really just comes down to a few different functions, and if I'm reusing them, then I just have to write them once. So I need to remind myself that, even if something seems completely difficult, that it can always be broken down into smaller, more manageable tasks.

**Link to work:** [Instagram post](https://www.instagram.com/p/BoyHutmBuHh/)

### Day 28: October 11, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Still hate fishing with all my heart and soul, but I did put a cap on number of fish and I did edit the user table to allow for things like "has the user eaten today? What level of `wellFed` are they?" and these will come in handy in the future, since I'm hoping to give people less energy than the full 100 if they're not `wellFed` that day, so that people will have to be smart about what food they're eating and when, etc. Of course, have I even planned out the eating stuff? KIND OF? There's so much to doooooooo.

**Thoughts:** Gotta remind myself of yesterday's thoughts -- despite there being a lot to do, I gotta focus on the things that are relevant to what I'm doing right now and just write those functions, one by one by one.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bo06LIXhlBF/)

### Day 29: October 12, 2018
#### Hours spent coding: ~3 and 2+ hours planning!

**Today's Progress**: Had coffee with L and we nerded out together about my game for a couple of hours. She helped me to do math and gave me some great ideas, including adding aggregate stats, so I can come up with things like a "correct question response rate", which then factors into the cost of actions in energy in the game. Super exciting! After meeting with her, I spent time working on an admin menu (since I'm not necessarily going to display those stats to the public at large) and added a simple check for admin (I had a flag in the user table). I then used a function to pull out the contents of the new `data` table I created that will ostensibly count all of this stuff. Must confer with my friend, A, to see if I need to worry about database locks and such if there's a lot of traffic, because I'd rather know *now* that I need an alternate plan, before I've written too much.

**Thoughts:** Everything is super exciting and super overwhelming but also super awesome.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bo3pw8shRuW/)

### Day 30: October 13, 2018
#### Hours spent coding: ~3

**Today's Progress**: Didn't do a whole lot of *coding*, actually, but I did a lot of database stuff, which totally counts. :D I added a bunch of new questions (over 50 to do with European/UK capitals and 100 about the Montreal Canadiens). I also organized stuff with the database tables and the users for a better way to do aggregate stats. I'm hoping that the way I've done it will allow me to pull out stats such as the total questions asked and total questions answered correctly, **but also** things like which question is the easiest/hardest to answer? Which category is the easiest/hardest?

**Thoughts:** Even though I know *a lot* about the Montreal Canadiens, even I struggled to create 100 questions. I swear to God, more than 50% of the answers are either: `jose theodore`, `saku koivu` or `richard` (meaning either Henri or Maurice). My goal is to have ~100 questions on each of a variety of subjects before launch. Like, 4000, 5000 questions. I am currently at, uh, 293. So that's not intimidating at all! :'D

Also, wow, 30 days. Nearly a third of the way there and the first month is officially done!

**Link to work:** [Instagram post](https://www.instagram.com/p/Bo6JWA0BTWY/)

### Day 31: October 14, 2018
#### Hours spent coding: ~2

**Today's Progress**: By "coding", you should take that to mean "yelling at MySQL, Google Sheets, Google and Stack Overflow", but I got the import of a CSV file to work. Rather than having hundreds (and eventually thousands) of `INSERT` statements in startup MySQL scripts, I figure I can put CSV files in a directory for MySQL to import. It took me a long time to figure out how to:

- `LOAD DATA INFILE` at all, because the default Docker config has secure_file_priv on or whatever it is and that prevented me from importing
- not get MySQL errors once I COULD load the file because the formatting was wrong because I'm importing into a table that has an auto increment (fun fact: use `set category=null;` for the auto incrementing one
- determine if I should use `\r\n` or `\r` or `\n` to signify a new line (it was `\n`)

So a lot of finicky stuff tonight, but this means I can write questions in Google Sheets. More importantly, this means my friends and family members can write questions in Google Sheets! And I won't have to spend hours of my life copy/pasting these questions into `INSERT` statements.

**Thoughts:** Didn't do a lot of real coding this weekend, but that's okay. Also, I suspect that I'll be spending a bunch of my `#100daysofcode` time in November dedicated to writing questions in Google Sheets. That needs to get done and I can spend an hour or so every day writing questions for my game while I take part in National Novel Writing Month. I've been pretty freaked out at the prospect of coding daily *and* writing daily, so while it's not technically going to be "coding", it's going to be essentially populating my game's database. Which is, you know, important for the game. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/Bo8SF6CBrZ1/)

### Day 32: October 15, 2018
#### Hours spent coding/learning: ~2

**Today's Progress**: Was up inexplicably early, so I bashed my head against some Docker issues and decided to get myself the [Udemy Docker Mastery course by Bret Fisher](https://www.udemy.com/docker-mastery/). It's absolutely necessary, since I need to know how to properly customize my Docker images in order to allow for the importation of data in a CSV with `LOAD DATA INFILE`. And I'm not going to edit my config and restart MySQL each time I want to develop or deploy or any of that nonsense. Anyway, so I bought the course and went through the first couple of sections tonight. I'm into **Section 3: Creating and Using Containers Like a Boss**. The guy has a sense of humour. :) So far, I've learned more about Docker commands in a couple of hours than I did in the entirety of my PHP II class. Which, you know, that's fair. It was a PHP II class. The instructor gave us prepared Dockerfiles which I'm now trying to modify without understanding, and that's not working. Hence the course.

**Thoughts:** I was a little nervous -- and still am -- about the online course. I much prefer learning in person. I hope I'll stay motivated to get through it all.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bo-5JfCha6p/)

### Day 33: October 17, 2018
#### Hours spent coding/learning: ~1

**Today's Progress**: Just did about an hour's worth of lectures and stuff from the Udemy course I'm taking on Docker. Learned a lot about some of the CLI stuff plus Docker networking. Some of the commentary in the course has also reassured me about changing default stuff in various images, which is part of my goal in taking this course, so that's good. I'm just eager to get to it. Hoping to finish the course this weekend and get back to coding and such soon.

**Thoughts:** I took yesterday off because I was legitimately too tired to do anything. I was in bed by 10 and up at 4 for a couple of hours, but fell back to sleep for, oh, another five+ hours. Thankfully, I have flexible hours in terms of work. :D Anyway, hoping for more good sleep tonight. I've been having a hell of a time sleeping lately, so I hope my body has learned its lesson and that it's ready for a good night of sleep tonight. It's also not easy to code and figure things out when my brain has totally checked out, you know?

**Link to work:** [Instagram post](https://www.instagram.com/p/BpD0p_Uhrwp/)

### Day 34: October 19, 2018
#### Hours spent coding/learning: ~1

**Today's Progress**: Finished the third section of the Udemy Docker course! Networking makes my brain dribble out my ears, it feels like, but I got through it. Looking forward to the next section where we start to talk about images. My main goal here is to be able to customize the MySQL image so that I can upload my stupid CSVs containing questions, so that they get imported into the questions database, instead of writing thousands of ```INSERT``` commands.

**Thoughts:** It's been a slog this week. Not because I'm not interested, but because work has been more draining than usual. We hired new people and are growing our team, but that means some resources are diverted towards training, which means more work for me and a couple of other colleagues. I am _wiped out_, man. And I have to stop skipping days here! I have 6-7 days "off" left. That is not a lot. This daily thing is different from National Novel Writing Month, wherein I can skip seven days and then just write 11,669 words in a single day. (I've done it. I've done more than 17,000 words in a single day. I do not wish to repeat that. *BUT I CAN DO IT!*) I just can't do that with this daily thing. I've also realized that "learning" (courses, etc) don't count, according to the official rules, but screw it. I'm investing in knowledge now so I can code later. It's all going towards my project. The same goes for writing questions -- everything I'm doing needs to be done for this project and I'm using this ```#100daysofcode``` thing in order to move forward in my game. And I have done SO MUCH, which is kind of insane. And amazing. But mostly insane. ;) Anyway, hoping to do more this weekend and maybe I can get back to really coding come Sunday.

**Link to work:** [Instagram post](https://www.instagram.com/p/BpJXsFTB7t1/)

### Day 35: October 20, 2018
#### Hours spent coding/learning: ~5? 6?

**Today's Progress**: Got through almost three full sections in the Udemy Docker course and I now more thoroughly understand my own ```Dockerfile``` and ```docker-compose.yml``` files (which were created by my teacher in my PHP II class and I've been using for my own purposes for nearly a year). I have a lot of ideas on how to improve them and am looking forward to finishing off the last bit of this section about Docker Compose.

**Thoughts:** It feels really good to actually _understand_ things that exist in the ```Dockerfile``` and ```docker-compose.yml``` I've been using for so long. I understand about mounting volumes, setting environment variables, etc, so I'm pretty pleased to have that kind of understanding if nothing else. At minimum, I will now be able to properly modify these files to work better for me. Plus, I know how to avoid certain issues, such as what happened to me in late August/early September when I ended up arguing with Docker and MySQL for far too long:

[Instagram video here](https://www.instagram.com/p/BnNwHwOBEcG/)

What had happened then, which I recognize now, is that my ```Dockerfile``` was using the ```mysql``` image. When you don't define a version, it uses ```latest```, which is generally the latest stable branch of that software. I had been using MySQL 5.7.20 or something along those lines.

Guess what happened in August at some point?

MySQL 8 came out.

So my image requested the latest version and downloaded the new one. And borked my stuff. It took me ages to figure it out, but I had to add this to my ```docker-compose.yml``` file in order to ensure the MySQL users I'd created had permissions:

```command: --default-authentication-plugin=mysql_native_password```

Not knowing anything about Docker and images at the time, I was essentially stumbling around in the dark on that, but I figured it out. Probably should have taken my online course then, to be frank. ;) Anyway! I now know how to prevent things like that by _specifying version numbers_ for the images. Already, this course has improved my quality of life as a developer. Looking forward to the next few bits before I turn loose my knowledge on my existing ```Dockerfile``` and ```docker-compose.yml```!

**Link to work:** [Instagram post](https://www.instagram.com/p/BpMBvaaBO-n/)

### Day 36: October 21, 2018
#### Hours spent coding/learning: ~5

**Today's Progress**: Finished up the sections of my Docker course that are actually going to be useful for me right now and then proceeded to break my local environment by trying to be fancy. ;) It works again, but I still have some stuff to tweak.

**Thoughts:** It felt great to finish the part of the course I'd been most looking forward to and it felt very good to be working on my own ```Dockerfile``` and ```docker-compose.yml``` again. I even committed changes and pushed them to GitHub for the first time in days! That felt pretty great. I feel like I'm coming into this week ready to squash the Docker issues I'd been having and ready to move forward on the game itself.

**Link to work:** [Instagram post](https://www.instagram.com/p/BpONwUvB5Lw/)

### Day 37: October 22, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Struggled with Docker issues for about a half hour before I gave up on it for the moment, deciding to instead reacquaint myself with my code. I solved a division by 0 problem on my admin page, but then when I decided to show an admin menu option if a user is an admin, I get a too many redirects error if the user is _not_ an admin, so I need to remove the redirect from the admin check -- or write a second admin check. I also need to rewrite fishing entirely.

**Thoughts:** I have to write PHP more than every week, because I forgot two closing ```}``` tonight and both errors made me go "what the what?" That said, I did decide that the first session post-intro will be like a session and a half. You'll make camp and be refreshed and be able to actually start down the river, rather than only get a half session to start with. Gotta get them hooked on it, after all.

**Link to work:** [Instagram post](https://www.instagram.com/p/BpRCKxxhP2Q/)

### Day 38: October 23, 2018
#### Hours spent coding: ~2

**Today's Progress**: I _finally_ rewrote the damn fishing functionality, which I thought was awful and clumsy and I hated. It's now completely rewritten, which meant that I could write the _foraging_ functionality, which is almost identical to the fishing except for some math. I'm super stoked about it, too. I feel like I'm making true progress. Like... _maybe an alpha version will be out in December_? I have no idea. ANYWAY, I also wrote a ```switch``` statement for the different food types you can forage. Check it out in my Instagram post, linked below.

**Thoughts:** I **really** did not want to rewrite fishing. But I did. I sucked it up and pushed through and victory was at the end of the road, along with my foraging functionality. And now I feel satisfied and productive and I can hopefully go sleep the sleep of the dead.

**Link to work:** [Instagram post](https://www.instagram.com/p/BpTaeqfBTlw/)

### Day 39: October 24, 2018
#### Hours spent coding: ~2

**Today's Progress**: Refined a few things, including my ```docker-compose.yml``` to create a network so that my IP address doesn't randomly change whenever I bring up my containers. I also worked to add eating to the game. Realized it's a bad thing to have ```NULL``` in certain columns, because users will often get down to 0 food items, so I went through and added ```NOT NULL``` to a bunch of columns in the creation script. I _think_ that'll fix the issue I'm having with my ```foodValue``` not appearing. Because, you know, it's ```NULL``` and not ```0```. Sheesh, the number of times I have modified my users table as I went through this, even though I was **absolutely certain I had everything accounted for** when I started? It's, well, unnerving. Huge props to DB admins for their foresight.

**Thoughts:** Feeling good about moving through the intro. Once I finish eating, then I can get on to the sleep function, which will run a mini maintenance on the user. It'll check how well-fed they were (a certain amount of food will give 100 energy, down to 70 energy or so if you aren't fully well-fed), it'll restore some energy, it'll flag them as having completed the first night on the river and it'll unlock paddling, which leads to trivia questions.

I don't even have to write _too_ much for paddling, since I've already got the basic question format done. But I'm probably not thinking far enough ahead to anticipate all my needs. We'll see! Once that's done, the bulk of gameplay is done. I need my three trials, of course, but those are just going to be special kinds of events at certain benchmarks. More thinking required here, too.

Anyway, productive evening. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/BpWGgw_hf_u/)

### Day 40: October 25, 2018
#### Hours spent coding: ~2

**Today's Progress**: The good news is I got the eating fish and food functions working properly. Fun fact, the ```null``` issue was not, in fact, caused by the column stuff because it was ongoing.

Wanna know what it was?

I was calling ```$newFoodValue``` but I'd only defined ```$newfoodValue```. Yep. One casening error.

![facepalm](https://i.giphy.com/media/11zhT08QROSK64/giphy-downsized.gif "face. palm.")

So that sucked. I spent like 90 minutes trying everything from type juggling to rewriting the function. Nothing worked. Because "food" and "Food" are quite different, apparently. Which I know. Oof.

**Thoughts:** Kind of irritated with myself for not realizing that issue, you know, instantly. _*sigh*_ Hoping to tackle the end of the intro and on to the river proper on the weekend, hopefully. Hopefully. Maybe.

**Link to work:** [Instagram post](https://www.instagram.com/p/BnTf_bCBMOP/)

### Day 41: October 26, 2018
#### Hours spent coding: ~2

**Today's Progress**: Mostly some planning and tweaking to try to get the ```wellFedToday``` functionality to work properly. Had to plan out what changes I needed to make to the two eating functions so that ```wellFedToday``` is flagged and respected.

**Thoughts:** Slow progress tonight, but the planning helped! Would do more work but I've got to be up in the morning for family stuff.

**Link to work:** [Instagram post](https://www.instagram.com/p/BpbTRYwB6VF/)

### Day 42: October 28, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Added a new column to my user table, ```foodUnitsEatenToday``` to better help me calculate whether or not a user is ```wellFedToday```. Then, I added some conditionals to various eat commands (and eat pages) to make sure players are respecting the supplies of their food and fish, as well as respecting the ```wellFedToday``` flag.

**Thoughts:** Important, small step of progress today. Took yesterday off, owing to family stuff around pumpkin carving. I'd thought for sure that I'd code well into the night afterwards, but passed out on my couch for like three hours instead. Whoops. Anyway, still made progress tonight and feeling good about that!

**Link to work:** [Instagram post](https://www.instagram.com/p/BpgKWtMhnNy/)

### Day 43: October 29, 2018
#### Hours spent coding: ~1.5

**Today's Progress**: Finished up the eating functions and started in on the sleeping functions! Realized, yet again, that I have to modify some database tables because where do I put the ```builtShelterToday``` flag? And where do I put the ```weatherTonight``` value? So I added a column for the shelter being built in the user table and edited the miscData table to insert the weather one, which should be a game-wide event. Well, I'm not sure, actually, but that's how I wrote it. I might rethink it later.

Added a ```checkForBarb``` function, which is a fun in-joke with co-workers, but really refers to what might happen if you have _too many_ fish on you.

**Thoughts:** I got the "great" idea to add in Shelter/Weather checks, so I need to deal with those tomorrow. One day, my database tables will no longer change every other day, I swear. Nearly out of the intro, which is both terrifying and exhilirating. But now, bed.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bpi1JyyhUg2/)

### Day 44: October 30, 2018
#### Hours spent coding: ~2.5

**Today's Progress**: Finished up ```#Hacktoberfest```, which is exciting, then spent time on my game. One of my switch statements is basically broken because it keeps going to the second case for some reason. That bears investigation. Speaking of bears, the Barb functionality for the sleep routine works great! I added preliminary stuff for weather and a check for building shelter. I'm also rethinking whether or not I should have those things, hahaha.

**Thoughts:** Super tired and wish I could have gotten more work in on the game. At 12:01am on the 1st, National Novel Writing Month starts, so most of tomorrow night (Halloween) will be spent planning out my novel. I've got some bits figured out, but no coding tomorrow night unless I am miraculously done planning by like, 10pm. I'm hoping I'll get to keep actually coding over the next month, though I know I'll probably spend a lot of my "coding hours" writing trivia questions. Which is fine. The point of this for me is to propel me forward in terms of this game project. Just wonder how I'm going to juggle the game project and writing. Should be interesting, at any rate.

**Link to work:** [Instagram post](https://www.instagram.com/p/BplegEbjb_W/)

### Day 45: January 10, 2019
#### Hours spent coding: ~1

**Today's Progress**: Well, I started up Docker and opened up Sublime and stared at my code and tried to reacquaint myself with things. It has been a long-ass break. I wasn't able to code at all in November and then December was over before I knew it and here we are, the 10th of January, and at like, 11pm is when I started even looking at code. I'm rusty as hell. I have no idea what 90% of stuff does right now. I'm going to have to spend time this weekend just catching up on what on earth all of this I've written does.

**Thoughts**: It was remarkably easy to just keep going back in October. I'd made coding a habit. And then I broke it. Time to get back to it. It was incredibly daunting just to launch Docker and then go to the command line and be like... uh, ```docker-compose build```??? Is that how this thing works? But I've dipped my toes in again and now I feel a little less intimidated by my own work. I keep forgetting, underestimating, the massive scope of this project. But I've spent some time in the last couple of days planning stuff out, so I'm hoping to start doing timelines and milestones and all of that.

Right now, I think my goal is for an alpha launch by February 18. Hah. We'll see how that works out. I think I could do it, too. Everything I'm coding at the moment (for the intro) is going to be used in the game itself. There are some things I'll need to add, but maybe I'm closer than I think. If I can dedicate 10-12 hours minimum to coding for the next 4-5 weeks, then that's 40-60 hours of coding. That's plenty of time to actually accomplish things.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bse4DdfBsXr/)

### Day 46: February 2, 2019
#### Hours spent coding: ~4

**Today's Progress**: Father, forgive me, it has been 23 days since my last update... I swear I have a good reason. It's because I'm spending a ton of my free time doing family research ahead of my trip TO SCOTLAND. I'm going with work in early April and then sticking around for a week. My dad's side of the family is English and Scottish. His grandfather was English and all three other grandparents were Scottish. The English grandfather married a Scottish woman from Aberdeenshire and I've seen a ton of that family-related stuff (and also, I'm not going to Aberdeen on this trip) so I'm focused on my dad's mom's family, since both of her parents were from Edinburgh. It's been a trip and a half and I've been doing all this research in my "free time". So, yeah, not a lot of coding going on. I am bad and I should feel bad!

That said, I jumped back into it on Saturday (it's after 5am on Sunday right now) and made some actual progress!

First, if I logged in as a non-admin, I kept getting "redirected too many times" errors. This is because in my ```checkAdmin()``` function, I had a stupid redirect. Initially, that function was only used when accessing the admin menu, but I decided to make life easier for myself (and only made it harder!) by inserting an `if` statement on a page to show the admin menu link. And then that borked the non-admins. Fixed!

Next, I had an issue where I'd forgotten to remove my limit on fishing, so I removed ```&& ($fishValue < 3)``` from that ```if``` statement and fishing is fine. Fish 'till you have 1000 fish, that's cool! Just watch out for bears...

I'm also adding complexity because apparently that's what I do for fun. Instead of just "rain" and "sun" for weather conditions, I'm gonna have a 5% chance of a storm, plus 15% chance of rain that isn't a storm and then 80% chance for sun. Of course, the code I'd already written to take weather into account only accounts for `0` and `1` as options, so I'm gonna need to rewrite that because I _like_ the idea of a stupid storm.

Speaking of complexity, as I'd mentioned back in _October_, I'm also adding shelter. Basically, to get max energy every day, you need to eat ```X``` amount of food and you have to have a shelter to avoid the bad weather. I specifically state in the intro that you take a bit of time to build yourself a shelter, so I had to find where I set all the initial variables and then add a ```builtShelterToday``` flag so that when the user goes to sleep (and then gets tossed into the proper game), they get full energy if they've eaten enough.

And speaking of full energy, ughhhhh, what a PITA that was to code at this point. I had some funkiness happening with some functions around energy, but I fixed them! Basically, instead of returning back to the page if someone _had_ been ```wellFed```, they continued through the loop and would end up with 70 energy instead of 100. Just had to define the variable ```$newEnergyValue = 100``` and then ```return $newEnergyValue```, which breaks them out and returns the proper value.

I also fixed something small, but important. If Barb and the kids show up, your food count at the top of the screen is what it _was_ before the Barb function runs. Then it runs, so I had to define that, if that occurs, ```$fishValue = 0``` and then re-display that after the description of the event. I'm feeling pretty good about that one.

Finally, I'm actually editing this file locally instead of on GitHub. Figure it's about time, hahahaha.

**Thoughts**: It's been hard to find time, but I also haven't felt too motivated to code lately. I don't know why. I enjoy it. Life's gotten in the way, I guess? I've been writing, researching, watching TV... 

But I was watching the latest video by [Mike Boyd](https://github.com/mikeboydvideo/), who has a great [YouTube channel](https://www.youtube.com/channel/UCIRiWCPZoUyZDbydIqitHtQ). The latest video is all about him [coding his own game](https://www.youtube.com/watch?v=s12npdDmGUc) in JavaScript, and it's a pretty darn good little piece of work! It totally motivated me to get back to it, at least on Saturday. Last month, I said an alpha launch could occur by February 18. That is, uh, rather unlikely. ;) I still need about 40ish hours, I think, before I can get this thing going where I want it to go and open it up to a friends and family alpha. With any luck, March 4 could be a possibility. I'm quite advanced in my family research and I don't _think_ I have too many more direct ancestors to track down ahead of my trip. Hopefully, some of my time spent doing genealogy can be repurposed to coding.

Anyway, here's a video to about 25ish minutes of my coding and trying to fix the energy stuff. Hopefully it won't be another 3+ weeks before I have another update!

**Link to work:** [Instagram post](https://www.instagram.com/p/Btad5naB6VK/)

### Day 47: February 6, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: I started off tonight wanting to ensure that my database for, well, _data_, was going to be able to be populated. You see, I want statistics for all the questions. I want to know how many times a question is asked and how many times it's answered correctly. I also want to be able to get those stats by category and I think, since I've used the `question_id` from the `main_questions` table in my `questionData` table, that it should be relatively easy to write a simple SQL query to do that. So I now have an admin-only page where I can go in to populate that `questionData` table. This is, obviously, not ideal. But I've got it happening programmatically! So I go to the page and it runs a function that counts the number of rows in `main_questions`. Then it offsets it by 3 (so it starts at 4) and adds those rows to `questionData` with columns for the `question_id`, `asked` and `correct`.

Why does it start at four? Because I have three introductory questions that you have to answer correctly to start things off.

I do this because, presently, I don't know how many questions I have. Well, I do. As it happens, it's like, 290 right now. But I only know that because of the function to count the rows! I'm hoping to launch the game with like, 4000 questions, so I have a long way to go here. The admin page counting/inserting of the rows is useful too, because if I add, I don't know, 1000 questions, I don't have to change anything there. Still, there's probably a more efficient way to do it than a for loop.

With that done, I can start adding stats on each action. Every time you catch a fish, iterate that. Every time you eat a fish, iterate that, etc. Of course, I do need to get the user out of the intro still, but we'll get there.

**Thoughts**: I spent some time with a friend of mine the other night, trying to get this going on an AWS instance, but we failed. Well, I failed. My friend doesn't know anything about Docker and I can't figure out how to get my Docker MySQL database to get spun up on his RDS instance. That's a challenge for later on, but it was neat to try to get things going. We got the PHP part of things running, but kept running into an error in terms of contacting the MySQL server. It was running, we just couldn't reach it and it wasn't running on the RDS instance, like I said.

At least this bit of database work makes me feel good about having managed to make some progress. I definitely have to stop just adding complexity to All The Things, though...!

**Link to work:** [Instagram post](https://www.instagram.com/p/Btkd1i9haZt/)

### Day 48: February 7, 2019
#### Hours spent coding: ~2.5

**Today's Progress**: I tackled stats tonight, at least in the sense of displaying them on the admin pages. So the queries are written in the code and they work. Then they're displayed properly on various admin pages. On the to-do list remains complex question statistics, but so far, I can get a count of all questions asked, all questions answered correctly and then get a percent of total questions answered correctly (rounded to two decimal places, thank you very kindly).

For later, I want complex question stats -- the above, but per question or per category. Like, who knows what Dy is the chemical symbol for? (Fun fact: it's dysprosium.) Is that going to be more or less difficult than naming Supergirl's adoptive sister? (That would be Alex Danvers.) And is that going to be more or less difficult than naming the capital of Lativa? (That's Riga.) I do eventually want to get all those kinds of stats in.

So the next step is actually building this stuff into the functions. Each time you catch a fish, increment the counter. Each time you each a fish, increment the counter. And so on and so forth. I also have a place to stash the weather for overnight stuff, which will help me to get out of the intro at some point. Why must I always add complexity before finishing the simple things? My creativity is my kryptonite here.

**Thoughts**: I sat down with a pen and paper and sketched out what I needed to do and I also fixed my data tables to populate them with 0s because they weren't being populated originally, so it was "empty set" results instead of the 0s I wanted to show. Whoops. Anyway, I spent a lot of time messing around in the command line interface of MySQL and figuring out how to join things again, so that was also useful. It felt good, too. I wish I'd learned more than "SQL Essentials" during my diploma. I'd love to do a more in-depth SQL course at school again.

Or maybe I'll just do it through Udemy? I dunno, we'll see.

Not sure how much coding will happen this weekend, unfortunately, but hopefully at least some. It feels really good to get back into it.

**Link to work:** [Instagram post](https://www.instagram.com/p/BtnHTm_h42o/)

### Day 49: February 9, 2019
#### Hours spent coding: ~4

**Today's Progress**: I had to refactor how I make all my database instances tonight. I was not pleased. Basically, I had included database classes in certain required files. This caused conflicts because the instance names would already be in use. So I separated out the three different database PDO connections into three separate files and now I call them when needed. (Actually, that's a lie. That's the goal. Right now, I'm just adding all three of them as required files any time I'm touching a database.)

Then, I got all the increments for stats going on any food-related action -- catching or eating a fish, finding food, eating food, plus Barb's visit count and the total number of fish Barb (and kids) have eaten. It wasn't too hard to do, which is nice, but it was a bit tedious to find a good way to do it and then basically copy it to the remaining five actions. Plus testing.

I also tested out registration (while testing to make sure I included the database connections on all appropriate files) and I'm pleased it's still working properly, as is the SendGrid integration. :)

Oh, I also eliminated some divide-by-zero errors in the stats, where there haven't been wins or there haven't been questions asked.

**Thoughts**: I still don't know how I want weather to work. Should it be a one-off check that fires when someone goes to sleep? Should it be a maintenance event that happens every night for everyone? I don't know. I kind of like the randomness of it (also fixed a bug there). Still, gotta figure out weather and the shelter thing.

Moving ever-closer to actually leaving the intro and getting people out on to the river. With questions. And answers. Eek. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/Btsis7XBFa-/)

### Day 50: February 12, 2019
#### Hours spent coding: ~2

**Today's Progress**: The good news is I got weather to work. So that's a good thing. The not great news is that I'm bashing my head against the wall when it comes to the intro questions. As things stood, I was iterating on questions whether you were right or wrong. I also had no idea why I'd chosen that particular way to go through things. So I decided to rewrite it. But I was paralyzed with indecision and didn't get much done. The result is that the intro questions do not currently work. Blah.

**Thoughts**: Feeling pretty annoyed with my lack of overall progress tonight. I'm sure it'll be like cleaning -- you get a bigger mess first before you get to where you want to be, but still. I'm annoyed.

**Link to work:** [Instagram post](https://www.instagram.com/p/Btz8h-eBWSx/)

### Day 51: February 16, 2019
#### Hours spent coding: ~4

**Today's Progress**: I reworked the intro questions. And they even seem to work. I need to double-check on how I trigger the intro done flag, because I think I need to hit that if they've answered question 3. Still, the intro questions basically all work properly. And if you show up at `introq2.php` and you've already answered questions 1 and 2, you get bumped to 3. Or if you go to 1 and all three are done, you get bumped to `intro-done.php`. There was a lot of time wasted thinking I'd done my comparisons wrong when, in reality, it was a copy/paste error and I'd neglected to call the proper variable on Q2 and Q3 of the intro.

With that done, more or less (again, need to double-check triggering the intro-done flag), I think I'm finally ready to move out of the intro onto the river itself. Of course, I could refactor the intro questions so I'm doing less repeating of myself, but frankly, that can wait. My brain aches from all of this.

Anyway, so I'm going to need to create a bunch of admin commands, including a maintenance routine, that can be run manually during testing and such. So that's going to be... interesting. At least I already have a bunch of admin stuff and an admin menu all set up.

Should be interesting to work on tomorrow!

**Thoughts**: Ugh, definitely so very frustrated by how inefficient I think the intro questions are done, plus the copy/paste error, which was maddening. I feel like I should be able to have just one page that changes based on whether the question is answered correctly or not, but I can't seem to work it out, so I just added three flags to the user table, one for each intro question.

I was also annoyed by the whole reworking of the questions all week, so much so that I didn't code at all after Tuesday, but I think the time away helped a bit, because now it all seems to work. Good stuff, I guess.

I also decided to capture my screen, rather than use my camera to film it, to make a video tonight. Pretty pleased with it. It was relatively easy to do. Link below. (And hahaha you can definitely see when I just copy/paste a bunch of stuff and completely miss out on changing two instances of the number "1".)

**Link to work:** [Instagram post](https://www.instagram.com/p/Bt-f-F1hdiR/)

### Day 52: February 17, 2019
#### Hours spent coding: ~3

**Today's Progress**: SUPER excited about all the progress I made tonight! I exit the intro cleanly and move into the real game where fishing, foraging and eating either of those things work just fine because I basically used exactly the same functions as in the intro! Super pleased with myself. Paddling took some work, but things are working in the sense that you can paddle (currently endlessly as I don't have energy costs or checks implemented yet) and get questions and answers and you can actually go down the river! And it'll save your location! So I'm really pleased with that. I definitely need to tweak some story aspect stuff, plus add energy checks and costs, plus add statistics to the paddle function, but that's working out nicely.

Also to do:

- Shelter & weather so I can do sleep function stuff.

**Thoughts**: All of that frustration from the last few days is gone and I'm having to drag myself away from the code to go to bed. Really looking forward to this week and all the coding that will come with it!

**Link to work:** [Instagram post](https://www.instagram.com/p/BuAuQUIB3pj/)

### Day 53: February 18, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Ughhhhh, all of my excitement from yesterday vanished when I finally got to sit down and code tonight. Still, kept working at things and got paddling in the game to a decent state. Still doesn't cost any energy, so there's an energy check to do there. I did set up a "first paddle" experience that explains how that aspect of the game will work, though, and have a subsequent check for it, so that's a good thing done... although it _did_ mean editing my user table. Again. And I really do need to look at refactoring the database calls for the trivia questions because apparently what I was doing a year ago is completely different from what I'm doing now. Go figure.

**Thoughts**: I've had a headache for a couple of days now -- much worse on Sunday than Monday, but it's still lingering and annoying and I'm tired. And cranky. I blame that for not getting more advanced tonight, despite looking forward to it all day long.

**Link to work:** [Instagram post](https://www.instagram.com/p/BuDXJp1heBR/)

### Day 54: February 19, 2019
#### Hours spent coding: ~2

**Today's Progress**: Little progress tonight -- more thinking than anything else. I had to figure out when to "charge" the users energy for paddling down the river. I finally decided to do it when they submit the answer, rather than on page load, or in the various functions in the page. I think that's fair, because it still lets you submit the answer and, consequently, move forward, without getting a new question if you don't have enough energy for that next question, if I run the check on the page load. Which I do. I think that has _also_ gotten rid of the fact that a player's energy can dip into the negatives. Whoops! hahaha. I also hardened that a bit by saying, on that charge energy function, that if the energy is equal to 2 or less, set the energy to 0, in case they _somehow_ manage to get to paddle with less than 3 energy.

**Thoughts**: Headache continues. I hate my sinuses. And weather fluctuations. Can't it just be -20C all winter long? Then 15C in the spring and fall and 25C in the summer? Anyway, I think I'm getting there. Energy will be reduced going forward. Just need to figure out building shelter and sleeping/waking up next, I think. Not the most glamourous of things, but neither is refactoring the fetching of the trivia questions, which I have steadfastly avoided...

**Link to work:** [Instagram post](https://www.instagram.com/p/BuF5lw3Blk-/)

### Day 55: February 20, 2019
#### Hours spent coding: ~2

**Today's Progress**: Paddling seems to have been in a good state when I left it last night, so I didn't have to do too much there. I did a few small things, one of which was `trim()` my user's answers, because ```toronto ``` or ``` toronto``` was incorrect. So I now properly trim whitespace for both the first paddle and the subsequent paddles. Yay! I also removed the autofocus on the input field for the first paddle because it was incorrectly scrolling the page down to the field. Whoops.

Hands down, the _worst_ part of the night was the realization that _if someone builds a shelter and then paddles away, they are abandoning their shelter_. So I would have to either stop them from doing so or maybe warn them somehow and then unflag their `builtShelter` flag. I'm in favour of letting users do many dumb things, if they wish, so long as they understand that it may not be the wisest thing to do in the future. So I have the water nymph show up and be like "human, wtf are you doing?" and I give the user _two chances_ to not abandon camp. Still, if they do, their `builtShelter` flag is removed.

Of course, I had to build checks around this. Could they paddle? Would they have the three energy to do so? Etc, etc, blah, blah. And shelter building isn't completely done -- it's charging energy oddly, so that's something to look into.

Once I get the shelter thing down, it's time to figure out how to make sleeping work. I want to build in a daily maintenance. When that happens at, say, 3am ET (GMT-5 -- I'll have to look at coding something for that pesky Daylight Saving Time which is nearly upon us), the following things need to occur:

* all "today" variables reset: fish/food eaten today, food units eaten today, wellfed today, build shelter today
* weather changes
* energy is restored based on a stupidly complex math problem that takes weather, shelter and being well-fed into consideration

Once I've got that done, I'll need to start adding question statistics and such.

Other things I'll eventually need to code:

* email inactive players (haven't played in 30 days)
* email inactive players that their accounts will be deleted tomorrow (haven't played in 44 days)
* delete inactive players (haven't played in 45 days)
* random events - I think it would be cool for some elements of randomness to occur. Maybe even some easter eggs -- like a specific answer to a specific question will do X, Y or Z... But maybe that's a version 2 kind of thing.

And, of course, that whole "winning the game" thing, too:

* Check win state; if winner, freeze everything for one day
* If win state granted yesterday, reset everyone to 0km, add winner to hall of fame (should code that too!)

Of course, we're a long way off from someone actually winning the game. There are trials and such to be coded, but we're not quite there yet.

**Thoughts**: There's still a lot to do and a long way to go before a real launch, but I'm hopeful that I can show my brother, at least, and have him play for a bit to see what it looks like.

I have to get to writing more questions, too. I want to launch with 4000 questions. I have like, oh, 400ish? And that includes the periodic table of the elements questions. hahaha.

**Link to work:** [Instagram post](https://www.instagram.com/p/BuIgvSuB_Iq/)

### Day 56: February 22, 2019
#### Hours spent coding: ~2

**Today's Progress**: Well, it was less coding and more trying to figure out what the hell was going wrong. I wanted to get things working on my laptop because I'm going to have 2 hours on a train tomorrow where I can code and I'm super looking forward to that. For whatever reason, my Docker IPs are messed up on the laptop. Like, the Dockerfile is correct, but I'm connecting to the database from the wrong IP, so that's all messed up. Works just fine on my desktop. I don't get it.

Anyway, I fixed that, it just means changing my MySQL creation file to give permissions to the right user on the right IP.

Then, I wanted to insert some more questions I've got. I'd previously had a heck of a time inserting questions via CSV, but, after a lot of trouble, I got some proper CSV questions inserted. I'm feeling pretty jazzed about that. Close to 500 questions total!

Other things I did:

* trim whitespace on intro questions!
* remembered to `removeShelter()` from user intro -- need to think about if I want to remove it in the future after it's been used. Probably not??

So not only do I want to code on the train, but I really want my brother to test out the game. Hopefully, while on the train, I can get some progress done on sleep functionality, because that's definitely not finished yet. I have this ugly call to a function that's currently commented out:

`//$finalEnergyValue = finalEnergyRestoration($user, $wellFedToday, $newEnergyValue, $shelter, $weather);`

It's commented out because I only just put in shelter and weather over the last few days, but also because my `finalEnergyRestoration()` function scares the bejeesus out of me. So there's that to tackle on the train. hahaha.

**Thoughts**: Looking forward to a proper user test from my brother as we hang out in Ottawa for a bit. I'm going to Ottawa for like, 24 hours, at the behest of my parents and my brother, but mainly to see my nephews and to hang out with a friend of mine from the area. It's ridiculous that all of us are going to Ottawa so my brother can pick up a *tent* of all things, but there ya go. Somehow my parents decided to make it a big family trip and, against my better judgement, I'm going.

But I'm still going to make my brother play my game. ;)

**Link to work:** [Instagram post](https://www.instagram.com/p/BuNvfEKhUTW/)

### Day 57: February 28, 2019
#### Hours spent coding: ~3

**Today's Progress**: It took me a while to wrap my head around how to tackle it, but I finally got a manual maintenance routine going by coding all the functions required for it -- which is good, because this will eventually run automatically, albeit with some additions. I can now hit that button as an admin and the following will happen:

- weather gets set
- weather gets fetched
- we count the total number of users in the users table
- we run a `for` loop that iterates up to and including the final user in the table
- the loop takes their `wellFedToday` and `shelterBuiltToday` values from their `user_id` (cleverly snagged from the variable I'm using that increments all the way up to and including that final user)
- then it calls the `dailyChecks` function, which analyzes the `weather`, `wellFedToday` and `shelterBuiltToday` data and puts the user into one of 12 separate scenarios
- it calculates the `newEnergyValue` based on one of those 12 scenarios and returns the value back to the maintenance routine
- then we `clearDailyValues` on that `user_id`
- then we restore the energy by passing `$userId` and `$newEnergyValue` through the `finalEnergyRestoration` function

Whew.

That took a lot of energy. No pun intended. :)

**Thoughts**: So that's great, because now I can continue to test and eventually write up some more functions that will email users who haven't logged in, etc, etc, etc. I have a lot left to do, but this at least fixes the user data and makes them able to play another day's worth of stuff. Additionally, I got some good feedback from my brother. Plus, I know what the first "trial" is gonna be. Lots of stuff to do this weekend, including adding more questions. I've got 100 Red Dwarf questions and should have 100 questions each in the subjects of Star Trek TNG, DS9 and VOY. Why, yes, I AM a nerd, thank you for asking. ;)

**Link to work:** [Instagram post](https://www.instagram.com/p/Buda7aEhq7T/)

### Day 58: March 2, 2019
#### Hours spent coding: ~2

**Today's Progress**: So after the success with regards to the maintenance routine, my brother kindly inquired about the use-case where, oh, you know, maybe someone wasn't going to log in every single day. Is it fair to punish them for not eating or building shelter or whatever when they come back?

... no.

SIGH.

So tonight, I refined things by checking the `lastLogin` and doing some time-based math and finally figured out how to do that.

It all came down to this:

```    $lastLogin = strtotime($lastLogin);
    $time = strtotime("now");

    $timeSinceLastLogin = $time - $lastLogin;
```

If that's greater than 86400 seconds, which is 24 hours, then I skip that iteration of the loop. In my searching, I realized that I might have learned about `continue` in a loop during my classes, but I definitely had forgotten about it entirely. I've known about `break` since Java class, almost two years ago, but I legitimately don't remember if I did learn about `continue`. Anyway, that works BEAUTIFULLY.

```
        $skipCheck = skipMaintenanceCheck($i);

        if ($skipCheck == true) {

            echo "User " . $i . " has not logged in for 24 hours. Skipping.<br>";

            continue;

        }
```

Not too shabby!

Things are coming along super well. I have a lot of little things to focus on now. I'm slowly, but surely, getting to the point of a closed alpha!

And while I haven't done a ton of coding in a couple of days, I've been writing up some questions. Not sure how many I have at this point. I'll finish up the _Star Trek_ ones tomorrow and import them all and I'll do a count.

**Thoughts**: Feeling pretty great about the fix to the maintenance routine, though I do feel kind of dumb for not having thought it through first. Well, that's what alpha and beta testing are for, right? Right.

**Link to work:** [Instagram post](https://www.instagram.com/p/BuiwIEXhAj5/)

### Day 59: March 3, 2019
#### Hours spent coding: ~2.5

**Today's Progress**: To be fair, tonight's work was less about coding, per se, and more about testing. What comes _before_ alpha testing? Because that's what I was doing, hahaha. I worked to format some CSVs, I imported them, dropped my question_id column, then recreated it so I wouldn't get blank questions and so that my number of questions is correct. The number currently, by the way, without _Star Trek: Voyager_ questions included, is 711. That's 100 on the Montreal Canadiens, Red Dwarf, TNG and DS9. Then we have questions for the periodic table of elements, Supergirl, the Canadian capitals, the American capitals and European capitals. I'm halfway through 100 questions for _Star Trek: Voyager_, but apparently I haven't rewatched that show as often as TNG. I knew that, but I guess I didn't realize just how much of TNG is ingrained in me and how much Voyager just... isn't. So that'll bring the questions up to 811. I have about 38 more categories (so 3800 or so questions) I have sketched out. No questions for any of them have been written, so that's gonna be interesting... So perhaps a launch with close to 5000 questions?

Anyway, so I played the game for 45 minutes, pausing for a few seconds to run maintenance several times, and got like, 687 kilometers down the river. I'm going to add some stats to questions, plus keeping track of days, etc, so I can get a better idea of how long it's going to take someone to do this sort of thing. I want the entire game to play through in about 30-45 days before we pause it and reset it. Right now, it feels like:

* The days go by too quickly. I'm not sure if that's because the user is expending too much energy or if it's because I know the answers to most of the questions.
* You can make too much progress too quickly. If I played for about 10 days' worth and I got to 687km, that's a little ahead of my 30 day projection, assuming the length of the river is about 1800km, but more importantly, it makes 45 days of gameplay damn near impossible, particularly if I do grant people a bonus for questions right in a row.

So I need to observe this kind of thing and track the stats in my playing (and in alpha) and we'll see how it goes. I may lessen the energy requirement on a few things to extend the length of the day, but may make the river longer to extend the length of the game.

**Thoughts**: It's pretty freaking cool to _play your own game_ for 45 minutes straight.

**Link to work:** [Instagram post](https://www.instagram.com/p/Buk_q_fBsUE/)

### Day 60: March 4, 2019
#### Hours spent coding: ~3

**Today's Progress**: Today's work was more about adding 100 Voyager questions (oh god, I am not as familiar with it as I am with TNG and DS9!) and then working with the data rather than anything else.

I imported it and so my questions table then had 811 questions. Prior to today, I'd have my intro questions (3 of them) pre-inserted into the table on creation, followed by a number of additions for things like the _Supergirl_ category and the different capitals categories and the category about the Montreal Canadiens. So tonight, after importing yet another CSV that was yet another PITA, I _exported_ the table (wow, super easy!) and then copied that file from that container to my actual computer (also super easy!) and then replaced my original main questions SQL file on load with the exported one. It seems to have worked???? If so, that's _ridiculously_ simple. I did connect to the container and the MySQL server within and selected the entire table and it all came up properly, it looks like. I mean, all 811 questions are there. I guess we'll see tomorrow if I can access them properly. (I'm thinking I can.)

**Thoughts**: This is going to make life a lot easier, both for backups and potential restorations, but just adding more questions in the future.

**Link to work:** [Instagram post](https://www.instagram.com/p/BunfASghA7X/)

### Day 61: March 6, 2019
#### Hours spent coding: ~2

**Today's Progress**: Fun fact, the MySQL dump of the questions table worked fine when loaded on startup and throughout my pre-alpha testing of the gameplay functionality! I had a couple of glitches that I had to fix (missed semicolons, whoops) but that was easily done.

I then tackled two global stats I had yet to do: total days played and total distance travelled.

Days played is easy -- I pre-populate the table at creation at `1`, then pull from the `miscData` table and increments by one each time maintenance is run. Easy.

Total distance was a little more complicated, so I eventually settled on adding it all up at maintenance. Each user has a `location`, you see, so in my maintenance routine, we now `SELECT SUM(location) as totalDistanceTravelled from users` and then pass that through to the `distanceData` table. Took a few tries, but it seems to be working just fine, now. There are a lot of stats left to do -- question stats, for instance -- but I was pleasantly surprised to see I'd already done all the simple food stats. Go me. :D

**Thoughts**: Whenever I sit down at the computer to work on things, I'm now torn between writing All The Questions and writing All The Code. Tonight was a coding night, but maybe I should have written more questions... Anyway. Time for bed.

**Link to work:** [Instagram post](https://www.instagram.com/p/Busk_PYBwxt/)

### Day 62: March 7, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Started in on stats for questions, which seem to be working okay, except they're not incrementing for some reason. Like, I _know_ I've answered specific questions more than once in this session and yet the `asked` column in `questionData` only increments by one and then sticks there. Something to look into. But not at 4am on a weeknight. Whoops. That's what I get for napping on my couch for almost four hours.

**Thoughts**: Some progress is still progress. Gotta remember that.

**Link to work:** [Instagram post](https://www.instagram.com/p/BuvcP77hgq8/)

### Day 63: March 8, 2019
#### Hours spent coding: ~1

**Today's Progress**: The aforementioned issue was that I wasn't _returning_ the data to the PHP page and so it never incremented beyond 1 because it assumed a null value instead of something like a 1 or a 6 or a 100 because there was no data to increment. *_sigh_* Learning. Always learning.

So basic question stats now work, which is great. Eventually I'll be able to create more complex stats but this is decent for now.

**Thoughts**: Stop coding in the middle of the night, self.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bux5_LbBpaU/)

### Day 64: March 9, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Got exceedingly little done, but at least what I did is visible in-game. I added colour and such to the correct/incorrect responses. And found a new bug. If you reload the page and resubmit the form multiple times on a correct answer, you _keep going forward_. I mean, yes, your energy decreases, but you keep progressing down the river. This needs to be fixed PRONTO.

**Thoughts**: Progress is slow, but it's there. Also, DST can suck it.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bu0mo48B2XZ/)

### Day 65: April 29, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Was unpleasantly surprised to remember where I'd left off with the reloading bug. For real. I could have lived just fine without that. I spent a good 45+ minutes tinkering with my form page. Maybe I should go the AJAX route if I can't get the check to work otherwise?

**Thoughts**: Hoo boy, it's been a while. In my defense, I spent two-plus weeks in Scotland and that was awesome. Now that I have some semblance of that mythical thing called _free time_ again, though, I hope to code more!

**Link to work:** [Instagram post](https://www.instagram.com/p/Bw3UmwphtJm/)

### Day 66: April 30, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Decided to scrap the self-posting form for the questions because I can't figure out how to not allow reloading to continue to bug the game out. I now point to a `processquestion.php` page, that does all the math and stuff and then points to either `questioncorrect.php` or `questionwrong.php`. Trouble is, I _think_ I may have broken user sessions now.

This is my unamused face. >.>

**Thoughts**: I legitimately have no idea what I'm doing and I'm flailing around and how did I ever think I could do anything with code ever??? And it was all going so WELL before I discovered this bug. :(

**Link to work:** [Instagram post](https://www.instagram.com/p/Bw54Z5AhahL/)

### Day 67: May 27, 2019
#### Hours spent coding: ~1

**Today's Progress**: Yeah, user sessions are good and truly busted. I spent a good chunk of time actually trying to get self-posting to work, but if you legitimately know the (short) answer to a (short) question and answer it in under 2 seconds, then you're basically just as fast as reloading the page, so I can't tell if you're cheating. As such, I really do have to go the process page route.

It doesn't help that I haven't touched my code in a month, either, I know, but also I can't seem to find anything anywhere, in a book or online, that's doing what I'm attempting. Which causes me concern.

**Thoughts**: Still flailing like a flaily thing, but I guess if I just _rewrite_ a few things from _scratch_, I can get things to work. Kind of.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bx_iRUBAEe9/)

### Day 68: June 30, 2019
#### Hours spent coding: ~1
#### Hours spent organizing: ~2

**Today's Progress**: Well, after trying a few things, I said screw it and reverted to my (admittedly broken) version of the game where if you hit reload, it acknowleges a right answer. I'm going to have to do more testing to figure out how to not break sessions when I'm using a processing file. Near as I can figure, it just completely removed the username from the session, so none of my database calls worked, since there was no user ID or username.

I also merged `gameplay` into `master` because I do have a few other branches I want to work on and want them all to be based off of this version, because at least this version sort of works. It felt really good to merge that branch, since I'd created it in like, uh, September.

Then, I just organized _all the things_. I took my Trello boards, updated them, added the GitHub powerup, then started linking those cards to GitHub issues. Then, I labelled all the GitHub issues and milestoned them. I feel pretty organized and productive, now, and even ready to start tackling things to see the milestone progress bar move.

**Thoughts**: In adding milestones, I came up with dates. Alpha should launch September 2. Beta on February 2, 2020. And v1.0, no later than July 1, 2020.

Yes, I am terrified of these dates. But I think they're mostly feasible.

November and December are basically worthless to me in terms of getting stuff done, due to National Novel Writing Month and the holidays and such. That gives me all of September, October and January to get beta stuff done for February 2.

Stuff in the first half of next year (company trip, possible vacation, family stuff) will really mean I don't get much done in April or May, which leaves me February, March and June to get stuff done for launch.

And throughout the beta processes, I'll hopefully be gaining valuable statistical data to help me figure out if people are cheating, if questions are too easy, too hard, etc.

That said, I think my goals are reasonable and attainable. I'm just gonna have to do A LOT in the next two months.

**Link to work:** [Instagram post](https://www.instagram.com/p/BzXpqIngCDr/)

### Day 69: July 1, 2019
#### Hours spent coding: ~3

**Today's Progress**: There was a fair amount of organizing left to do -- tasks I hadn't thought through first and such. I'm mostly done with that now, I think.

I also did the primary separation between `users` and `players`, as I'm going to have, at minimum, two instances of the game: blue and green -- one that's monetized with optional microtransactions and one that isn't. So I have one user account and then I have players in game green and game blue. I've found it easiest to think of it as the user being the person and the player being the person's representation within the games.

Of course, the separation of these things has almost certainly completely borked everything. The database loads up without error, but I haven't dared to try registering a new user yet. Still, it's progress. 

**Thoughts**: Still moderately terrified, but pleased at separating out the `users` data from the `players` data. I also took the opportunity to add a few more flags in each table. I feel like I will never stop adding more crap to my `users` table (and, well, now the `players` one as well).

It feels good to be excited about things.

**Link to work:** [Instagram post](https://www.instagram.com/p/BzaWmlTAmKI/)

### Day 70: July 7, 2019
#### Hours spent coding: ~5

**Today's Progress**: I did a lot today! I fixed my registration and blacklist issues, added DKIM CNAME records to my domain name so my email isn't viewed as spam, figured out how to define a variable for "game" so I don't rewrite the entire thing twice, then started the arduous task of adding the `$game` variable to, oh, every call, and modifying all the database calls to ensure it's calling from the game's table and not the `users` table.

It's not done yet and the intro isn't fully working, but at least registration and login are fine now. More fixing this week, for sure.

**Thoughts**: I'm very proud of myself for trying to figure out a way not to repeat my code. The code between the games should be identical (more or less) and it doesn't make sense to have literally two (or more) copies, so I'm pleased I figured out how to pass a variable, then store it in the session, plus add it to the database for the `active_game` in the user table.

The easy thing is, of course, to duplicate everything, but that's not the programmatic way to do it. So I found a programmatic solution and I feel pretty good about it. Just a couple of years ago, it never would have dawned on me to try it in a programmatic way, and yet, here we are.

**Link to work:** [Instagram post](https://www.instagram.com/p/BzpNc5MAIvh/)

### Day 71: July 9, 2019
#### Hours spent coding: ~2

**Today's Progress**: Well, something is wrong with either:

- my database call
- my database user permission
- my code in general

Because I'm getting undefined variable errors for a variable that should be defined, but the MySQL command isn't getting run. So there's definitely something forked up there. But I'm too tired to figure it out. Bedtime.

**Thoughts**: Frustrated that something that should be working isn't.

**Link to work:** [Instagram post](https://www.instagram.com/p/BzuPALlgUbZ/)

### Day 72: July 11, 2019
#### Hours spent coding: ~1

**Today's Progress**: Hooooo boy, I figured out the issue. First, I thought it was that my user registration hadn't gone through (since I just inserted the user) and that might be causing issues, but no, because I went through registration this time and it still didn't work.

Then, I managed to narrow things down to my `$stmt->execute();` not actually executing. Doing a `print_r($stmt)` showed me that things should be okay, but it would. not. execute.

On a whim, I replaced my variable for the table name with the table name itself... and it _worked_.

Fun fact, everyone -- you cannot `bindValue` for a table name. So if you don't know the name of the table, you'll want to concatenate it into your statement.

Didn't do a lot of work tonight, but the work I did was very, very important. #smallvictories

**Thoughts**: I'm very pleased I figured that out. That's going to fix a lot of issues going forward, I'm sure. Getting closer to having the databases and game stuff separated.

Also, it makes me ridiculously pleased every time I get a registration email sent to me from SendGrid because HELL YEAH, I INTEGRATED THAT API ALL BY MYSELF. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/BzzX0HhgXbt/)

### Day 73: July 13, 2019
#### Hours spent coding: ~8

**Today's Progress**: Lots of progress in separating the databases. I basically have to define all the different tables in variables in the session as soon as the game is chosen and then refer to those for a variety of things. When I'm done with this, the users and players will be separated, plus the various game stats will be separated... and the Barb function will be rewritten to work well regardless of which version of the game is being played.

**Thoughts**: I had the most hilarious error earlier, where, upon raising my fishing skill, it claimed:

`fishing skill has increased to greeo!`

Still have no idea why that was happening, but I did end up fixing it in the end. It amused me tremendously, though.

This separation is slow, meticulous work. Rather than just do a search and replace (and I did think about it), I figured I'd just go through the game and test things and fix the errors as they come up. So far, so good. Load page, see errors, fix errors. Load page again, see more errors, fix more errors. Rinse and repeat.

Currently stuck on rewriting Barb to not repeat myself a zillion times, but apparently switch statements are not made to play nice with two variables? I'm going to have to have switches nested in if statements, I think. We'll see. It's 4:03am and I'm definitely too tired to do this.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bz4f4V1Akg0/)

### Day 74: July 14, 2019
#### Hours spent coding: ~6

**Today's Progress**: Holy crap, I think things are done!

All my functions appear to work.

I even rewrote the Barb event. (400 lines of code later...!) It's something I've wanted to do since like, January? February? But especially in May, when my friend Andrew deliberately broke the functionality of the game by hoarding food. Like a jerk.

It took me most of the day as I had to push through some logic issues, but I think all's well and I am now back to where I was except now I can define any game name. There are some small optimizations to do, for sure, but things _work_, which is just so exciting. This is gonna knock out 3-4 issues in my GitHub repo.

Also, I figured out why my fishing skill had `increased to greeo`. This is apparently what happens when you pass more than the number of expected parameters. So I was passing, for example, `$user` and `$game` and `$game_players_table` and the function was only expecting two, the first and the last. So that got wiggy. This happened a lot.

Another thing -- `debugDumpParams();` is my favourite.

**Thoughts**: I feel awesome. I want to write more stuff right now, but it's 1:41am and also, I literally don't have more of the game yet. I need to tidy up a number of small things, but I need to get the sleep function written. Maintenance... crap. I just realized maintenance hasn't been edited. Well, that'll get done tomorrow, since I'll run maintenance on both games when I run it, so that'll be interesting to work out. Still, that's probably the only thing I'm missing.

Whew.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bz7SJhNgnUH/)

### Day 75: July 15, 2019
#### Hours spent coding: ~1

**Today's Progress**: Bleh, not quite done. Still a few pesky things to fix, including how to set the weather for both games simultaneously.

**Thoughts**: Dinked around a bit and things mostly work, which is good. Will need to do another sweep tomorrow, but not feeling it tonight.

**Link to work:** [Instagram post](https://www.instagram.com/p/Bz9rn0CAb3E/)

### Day 76: July 16, 2019
#### Hours spent coding: ~2

**Today's Progress**: I'm never going to be done separating everything, I swear to God.

Looks like the gameplay is pretty solid (well, okay, there's a very odd thing happening with regards to some answers being very wrong and yet being correct), but stats are a mess. I'm having to rewrite a lot of little things, which is annoying.

**Thoughts**: I'm definitely annoyed. I just want to be done with this branch and merge it to master and I know I'm basically the only person who will know if it's done or not, but I cannot bring myself to merge an incomplete branch. GRR, ARGH.

Bedtime.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0AcJDMgIfc/)

### Day 77: July 17, 2019
#### Hours spent coding: ~2

**Today's Progress**: Stats are still a mess, though marginally less of a mess than yesterday. No more errors, fatal or uncaught or otherwise. Just... wrong data. Everywhere. So I gotta fix that up.

Also, question verification? TOTALLY BUSTED. But that's okay. I can fix that. I need to rewrite asking questions in the first place due to that reload bug. But first, we'll get stats working okay.

**Thoughts**: If I don't merge this branch to master by Friday night before I go to bed, I may chuck my computer out my window.

Just sayin'.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0C9ebMASx-/)

### Day 78: July 18, 2019
#### Hours spent coding: ~1

**Today's Progress**: Stats all seem to kind of work. At least, the database separation part of them. And so the database separation is complete and I've merged the branch to master!

Question verification and funneling the stats info are _slightly_ busted, but we'll get to that soon enough.

Since I probably just have to rewrite the question functionality anyway, I'll tackle:

* question verification
* question stats
* repeat check (no dupes within 100 questions)

This is my goal this weekend.

**Thoughts**: It felt so good to merge to master. :D

**Link to work:** [Instagram post](https://www.instagram.com/p/B0FX2kKgT1_/)

### Day 79: July 19, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Fixed question verification and question stats. Part of one of those issues is that I just, you know, _wasn't calling the function_. Another was a misnamed function and yet another was me accidentally passing the `$questionId` twice in the same function, for some unknown reason.

I blame fatigue.

_time: 4:37am_

Yeah, definitely fatigue.

**Thoughts**: I need to do the repeat check functionality, but I want to fix the reload bug first, since I'll _probably_ have to rewrite paddling as it is... but couldn't I just copy over the repeat check session stuff over to a new paddling version? Probably.

I think I'm just putting off the hard work of redoing paddling. There's just _so much stuff_ that happens and I'm sure I'll just end up breaking it. Again. Not like it's not broken now (a reload should definitely not assume you got the question right), but if you're not out to explot things, it works beautifully.

Alas. I guess all of this is this weekend's work.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0IdvdzgYye/)

### Day 80: July 20, 2019
#### Hours spent coding: ~5

**Today's Progress**: Well, on the bright side, my question IDs are now being moved into the session, and that's persisting as it should.

On the downside, I cannot, for the life of me, figured out why `array_slice` isn't working appropriately. I want to slice the aforementioned array to the 100 last elements, but it just won't do that. Works fine on a test file with an array with 130 elements. Does not work in my `paddle.php` file.

This is probably a sign that I should give up on the session stuff for now until I rewrite paddling.

I still don't want to rewrite paddling.

**Thoughts**: I felt pretty great when I actually got my session array of question IDs to work. Too bad the great feeling was relatively short-lived, due to the frustration from `array_slice`. I'm sure I'm doing something wrong, but it's nearly 5am, so... bedtime.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0LDDsQA_5I/)

### Day 81: July 21, 2019
#### Hours spent coding: ~5

**Today's Progress**: Still stuck on the array thing.

I have determined that the array does get deleted when I unset it, so it's not like the 100 elements from `questionList` are getting added to values that are already there.

It's just taking the entire array and not the last 100 elements.

Still works fine on my test array file.

Still not working in my `paddle.php` file.

And yet, I still don't want to rewrite paddling.

But I think I really, really need to, now.

**Thoughts**: Arrays can kiss my ass and are making me rethink the importance of not having repeating questions when my final question tally will be close to 6000...

**Link to work:** [Instagram post](https://www.instagram.com/p/B0NIO3JgMh8/)

### Day 82: July 25, 2019
#### Hours spent coding: ~1

**Today's Progress**: Yep. _Still_ stuck on the array thing.

I can't explain why `array_slice` seems to work differently in my test array file versus my actual game file. But it does seem to. So that's weird.

In other news, in my intro and in my maintenance routines, I was passing different variables into the same function, which resulted in my daily values not being cleared on one or the other. The maintenance needs to go by `user_id`, since it iterates on all users numerically, while the intro sleep was trying to pass a username. Then I made it pass a username and broke the maintenance function because it can't iterate on `julie`. Whoops.

**Thoughts**: Arrays can still kiss my ass.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0XxYP7AAp4/)

### Day 83: July 27, 2019
#### Hours spent coding: ~2

**Today's Progress**: Fixed the repeat check functionality!

I started to think that if there wasn't anything wrong with my use of `array_slice`, as proven by my array test page, then maybe there was something wrong _with my array_. (I may have channelled my inner Beverly Crusher with that logic.)

Turns out my `questionList` array is _multidimensional_. So when I was slicing it, since there's just one element at the top level of my array, I had to add the index to the name in order to access the elements within it, so `$questionList[0]` instead of `$questionList`.

Well, that's solved and I've merged to master. Probably still need to rewrite paddling, but the repeat check is a big thing done and I learned a lot about sessions and arrays over the last, oh, 13ish hours of this project.

**Thoughts**: Arrays can _still_ kiss my ass, but at least things work. Planning to tackle something slightly easier tomorrow -- leaderboards in each game.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0dEK8JADYp/)

### Day 84: July 28, 2019
#### Hours spent coding: ~3

**Today's Progress**: Put together the leaderboards! It was pretty simple. The worst part was the styling of everything, which was a bit finicky.

The interesting thing here was that, when people register, I insert them into All The Games so that user IDs remain the same across the board, so I wanted to omit people in the leaderboards if they hadn't actually logged into that game. But I didn't want to add a new flag and check for that or anything.

Instead, I thought I'd exclude people at 0km, but that's silly, because you can log in and fish your life away at 0km, if you want to.

I do have an `introCampDone` flag, though, so I used that and came up with what I think is a pretty neat SQL query, which fetches usernames and locations where the user's record in question has the `introCampDone` flag, then I order it by descending location.

Works pretty well!

**Thoughts**: It feels good to merge to master twice in under 24 hours.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0ey_MZAk8v/)

### Day 85: August 1, 2019
#### Hours spent coding: ~2

**Today's Progress**: Still avoiding rewriting paddling, since at least the repeat check now works. :D What I decided to tackle tonight (at like, 11:30pm) was going to sleep. There wasn't actually a `sleep.php` file at all, so if you'd hit sleep, you'd get a 404 not found. Then I'd run the manual maintenance routine and then just hit the back button.

Now, you get to sleep and have the choice to return to the main menu. I mean, I guess you could hit back from the sleep page, but all it really is designed to be is a way for someone to elegantly quit the game, so to speak.

Man, I miss the old text games like Trade Wars 2002 and Legend of the Red Dragon, where you had menu screens and you didn't have a back button of any kind. Anyway, I decided not to worry about the back button functionality. If they don't want to do that, they don't have to.

Coming back _into_ the game was interesting, though. How to check if a user has played since maintenance? Yep, adding in yet another column to my player table, which gets reset at maintenance time. With that in, I'll also be able to customize the waking sequence based on if they've returned, based on their energy levels, tell them why they only have, for example, 40 energy after a terrible night of sleep, etc.

**Thoughts**: Some tinkering required here, but it should be some easy logic insertion. I'm pretty jazzed that most of it's done and works.

And crudpuppies, I forgot to ensure *Eat* was an option on the waking up. I'll have to add that logic if they're not well-fed.

Tomorrow. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/B0porPGAAW7/)

### Day 86: August 3, 2019
#### Hours spent coding: ~3

**Today's Progress**: Something dawned on me this evening -- why do I not seem to be counting days? There's logic for it. What's wrong with it?

Found it. I was calling the original `miscData` associated with the original database and not the separate game databases. So it kept pulling a non-existant value from a non-existant table and then iterating it by 1, so that's why my days played were always just `1`. It wasn't that I was doing it by actual dates, no. I just messed up. haha.

So I fixed that for global days played for the game. I fixed that for current days played for the user (which resets upon the game's reset), and on the total days played (which doesn't reset). This is only triggered when the user logs in for the first time after a maintenance happens.

Oh, and I did include *Eat* as an option on waking up as per the last entry here.

Other things yet to do in this branch:

* waking up text that explains _why_ you only have X amount of energy
* write up a couple of variations on sleep/wake text (switch statements)
* `intro-sleep`'s waking up text should, you know, _exist_

**Thoughts**: Coding on the laptop and not my desktop is, well, not ideal, but it works. I shudder to think of my data bill, though, since I'm tethering. Stupid cottage without Internet.

**Link to work:** [Instagram post](https://www.instagram.com/p/B0u3KOeAiDL/)

### Day 87: August 6, 2019
#### Hours spent "coding": ~1.5

**Today's Progress**: Well, it's not exactly coding, but tonight I wrote 93 questions about Superman. I am literally 7 questions from 100 and I can't think of another damn thing about Superman. And I freaking love Superman, let's be absolutely clear about this.

I figured I can get 1200-1300 questions done for alpha launch and then add in questions as I go, but I definitely want to break 1000. Almost there -- I'm at 904 questions now, total. But it'll be good to get some other general knowledge questions in there before alpha, for sure.

**Thoughts**: I love GitHub. What an awesome way to ensure my code can be pulled or pushed to or from another computer. I'd been like "oh no, I should get this stuff off my laptop --- BUT WAIT. I PUSHED TO GITHUB." Fabulous.

**Link to work:** [Instagram post](https://www.instagram.com/p/B02jvWHgD-G/)

### Day 88: August 7, 2019
#### Hours spent "coding": ~3

**Today's Progress**: I finished up the Superman questions, imported them, dumped the DB, then wrote 100 questions about US presidents and did the same thing. I had a few issues that meant I had to massage the imported text -- quote marks, single quotes, commas and escaping things can be nightmarish.

1011 questions, all properly formatted now!

**Thoughts**: I realized that I don't run `checkForBarb` anywhere except in the intro. Lord. Must integrate that into the maintenance routine ASAP. Still also need to do the things I noted this weekend:

* waking up text that explains _why_ you only have X amount of energy
* write up a couple of variations on sleep/wake text (switch statements)
* `intro-sleep`'s waking up text should, you know, _exist_

... also, I think my sessions are broken because I feel like I'm getting repeats more often than every 100 questions. But is that because I'm using another browser window to run my maintenance event? Maybe. Gotta test that like, tomorrow.

**Link to work:** [Instagram post](https://www.instagram.com/p/B05LkbzAoAG/)

### Day 89: August 8, 2019
#### Hours spent coding: ~3

**Today's Progress**: No new questions tonight. I went back to actually coding and tried to add the `checkForBarb` function into maintenance, which meant adding a new flag to a player's table, `barbAte` and other such nonsense. I also fixed the `checkForBarb` function -- I had set `== 6` instead of `>= 6`, so anything beyond 6 fish meant Barb doesn't show up and eat your food.

**Thoughts**: Need to fix the loading text to make sure it properly tells you if Barb and the kids ate, PLUS, the things I realized I need to do from last weekend:

* waking up text that explains _why_ you only have X amount of energy
* write up a couple of variations on sleep/wake text (switch statements)
* `intro-sleep`'s waking up text should, you know, _exist_

Also haven't tested sessions. More to-dos.

**Link to work:** [Instagram post](https://www.instagram.com/p/B07oXT_AutH/)

### Day 90: August 10, 2019
#### Hours spent coding: ~6

**Today's Progress**: Merged `maintenance` to `master`! After way too much work on Barb and making sure that whole thing works, I then had to add a new column to player tables about energy states. I have, uh, **TWELVE** different possible energy states, so I store them in the new column as like `1113` which means `wellFed`, `shelterBuilt` and sunny weather. `1112` means the same, only rainy. `1111` means the same, only with a storm. And so on.

All this to explain _why_ a user has X amount of energy on waking up.

Still need to write `intro-sleep`'s waking up text.

BUT. Victory regarding sessions! I figured it out. For some reason, in my `playgame` page, I was setting the question array to, uh, nothing. Like for real. I guess I was trying to initialize it?? Weird. Anyway, the question array persists in the session now. I feel super great about that.

I also did up a silly image and started in on like, the main page, the about page, the terms and privacy pages, plus the contact page. I'm gonna see what my options are for sending -- PHP mailer is what I use on my personal website, but I could probably use SendGrid for this? Not sure, will need to investigate.

Next up, probably the `intro-sleep` text, followed by the first paddle to normal paddle transition, which is just bad. In the same branch, I can probably also put in the colour-coding for fishing and foraging, since these are likely just small CSS changes.

So after adding those to GitHub, I now have 13 open issues for alpha and 8 closed. Some are small, some might not even get looked at until beta, and a couple of them have to do with cloud hosting. Can I get it all done in three weeks? Depends on how well cloud hosting stuff goes, I guess, really. Ugh, make that 14 open issues -- I need to figure out how to trigger the maintenance routines with a cronjob.

Well, make that 13 issues -- I had an issue about running an import for CSVs of questions, but we'll use a mysql dump after importing questions manually, I guess. It would be easier overall.

Well, 13 issues. 3 weeks. 4 issues a week? Ehhhhhhhhh, it might be tight. We'll see.

**Thoughts**: Wow. Day 90. And it's only taken me like 11 months to get to this point! hahaha. Hoo boy. I'm bad at that "consistent effort" thing. I'll be good for a few days and then stop for a week or more. Still, it's been wonderful to keep this log to see when I did make time and when I was on a streak, basically.

Can't believe it's almost over, both the #100daysofcode as well as the alpha for my game.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1AgCXwgLn9/)

### Day 91: August 11, 2019
#### Hours spent coding: ~5

**Today's Progress**: Ugh, I had a funky branch that was simultaneously ahead of and behind master and there are issues now that I've resolved that.

Priority is getting the `questionList` array working again, which means I have to define the variable but be careful not to overwrite the variable. Probably something with `isset` will be helpful. So:

- fix `intro-sleep` and such
- write `intro-sleep` text
- colourize fishing/foraging the way I do with questions
- colourize first couple of answers (like in first paddle)
- first paddle to regular paddling transition

**Thoughts**: Feels like two steps forward and three steps back, sometimes. That said, I finished basic website content, including a contact form that integrates with SendGrid, so there's that. Positives.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1DSG58gmC7/)

### Day 92: August 12, 2019
#### Hours spent coding: ~3

**Today's Progress**: Fixed the stupid `questionList` array issue. Ultimately, it came down to this:

```// Logic for session to persist

if (!ISSET ($_SESSION['questionList'])) {

$questionList = array();
$_SESSION['questionList'] = $questionList;

}
```

So with that, if it's not set, it'll set it. But if it _is_ set, it won't empty it. So I think that's done. That took way too long.

**Thoughts**: Still feel like my progress is incredibly incremental. But at least it's progress. Right? Right.

I spent a bit of time messing with the piece of code from my Instagram post tonight. But no. That code was fine. Siiiiiigh. And it's pretty, too. Well, maybe not pretty, exactly, but it's _clever_. And clever is fine by me.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1F9Jy1AjKu/)

### Day 93: August 13, 2019
#### Hours spent coding: ~2

**Today's Progress**: Finally, I got to doing some stuff that I've been meaning to do.

- fix `intro-sleep` and such
- write `intro-sleep` text
- colourize first couple of answers (like in first paddle)
- first paddle to regular paddling transition

Hilariously, I'm not sure what to do next. Probably colour-coding fishing and foraging, then make sure I'm sanitizing user responses? Yeah, that sounds like a plan.

**Thoughts**: 11 issues closed, 11 issues remain for alpha release, which is in like, oh, 3 weeks. Ish. Hopefully. Some of them are easy. Some are less easy. It's slowly, but surely, coming together.

And now, bed.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1IkRIlg1Z2/)

### Day 94: August 14, 2019
#### Hours spent coding: ~1.5

**Today's Progress**: Exhausted tonight. Couldn't really focus. It took way too long to figure out exactly what I'd done to return fish and foraging results and then make sure I opened and closed divs appropriately. Still to do:

- colourize fishing and foraging in the intro files
- sanitize user input

**Thoughts**: I'm super burnt right now. Too much work during the day, too much coding at night, not enough sleep overall. Might just take Friday night off from coding to veg out. I guess it depends on how I feel tomorrow night and also what I have left to do before the weekend push.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1LFs6Pgb4n/)

### Day 95: August 15, 2019
#### Hours spent coding: ~2

**Today's Progress**: Still tired, but pushed through the fatigue and managed to do exactly what I planned to do:

- colourize fishing and foraging in the intro files
- sanitize user input

**Thoughts**: I'm feeling pretty smart because at no time do my user's responses go into the database. They're held in a variable in the code and I run a comparison on them versus the data I'm pulling from the database. So even if you go all Little Bobby Tables on the response, nothing happens.

Usernames were a little less, uh, secure, shall we say. I'd meant, ages ago, to not only rely on JavaScript validation, but had never implemented PHP validation. That's all sorted now.

Passwords get hashed in my environment, so that shouldn't be an issue.

I'm probably overdoing it with emails a bit, but I'm using the email format being forced in the browser _and_ using `FILTER_VALIDATE_EMAIL`, so that should be okay.

Of course, all of this is just me being maybe a bit paranoid because none of my database users have DROP capabilities and stuff and I've siloed their permissions pretty well, I think. Still, I've sanitized anything that can be put into the database and the check I'm using can be (partly) seen in my Instagram post for the day.

Oh, and I made the caught/failed to catch a fish and found/didn't find food stuff look pretty in the intro, too. This closes out two more issues in GitHub. Woot!

Pretty tired overall, it's been a long week. But really pleased with all that I've accomplished this week.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1Np2j9A16z/)

### Day 96: August 17, 2019
#### Hours spent coding: ~4

**Today's Progress**: Fixed a lingering reset daily values issue in the intro earlier today, but then tackled a bunch of stuff tonight.

- Screw reCaptcha. I don't think it'll be necessary, so I'll incorporate it with beta. I can't figure out how to get it to work right and be mandatory for registration and login.
- Was very perplexed by token issues, but realized that's because I manually inserted my first two users with MySQL commands and not a proper registration, so they didn't _have_ tokens. Whoops. Fixed.
- Closed issue 16, verifying JS doesn't mess with changing PW
- Closed issue 39, which really only had me insert `<noscript>` warnings that JavaScript is required.
- Closed issue 42, after realizing reCaptcha was going to be a PITA.
- Closed the newly-opened issue 81, which had me add a "new user registration" email to the registration process, so I know when (and who) has signed up. Clearly, if traffic picks up, I need to remove that, though I am in no imminent danger of bypassing 15,000 emails a month, which I get for free.

**Thoughts**: This leaves roughly five issues open and I launch in two weeks. Two of them are basically the same issue, though -- cloud deployment, basically. One of the others is something I _should probably_ do, but it's not a huge deal right now. Another is something I _must_ do to ensure proper maintenance once loaded into the cloud. The last is a critical, game-breaking bug that I definitely need to fix.

Oh, and I just opened up a new one for this alpha launch -- fix my div padding.

Still, all in all, things are looking good. I'm gonna try to play with cloud-related things tomorrow (?) and see what I can get accomplished.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1TB_BBA1Y0/)

### Day 97: August 18, 2019
#### Hours spent coding and testing and deploying and debugging: ~9

**Today's Progress**: Well, on the bright side, I have the game running on AWS.

On the not-so-bright-side, that was a herculean effort _and_ not everything works properly. I'm convinced it has to do with database permissions for the database users and various hostnames. I could be wrong.

Still, you can register, you can play. You just can't change your email address or password. I think this is because something borks when the (perhaps not properly privileged database user) tries to make changes.

I cleaned up a couple of things, plus ensured the "new user registered" email gets sent to me on registration of a new user.

Other things to do which are not written down anywhere I don't think:

- automate startup (includes setting weather, populating question data, setting me as admin)
- automate maintenance (I have this as a GH issue at least)
- SSL cert (letsencrypt)
- get Elastic IP allocated and use it when we're all set
- point www to the allocated IP
- build forum on new `forum.riverofkurn.com` subdomain

**Thoughts**: It's driving me ABSOLUTELY MAD not understanding why the host my database users have to connect from is different given THE EXACT SAME CODE, based on whether this is on production (the AWS server) versus my local environment. Literally, the only way to make sure it works on both environments is to have the user host be `@'%'`, which is not, you know, ideal.

So, it's running, which is more than I honestly expected out of today. I was just gonna mess around with it, but props to my friend, A, who helped out for, oh, four or five hours. Today's Instagram post is me watching him play while he shares his screen. Warning: I'm loud, but you can also hear him in the background through my headphones. He is also The Worst.

Also: I'm wondering if the different behaviours might be because of Docker image caching on my localhost. That said, I did post to the Docker community forums. We'll see if that's helpful. If not, I might reach out to the guy whose Docker course I took. ... could actually stand to review stuff there first, maybe.

Really hoping I can sleep tonight without my brain whirring about these issues.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1U1bUeA9zW/)

### Day 98: August 19, 2019
#### Hours spent coding/tinkering/etc: ~4

**Today's Progress**: I am no more progressed than I was yesterday, at least not in terms of code.

However, we created an Amazon AMI image for the infrastructure and will solidify it tomorrow night on what we're using as production, then probably allocate an IP for prod.

We then used that AMI image for a stage instance because I basically now need to develop on stage, since none of the issues I'm seeing on prod or stage happen locally. Actually driving me crazy.

Developing on stage is awkward. There's a way to use Sublime Text to modify remote files. Something to look at more tomorrow, because making tiny edits on remote files in pico is not sustainable. At least I can push to GitHub from there, so I can download the changes locally.

Also, fun fact, my SendGrid shared pool is in the Spamcop database so my normal webhost is blocking, you know, ALL EMAILS from coming in. Can't bypass Spamcop, so I took the initial steps to delist the three pools of IPs at Spamcop (as per SendGrid's instructions). In the meantime, my G Suite email address and aliases are accepting email just fine.

Email delivery is a pain in the ass.

**Thoughts**: Tired. It's going to be a long and shitty week unless I get things working ASAP.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1X-udhAfOC/)

### Day 99: August 20, 2019
#### Hours spent coding/tinkering/etc: ~5

**Today's Progress**: Well, even though I have _remarkably_ little to show for it, I figured out All The Things tonight.

First, let's talk about the issues I was seeing on stage that I wasn't seeing locally, since that took me most of the 5 hours I spent staring at the computer tonight.

The issue was that I was getting an error with SendGrid, when sending to two recipients. But only on stage or "production", and not locally. I thought this was an issue with my database users or perhaps the code was just janky and was, for some unknown reason, behaving differently.

The most irritating part of the error was its claim that the array for the recipients had a null value in there. And I'm like "EXCUSE ME? It most certainly does NOT!"

Fun fact: it did.

But that's because stage and production, being new instances, downloaded the latest version of SendGrid with Composer, version 7.3.0.

While I'm sitting here on a 10-month old version 7.2.0.

Turns out that, you know, SendGrid CHANGED HOW TO SEND TO MULTIPLE RECIPIENTS in the intervening 10 months.

Great. Perfect. Thanks for the heads up.

So I updated my SendGrid and, voila, got the same error. Which is progress! Because at least I could _fix_ the error once and for all.

I did that and it worked on stage as well as local and life was beautiful and I was thinking, gosh, what will I work on next for an hour or so?

And then, as I was reviewing my branch that I wanted to merge to master, I realized I was using the wildcard for the database user's hostname. >.>

So I went in and changed things and made it the `(docker container name).(docker network name)` address. And it worked fine locally. So I pushed that to GitHub and pulled it down on staging and ... it didn't work.

What the fork, man?

It was then that I noticed that the container and network names on my local environment has hyphens in it and the ones on staging do not.

So I spent at least 45 minutes googling docker container names and hyphens.

Bonus fun fact: The `docker-compose` version on the environment we've set up at AWS? Using 1.17 of `docker-compose`. What version am I using locally? Why that would be version 1.24.1, of course!

... just recounting this story is exhausting.

So then I tried to install the newer version on the AWS environment and that didn't work. I had to uninstall the older version, _then_ install the new one. And _that_ worked, and I could see that the hostnames would be identical to the ones on my local environment.

Instead of `apt-get install docker-compose`, there's a whole curl command to run and such, so at least that'll be sorted tomorrow.

And then, gosh, do I actually get to start tackling some of the outstanding issues???

Maybe. We'll see. Tune in tomorrow for Day 100 of 100 Days of Code!

**Thoughts**: So here we are, the end of Day 99. It's taken me a lot longer than I wanted to get to #100daysofcode, almost a full calendar year, but I'm HERE.

I'll keep writing, to be sure. If nothing else, this is an epic recap of what I've been doing for the last actual year of my life, in terms of code.

That said, I'm so tired. It was just so maddening and frustrating that not one, but TWO version issues were conspiring to drive me crazy. For three days. Not that I'm counting or anything.

Just as frustrating is that I've spent nearly 20 hours in the last three days doing things that aren't even open issues in my repo. Like, I've spent 18 hours to get things to be THE SAME across my environments, essentially. That is a huge waste of time when I could be working on any of these items:

- automate startup (includes setting weather, populating question data, setting me as admin)
- automate maintenance (I have this as a GH issue at least)
- SSL cert (letsencrypt)
- get Elastic IP allocated and use it when we're all set
- point www to the allocated IP
- build forum on new `forum.riverofkurn.com` subdomain

... all of which I'm gonna go add to my repo so I can at least check them off when I do them. :P

And now, bed. At 3am. Note to future self: you were wondering why you're inflicting this on yourself at 3am on Wednesday, August 21, 2019. In case you were curious.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1anhcpAV9U/)

### Day 100: August 22, 2019
#### Hours spent coding: ~4

**Today's Progress**: I slept a bit last night instead of coding. It didn't work out wonderfully, but I definitely needed the break.

Anyway, welcome to Day 100. Insane.

I wish I had some resoundingly great news, but I don't. I have _some_ good news, though. We got the allocated IP and now my domain resolves to the website. This is great.

What's not great is trying to get an SSL certificate going. Let's Encrypt makes it super easy. Docker... does not.

Getting there, but hooooo boy. I have to run Let's Encrypt in the damn container. This may suck. Gotta do it, though.

Also, the `docker-compose` version? PERFECT. It fixed my hostname issues, so that's great. That means that I can get my game running beautifully, albeit without an SSL certificate at the moment.

Once the SSL stuff is dealt with, I'll have to work on a cronjob to run maintenance and backup stuff.

**Thoughts**: Very tired. And a little discouraged about the SSL stuff. It would be so easy without Docker! Not that I'm bitter.

As to the end of #100daysofcode, as I said, I'll keep writing, but it's kind of astonishing to me that I've spent 100 days (in the last 330+) coding. I didn't do this much coding in my diploma program.

I've learned a lot. I've banged my head against walls. I've refactored code. I've learned more about git. I've learned more about Composer. I've learned more about Docker. It's been a super valuable experience, if nothing else. I'm glad I tried, even if it took me almost a full calendar year to finish the challenge. But really, it's about getting my game to a point where I can share it with others and then work on refining it. I suspect I'll be doing this for a long, long time.

Thanks for reading. :)

**Link to work:** [Instagram post](https://www.instagram.com/p/B1fzMGKAKOz/)

### Day 101: August 24, 2019
#### Hours spent coding: ~7

**Today's Progress**: Pretty much the entirety of today's efforts were directed towards getting an SSL certificate working properly. After a variety of options and issues with each, I am certain I've done something sub-optimal. Still, it works. There's a little green lock by the URL. And it's repeatable, too! Even after bringing the Docker containers down, it's still there when it goes back up.

WHEW. I can refactor it Later(tm), but it works for now.

This leaves me with a few issues left:

- Fix question wrapper div padding (no big)
- Automate startup (should be doable)
- Automate backup routine (ditto)
- Automate maintenance routine (ditto, and will include the backup)

The other issues are optional-slash-can-be-done-later. I'm going to tackle those automations and then worry about the big one -- reloading assumes a right answer. I think I know why it's doing it, so paddling will likely require a small (?) refactor. I swear, I want to print out my code for that page.

**Thoughts**: Exhausted, but holy shit, I am so happy to have gotten the cert working. There's still a lot to do, but moving everything to AWS, getting an IP, redirecting the domain to the IP, getting the cert... all of it has taken a full week. And now it's done.

Everything else is just code, really. I can do the code parts. It's been the infrastructure stuff that has given me trouble.

Anyway. It's 6am. Bedtime.

**Link to work:** [Instagram post](https://www.instagram.com/p/B1lSFJAgTaT/)

### Day 102: September 1, 2019
#### Hours spent coding: ~8

**Today's Progress**: It's 7am on the 2nd and I'm wiped out. Bedtime shortly. BUT. So many things got done.

- Changed to 5 questions for the intro, and changed up the questions too
- Fixed question wrapper div padding
- Automated backup routine (wheeeee crontab)
- Set up the forum
- Set up SSL for the forum
- Edited forum link on various pages on the main site
- Wrote patch notes and an alpha FAQ for the forum
- Noted that the username will be visible to other users
- Tweaked registration etc notices to say if the user doesn't get an email within 30m to email through the website

Left to do, basically:

- Automating maintenance routine (includes minor .htaccess wizardry and bash scripting which I'm too tired to think about right now) 

Still haven't touched the reload issue and, frankly, I don't care. This sucker is going out later today.

**Thoughts**: Pooped. But feeling pretty damn productive.

**Link to work:** [Instagram post](https://www.instagram.com/p/B15_vjvgN_t/)

### Day 103: September 2, 2019
#### Hours spent coding: ~6

**Today's Progress**: And with that, folks, I am live.

[River of Kurn](https://www.riverofkurn.com/)

**Thoughts**: Excited and psyched and generally wow, but also tired. :D

**Link to work:** [Instagram post](https://www.instagram.com/p/B18FMS8A29-/)

### Day 104: September 6, 2019
#### Hours spent coding: ~2

**Today's Progress**: Chatted with my friend Andrew about the instance size (we upped it), the AMI, set up an S3 bucket, learned how backups to it work, etc. This led to me writing a pretty complicated (to me) bash script to replace the hacky maintenance I have going that's very reliant on several cron jobs. Anyway, this one should work, though I'll need to test it.

Tomorrow.

In the meantime, if you haven't played [River of Kurn](https://www.riverofkurn.com/), yet, what are you waiting for?

**Thoughts**: Now that the game is live, I cannot believe how much stuff I have to do. I need to plan out All The Things tomorrow.

**Link to work:** [Instagram post](https://www.instagram.com/p/B2GrJyiAKvE/)

### Day 105: September 21, 2019
#### Hours spent coding: ~6

**Today's Progress**: I haven't updated here at all, really, though I did renew my SSL cert the other week and have tweaked a couple of things.

Tonight, though, I did a full-on patch. I added questions, I changed stuff in the database (yet again), finally tested and edited my maintenance script and did assorted other things. Didn't fix the session bug -- maybe tomorrow.

Want to play [River of Kurn](https://www.riverofkurn.com/)? Go on. It'll be fun.

**Thoughts**: I have gone about things very stupidly in certain areas. Must fix those. Also, should plan things. I have not planned things out very well.

**Link to work:** [Instagram post](https://www.instagram.com/p/B2s_g5WAnXW/)