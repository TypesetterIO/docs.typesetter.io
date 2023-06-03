---
layout: default
title: Quick Start
---
# Quick Start Guide

Create ebooks, flyers, one-sheets and more from markdown! This command runs locally using PHP to convert your markdown into a PDF.

In this quick-start guide, we're going to look at creating an ebook from our markdown. The end result will be similar to our [example book](https://github.com/TypesetterIO/example-book).

## Steps

First, initialize and version a folder using Git - you can git ignore the `vendor` folder if you wish (but you don't have to). Remember this is a book project, not necessarily a PHP package/project.

Then, install the CLI tool

```bash
composer require typesetterio/typesetter-cli
```

After it's installed, you can generate a default configuration to customize.  

```bash
vendor/bin/typesetter init
```

This will generate some test content and a config file.

Customize the `config.php` with the author and title and replace `content/*` with my contents for your book.

A test cover has been generated for you at `content/cover.jpg`. Feel free to replace this with art that reflects your ebook.

If you want more customization, modify the  `theme/theme.html` with custom print media CSS.

Finally, generate the output:

```bash
vendor/bin/typesetter generate --output=generated/my-book-title.pdf
```

You'll find the generated ebook in the `generated` folder.

You've done it!

## Example

If you want to see an example and learn a bit about Laravel, check out the tips ebook from No Compromises in the [example book project](https://github.com/TypesetterIO/example-book) or just peek at the [PDF](https://github.com/TypesetterIO/example-book/blob/main/generated/tips-ebook.pdf) directly.

## Next Steps

Want to learn more? Check out the [documentation](intro) to learn more.
