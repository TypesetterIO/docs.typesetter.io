---
layout: default
title: Using Typesetter
description: Basic usage of Typesetter.
---
# Basic Usage

Before we continue, note that there are two other great resources you may want to also look at.

First, you can look at the core library [typesetterio/typesetter](https://github.com/TypesetterIO/typesetter). This has the underlying service class and may give you more context. (You don't need to do that, though, if you just want to generate an ebook from your markdown on the command line.)

Second, check out the [example project](https://github.com/TypesetterIO/example-book) to see one way of setting up a project. While you're there, you can get a free ebook!

Normally, this is meant to be used on the command line. The simplest way to use this would be like this:

```bash
vendor/bin/typesetter generate
```

But that's if everything is set up perfectly. And it has some options. Let's dig in.

## Initialization

So, you installed it - now what? You can run the init command which will generate some content for you to review and modify.

```bash
vendor/bin/typesetter init
```

Then you'll find a local `config.php` that contains options for you to change. In addition, you'll receive a folder for your content. You can replace your content there.

## Generation

After you've updated your configuration and put in your content, you can generate the book:

```bash
vendor/bin/typesetter generate
```

Boom! You'll find the output PDF directly in the same directory. Now you're done!

---

Ok now, where do you put your content? Or how do you make your own cover? That's covered in the [content](content) section.
