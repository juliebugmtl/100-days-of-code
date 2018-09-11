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
