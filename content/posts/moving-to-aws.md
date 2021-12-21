---
title: Moving to AWS
date: "2019-10-20"
---

I recently moved my website from Digital Ocean to AWS. Here's the what and the why.

## Why Move?

I had a perfectly good website set up on Digital Ocean. It was a single server running Linux, NGINX, MySQL and Laravel PHP. It was fast, and flexible. I never had downtime issues. So... why move?

AWS knowledge is [in demand](https://workremotetechnologies.tomontheinternet.com/), and I didn't know AWS very well. There's so much to AWS that you can't learn without putting things into practice, and what better practice than hosting my own site?

Also, I'd made an architectural mistake on Digital Ocean. Everything was tightly coupled. All websites ran on a single virtual machine. My virtual machine was set up manually, so I couldn't quickly (or automatically) recreate it. My blog, portfolio, and a game I'd made were all on the same subdomain. They were all part of the same Laravel app. I hadn't set up a CI/CD pipeline, so deployment meant sshing into the server and running `git pull`. It's hard to believe that when I was building this site a year ago I thought that any of that was a good idea.

So, AWS would be good to learn, and it would help me escape my own poor architecture.

## Current Setup on AWS

Every website I build on AWS gets it's own domain. So far they are all subdomains of [tomontheinternet.com](https://tomontheinternet.com). The websites don't know anything about each other. Or at least nothing more than any other website would know. This allows me to create new websites easily, and play around with new technologies.

I'm making heavy use of [AWS Amplify](https://aws.amazon.com/amplify/) to host my sites. So far, all of my sites have been static. So, no more server, no more database. Also, deployments are as simple as `git push`. It's also cheaper. Pennies a month.

I plan on doing some more complicated AWS setups, but it's so nice for now to have simple static sites that are hosted around the world.

## Challenges

Route 53 and DNS were the biggest challenges for me. It's not always clear why a website refuses to resolve. Sometimes you need to wait a few minutes, sometimes you need to add a record, and sometimes you need to remove a conflicting record. I'm happy at how much more comfortable I am with Route 53 with only a month of use.

## Next

Just keep shipping.

