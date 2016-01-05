---
layout: post
title: Weird behaviors of Saucelabs' Firefox
---

I was testing a feature, when one filter is clicked, 25 out of 42 results will be shown.
I wrote the test and got the specs passed two days before Xmas. Two days later, it is not working on Saucelabs.

I can pass the tests on standalone Selenium Server locally. But when tested on Saucelabs, it just won't pass.
The video shows that after clicking the filter checkbox, the number indicating the sum of results shows 17, then just 3 or 4 seconds later, the sum becomes 0. And the test ends here.
First I thought it happens because the Ajax has not been finished yet.
So I used setTimeout() (yeah, this primitive tool is my only option...) to wait the results to settle down.
But however long I wait, the browser just stuck to the 0 result.

Tested manually in the browser, everything works fine. Tested manually on the same environment and browser in Saucelabs's manual testing session, still everything is okay.

I asked Jessie about this, no clue, asked Serban later, still no clue, but suggested he could help check the log of dev server. 
The server log showed that not a single request was made during testing using Firefox on Saucelabs. Weird. 
Running tests on standalone Selenium server locally, however, leaves requesting records in server's log.
Yeah, completely at a loss now.
Then I tried Chrome on Saucelabs, and weirdly it works. And log shows it's hitting the server.
Then tried IE on Saucelabs' automation tests, and IE worked.
So it was the Firefox running on Saucelabs that causes problems? So Firefox on Saucelabs request nothing to the server, then why it was getting all the page?

Still no clue, there are just too many things going behind the scene and I don't about them.

Right now, I am going to stick to Chrome to avoid those weird problems.

Maybe will try debugging Firefox on Saucelabs later.
