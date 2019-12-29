---
description: Quick list of the most common commands you'll need for the tutorial.
---

# Command-line cheatsheet

## Which folder am I in?

You can use the command line to move through folders on your computer, just like with Finder on a Mac or File Explorer on Windows.

To see your location in your computer's file system, use the **pwd** \(Print Working Directory\) command:

```bash
$ pwd
```

## See what's in a folder

You can get a list of all the files in your current location, using the **ls** \(list\) command.

```bash
$ ls
```

{% hint style="info" %}
Pro tip: anything in the list that is followed by a forward slash is a folder, e.g. `Desktop/`
{% endhint %}

You can even look at what's inside other folders. Let's say you're currently inside `Desktop/` and you want to see what's inside `Desktop/pics/`, you can do this:

```bash
$ ls pics/
```

## Go inside a different folder

If you want to go from `Desktop/` to `Desktop/pics/`, use the **cd** \(Change Directory\) command.

```bash
cd pics/
```

#### Go back up to the parent folder

If you decide you've had enough of `pics/` and want to go back up the chain to `Desktop/` you need to do something slightly different. 

`Desktop/` is one folder up, so you need to do this:

```bash
cd ..
```

The `..` means the parent folder, i.e. the folder that the current folder lives inside.

