# 100 Days Of Code - Log

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
