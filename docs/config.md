---
layout: default
title: Typesetter Configuration
description: Customize the creation and processing of Typesetter.
---
# Configuration

By default, the configuration used during generation is a `config.php` file in the local directory.  You can customize this with [command line options](generate-command-line-options) if you wish.  If you're using the Typesetter library directly and without the CLI, these configuration options reflect the keys of the configuration array.

## Config File Format

The configuration file should return an array from PHP.  You may have other functionality in it as well (it is require'd during the processing of the command).  It's recommended to use full namespaced class names when creating this file as the internal namespace may change as the project progresses.

## Creating Config Directly for the Library

Unless you're using the Typesetter functionality as a library, you can skip ahead.

Create a config array and pass that to the config maker. Then create a new instance of the Typesetter class. Call the generate method with your config to get a PDF binary return from MPDF.

Here is an example:

```php
$config = [
    'title' => 'Benjamin Button',
    'observers' => [
        new \Typesetterio\Typesetter\Observers\DefaultMarkdownConfiguration(),
    ],
];

$service = new \Typesetterio\Typesetter\Typesetter(
    new \Typsetterio\Typesetter\Config($config)
);
$pdfContent = $service->generate($config);
```

You can customize any of the functionality that you normally can in the `config.php` file directly in that array. Note that you must build the configuration option as detailed above in order to use the service.

## Options and Descriptions

Whether you're using the command line or Typesetter as a library, you have the following options to customize:

| Option  | Definition | Example |
|---------| ---------- | ------- |
| `title`  | The Title of your book. | `Benjamin Button` |
| `author` | The author of your book. | `F. Scott Fitzgerald` |
| `theme` | The path to the folder which contains your theme info. This should at minimum have a `theme.html` file in it. | `bb` |
| `content` | The path to the folder with your markdown in it | `./resources/content` |
| `contentFilter` | A callable that is applied as a filter after the content has been gathered. Return `true` to keep, `false` to remove. | `fn() => true `|
| `contentExtra` | A path that has extra content not associated directly with the main content. This is all content you want, no filtering. | `./resources/content-extra` |
| `toc-enabled` | Should Table of Contents be generated after cover? | `false` |
| `toc-links` | Should table of Contents link to the headers in your document? | `false` |
| `toc-header` | What header with `#toc-header` html attribute text? Empty will not generate one. | `Contents` |
| `footer` | What text should be in the footer? Footer is `<footer class="footer">` element. Leave empty to not generate a footer. | `Page {PAGENO}` |
| `markdown-extensions` | An array of file extensions that indicate they should be rendered. Remember pages are generated in alphabetical or numerical order. | `['md']` |
| `observers` | An array of new instances of observers. You can read more about them in the [advanced](advanced) section. | See above |

---

You're all set.  But, maybe you want to do some [advanced](advanced) configuration of your project next.