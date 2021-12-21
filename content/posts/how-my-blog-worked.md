---
title: How My Blog Works
date: "2019-01-06"
---

**[My blog no longer works like this, but this post is still fun.]**

I plan on blogging more and I've decided to host my own content. My blog was previously on Medium, but I wasn't happy with that for a few reasons.

## What's wrong with Medium?

1. When I read something on Medium, I don't care who the author is. All Medium articles look exactly the same, so it feels like they are all written by the same faceless person, and frankly, that faceless person is pretty boring. By hosting my own blog I can have a different look than most blogs. Maybe, in time, people will come to associate the look and feel of the blog with me, the guy writing it.

2. I want to store my write my blog posts in [Markdown](https://daringfireball.net/projects/markdown/). I like writing Markdown because it makes my posts portable. I'm not tied to a proprietary format. Markdown is easy to style and convert when needed. You can't, as far as I know, post in Markdown on Medium.

3. I want to be able to work on blog posts without connecting to a third-party website. In fact, I want to be able to work on my drafts without an internet connection at all. Why shouldn't I be able to work on my blog just because I'm on a plane?

4. Medium is struggling to find a sustainable business model. They could make decisions that increase profitability in the short-term, but make for a worse reading experience.

## Making it easy

Blogging is easy to put off. Like exercise, it's something that feels good to have done, and feels good to do when I'm in a groove, but it can be hard to motivate myself to write. I want to remove as much friction as possible. To that end, my blog posts are Markdown files that live in a folder on my computer. That folder lives inside my Dropbox folder. When I write or edit a blog post, it is synced with Dropbox. I can access my posts from anywhere, and if I break or lose my computer, they're safe. Writing a blog post is as easy as opening Vim.

## From Dropbox to Tom on the Internet

Getting a Markdown file from Dropbox to tomontheinternet.com was surprisingly easy. Dropbox let's you create `Apps` that have access to a part of your Dropbox folder. So, I created an app and gave it access only to my blog directory. Then, on my server, I used [this awesome package](https://github.com/spatie/flysystem-dropbox) to download my Markdown files on demand.

## Storing Markdown in MySQL

I wrote a parsing function that takes my posts and makes database representations of them. The contents of the Markdown file are stored, as is, in the database. However, the meta data is all generated automatically by looking at the title of the file. For example, the file "2018-07-05_dev-for-one-year_programming,webdev,career.md" would be turned into a post created on July 5th (the updated at date is grabbed from the file's timestamp). The slug is used as is. Finally, tags are created from the comma separated list (in this case, "programming", "webdev" and "career". And that's it. I have a blog with tags.

## Biggest benefit

By far the biggest benefit of this setup is that I can store my files in a format I like and have access to them whenever I want. The second biggest benefit? I feel like a super hacker writing my blog in Vim.
  

