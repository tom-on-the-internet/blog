---
title: The Phoenix Project (Tom on Books)
date: "2019-02-24"
---

[The Phoenix Project](https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business-ebook/dp/B00AZRBLHO) is novel about IT at a large company  going horribly wrong and then improving. If that sounds interesting to you, you're probably a very particular kind of geek, like me, who is interested in how technology can be best integrated into an organization. If that sounds boring to you, please never read this book.

There's a meme going around that all companies are now technology companies, and those companies that realize it too late are doomed. Bill Palmer, the protagonist of the novel, is the new VP of IT at a company that hasn't yet realized that they are a technology company first and an automotive parts manufacturer second. Bill spends the duration of the novel uncovering problems with IT and then trying to uncover and implement solutions to them. He has help from a mysterious advisor and a group of co-workers. Working against him is the inertia of the company.

## Why I chose to read this novel

I'm learning more about IT operations. Instead of only focusing on the code that guides the software I write, I want to learn about how the underlying infrastructure works (the cloud, these days). In the last 5 to 10 years a movement has begun called DevOps. It's the combination of software **dev**eleopment and IT **op**erations. It used to be common for there to be a development team who would build software and an operations team who would make sure the software ran. The DevOps movement arose out of a need to foster collaboration between these teams (and in some cases combine them).

Anyone aspiring to learn more about DevOps will find themselves bombarded withe recommendations to read the Phoenix Project, and so I did.

## Recommending the Phoenix Project

If you're a developer who uses tools like Git, JIRA and Jenkins but has never thought much about them, I'd recommend the Phoenix Project. There's been a paradigm shift in software development, and newer developers might be missing some of the context.

If you're a developer at a company who is still FTPing into servers to "fix one small bug", please comiserate with this book and then give your copy to your boss.

If you're a manager at a technology company (and all companies are becoming technology companies), this book could help you understand why those damn developers want to waste so much time on process. It might also help you realize that the fastest solution in the short-term is often the slowest solution in the long-term.

Don't make the same mistake that I did in assuming that this novel has any intention of actually being a novel. The authors were clever in their approach. A novel is a soft entry into a complicated topic and it allows for readers to slowly convince themselves that they are dealing with the same problems as those found in the book. This book isn't a novel you could recommend to anyone outside of the IT world, but it's the lightest technical reading you can find.


**Below this point is my own experience with the novel and lessons learned. Minor spoilers.**


## What I thought at first

I didn't care for the Phoenix Project. The characters were boring. They were cliches who spoke in cliches. Eric, an advisor to Bill, was the worst of them all. Eric is an [omniscient](https://tvtropes.org/pmwiki/pmwiki.php/Main/TheOmniscient), a mysterious character who knows everything. He shows up from time to time to spoon feed Bill the knowledge needed to solve his current problem, and then disappears again.

The problems Bill was trying to solve didn't seem relevant to me. He was dealing with physical servers, complicated deployment procedures, and coworkers who didn't realize that technology was the lifeblood of their organization.

Every character being a cliche, and every problem being hard to relate to, made the book hard to read, at first. To make things worse, the main character (and anyone who he got on his side) were always right. When they predicted catastrophe, it happened. When they developed solutions, they always worked. *IT is the most important department, and you better not forget it!* It got bad enough that I had to put the book down. I'm glad I did.

## What I though next

About a week after putting the book down, I began to look differently at the day to day goings-on in my department.

Some bad code (that I wrote) made it into production. We removed it from production, but an unrelated task put it back in production. The code was insignificant, and quickly removed again, but it made me think "Eric and Bill would have something to say about this."

Our team also had a debate about how to best measure our output. When we talked about getting work done, what work should be counted? Meetings weren't work, were they? Can we measure bugs the same way we do features? 

And then there was a task that only one developer could complete. A large number of other tasks were waiting on the first task, and no matter how fast our team as a whole was, it didn't matter because the one developer had become a constraint.

Suddenly, the problems that Bill was trying to solve for his large automotive parts manufacturer didn't seem so irrelevant. Our small, "agile" company suffered from many of the same kinds of issues. I decided to continue reading the Phoenix Project and take notes.

## Lessons learned

I began my career as a software developer in 2017. We used a system to track tickets, moving them from one side of the board to the other. We set up continuous integration. Our code lived in version control. These were the practices every team was expected to follow, and I took them for granted because it seemed like they worked and that every company was using them. The Phoenix Project helped me realize how important these processes are and what the end goal of these processes is. 

The "Agile/DevOps" tools were created to solve the problem of companies moving too slowly and never being able to keep up with market demands. Some of the specific questions these tools answer are:

1. What work do we have in progress?
2. How much work can we expect to get done by next week?
3. How much of our work is unplanned? (The Phoenix Project makes it clear that unplanned work is a major problem because it stops companies from completing their real work)
4. Is this code good?
5. Does this code do what we think it does?
6. Will this code behave properly in production?
7. What changes have we made recently? (Having an answer to this question is especially important because it helps us understand what is causing bugs.)
8. Are things working?
9. Are things working better or worse that they used to?
10. Should we remove this feature?

The Phoenix Project helped me see why we have all these tools in place and why they've quickly become essential for modern development.

## Best practices in practice

Imagine your company realizes that the structure of one of your database tables is a little wrong. It's missing a foreign key constraint. How should you go about fixing this?

1. You could SSH into the DB and run an `ALTER my_database_table` command, right? This would take **5 minutes at most**, right? Problem solved, right?

The Phoenix Project, Agile, and the whole DevOps movement would never speak to you again if you did that. Instead, a better work flow would be...

1. Add the issue to the backlog.
2. Discuss the issue at the sprint planning meeting. Perhaps another developer can give you insight into why the foreign key wasn't added in the first place, or point out an issue with adding that foreign key, or explain that adding the constraint is pointless because of one reason or another.
3. Assuming the task isn't rejected, instead of connecting to the database directly, you write a "migration" in code. You test it out locally to see that it behaves as you expect it to.
4. You submit your change through a PR process. A developer points out to you that your code could be improved. You learn something and fix it. The code gets approved.
5. The code goes into production. It fixes the foreign constraint on the database. Also, it fixes the same issue on the demo server that you had forgotten about. Whew.
6. All of your fellow devs run your code locally. You're now developing against the same environment.
7. A new dev is hired and runs your migration to get their local database in the same shape as yours.
8. Another developers code is rejected because their code doesn't work with the change you made. They are able to see why the change was made and revise their code.

That's a longer process. But in time, it saves time. It reduces risk and makes resolving issues easier.

The rule is: **Every change to a system must be recorded.**

## Final thoughts

The Phoenix Project was a massive success in a market that I don't think may people knew could exist: Instructive IT Fiction. It's an oddity, but I hope it starts a trend. It's been surprisingly sticky.

