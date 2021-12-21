---
title: Make a New File in the Same Directory in Vim
date: "2020-12-07"
---

```txt
TLDR
:w %:h/my-new-file.txt # write current buffer to a file in the same directory as the file you are editing
:sav %:h/my-new-file.txt # save current buffer to a file in the same directory as the file you are editing
```

## Making a new file

To make a new file in vim type:

```vim
:w my-new-file.txt
```

`:` enters command mode\
`w` writes\
`my-new-file.txt` is the name of the file

The new file is written in the root directory where you opened vim. So given this project structure:

```txt
├── fileA.txt
└── somedir
    └── fileB.txt
```

Your new file will end up in in the root.

```txt
├── fileA.txt
├── my-new-file.txt
└── somedir
    └── fileB.txt
```

This might not be what you want. If you want the file to be created in another directory, you can specify it.

```txt
:w somedir/my-new-file.txt

├── fileA.txt
└── somedir
    ├── fileB.txt
    └── my-new-file.txt
```

This works well enough. But it gets harder if you have a deeply nested project structure. Given this structure:

```txt
├── fileA.txt
└── somedir
    └── otherdir
        └── more
            └── evenmore
                └── wow
                    └── fileB.txt
```

You would have to type

```txt
:w somedir/otherdir/more/evenmore/wow/my-new-file.txt
```

**That's too long.**

## Making a new file in the same directory

To make a new file in the same directory as the file you are currently editing, and with the same contents, type:

```txt
:w %:h/my-new-file.txt
```

`%` refers to the current file\
`:h` removes the last component and any separator, which means `somedir/somename.txt` becomes `somedir` and `/my-new-file.txt` is the literal value to append.

## Why not use Nerd Tree?

I don't want to use Nerd Tree. I never need it, and I can't rely on it being installed on remote systems.

## Why not use netrw?

I do. But for this it's faster to type the command above.

## When do you use this?

Given this structure:

```txt
├── main.tom
└── services
    └── service1.tom
```

and a file I'm editing called `service1.tom` that looks like this:

```txt
class Service1 {
  do {
    // logic
  }
}
```

If I want to make a file called `service2.tom` that is mostly the same as `service1.tom`, I can do so by typing:

```txt
:w %:h/service2.tom
```

## Thanks

Thanks to the folks at `/r/vim` who helped me understand what `#:h` was doing. https://www.reddit.com/r/vim/comments/k8lsfy/please_help_me_understand_h/
