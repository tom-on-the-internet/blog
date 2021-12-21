---
title: I Like My ThinkPad Now, but the First Two Hours Were Horrifying
date: "2019-04-17"
description: I got a new ThinkPad...
---

In 2014 I bought the best computer I'd ever owned. Every interaction, every moment  was a delight. Installation was smooth, the OS was clean and everything felt just right. I was glad to have left Windows behind. I was happy with my new *MacBook Pro*. I was an Apple fanboy now, and I wasn't going back to Windows.

But that was five years ago, and last month when I decided I needed a new laptop, a new MacBook Pro wasn't the obvious choice for a replacement. A _lot_ had changed. MacBooks had gotten worse every year. No more MagSafe (magnetic charging cable), worse keyboard, very few ports... and I'd changed to. I'd switched careers from being a teacher, to being a software developer. I needed a new rig that could keep up with what I was doing. It needed to be able to run two instances of Intellij, host two VMs, and serve Angular all while YouTube was playing the Mr. Robot soundtrack on loop. A MacBook that could handle that would have cost me over $4000.

At the same time, I'd realized that if I wanted to be a great developer, I was going to have to really learn Linux. SSHing into Ubuntu boxes had taught me a bit, but not enough. I wanted to be in Linux all day, every day. So, what computer could I buy that would be able to handle not only my current needs, but the needs I'll have five years from now? What computer will "just work" with Linux? What computer looks _so cool_? Reddit told me to buy a ThinkPad.

I bought a T580. A beast of a machine. A machine that would would make my 2014 MacBook Pro look like a toy.
-  8th Generation Intel Core i7-8650U Processor with vPro (1.90GHz, up to 4.20GHz with Turbo Boost, 8MB Cache)
- 15.6" UHD (3480 x 2160) IPS anti-glare
- 32 GB (16 + 16) DDR4 2400MHz
- NVIDIA GeForce MX150 2GB GDDR5

I submitted my order and waited. It would arrive in less than a month.

## Unboxing

Finally, my ThinkPad arrived. I had my ThinkPad shipped to work because I wanted to unbox it with my co-workers. It didn't come in a nice box like my MacBook Pro had, but I didn't care. I unboxed the beast, plugged in my Ubuntu Live USB, and started installing. Things were looking good. Input? Colemak please. Location? Toronto. Encrypt the drive? Why of course. OK. Installation complete. Remove the USB and power it up... and something was _wrong_.

My Thinkpad was slow. Reeaaally slow. I couldn't even open a browser. I started sweating. Let's open a terminal and see if I can figure out - IT CRASHED!

"It's kernel panicking" said someone. I can't remember who. What was going on?! I rebooted. It crashed again. I kept sweating.

"You're not using a nightly build, are you?" No. I've learned that lesson.

"Is your USB drive broken?" It's brand new.

"Try reinstalling it." OK.

I reinstalled it. Colemak? Sure. Location? Still Toronto. Encrypt the drive? Myabe not this time... OK. Installation complete. Let's reboot and end this nightmare... It's _still_ slow?! Maybe I can run `top` and see if there are any - IT CRASHED AGAIN! What am I going to do? Do I have to send this thing back to Kunshan?

"What message did it print before crashing?" I dunno. Something about Nouveau.
"Ha ha ha. Oh boy! Good luck!!"

What the hell is Nouveau and why is it crashing my new laptop? Linux is supposed to work on ThinkPads. Reddit promised!

"It wasn't slow when you were installing?" asked Steven, a coworker who I don't think knows that much about Linux. I tell him it was fine. "Probably an Nvidia issue. You'll need to install the drivers." OK, but how? I can't even keep a terminal open.

Steven takes over. Turns out he knows a thing or two about Linux. He tries to explain to me that Nouveau is an open source driver for Nvidia cards. For some reason, I don't understand. Steven says that he's going to install the drivers for me by using the Live USB to mount my disk and use `chroot` so that the drivers are installed to the right place. Sure...

And all of a sudden it works. My ThinkPad is running. No kernel panic. It's fast, too. I can install programs, visit websites, play the Mr Robot soundtrack.

I ask Steven if I should install Nouveau now. "No... I don't think you understand the problem."

"Tom, write it down!" shouts Mike. "Write it down so you don't forget what happened." This is me writing it down.

## So, how is the ThinkPad T580?

I've been using the ThinkPad for almost a month now. Everything's been perfect. The screen is beautiful and the keyboard feels good. It's never slow. And I'm learning more about Linux. I've even `chroot`ed.

My goal with using Linux as my main OS is not to have a smooth experience. My goal is to learn a lot and become a better developer because of it. I don't want to be a visitor to the command line - I want to live there. Spending all day in Linux is getting me there, one problem at a time.

Here's to the next 5 years!

