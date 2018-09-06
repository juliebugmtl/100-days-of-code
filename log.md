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
