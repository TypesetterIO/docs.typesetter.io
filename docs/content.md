---
layout: default
title: Typesetter Content
description: Learn how to add content and customize the cover.
---
# Content

You probably want to make an ebook fo your own content and markdown, right?  Let's dig in to this.

## Markdown Content

The `content` folder holds the content that is coupled with your config to create the PDF.

### Cover

There are three options for a cover.  The image or the html file should be in the content folder.

First, you can generate a cover image.  The file should be named `cover.jpg`.  The default configuration for MPDF is 96dpi.  The default page is a A4.  This means a standard resolution that fits that is 794 x 1123 (96dpi).  You may experiment with different values for larger resolution displays. Remember, the
larger in size your image, the larger the resulting PDF may be.

Second, you can generate a cover with HTML. The file should be named `cover.html`. For more details, reference the HTML processing of [MPDF](https://mpdf.github.io/).

Finally, if you do not create either of these, Typesetter will automatically generate a cover page. It will use your title and author configuration options.

### Chapters

Chapters should be generated in sequentially named files in your content folder. Refer to [League Commonmark](https://commonmark.thephpleague.com/) for
more tips on writing and configuring markdown processors. Out of the box there is a pretty good configuration. This includes the following functionality:

* Github-flavored markdown
* Attributes
* Spatie's Fenced Code / Indented Code renders

---

But that's not it. Next, you can check out the [command line options](generate-command-line-options) for generation, [config customization](config) to configure your book options, or [dig deeper into the advanced options](advanced) of Typesetter.
