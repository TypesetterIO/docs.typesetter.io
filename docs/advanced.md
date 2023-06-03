---
layout: default
title: Typesetter Advanced Usage
description: Customize themes, fonts, modify core functionality and listen to events.
---
# Advanced Usage

In this section, more advanced usage and configuration is covered.

## Observers

Observers allow a decorator or visitor style of design pattern to interact with the process of generating this PDF.  To make things
as transparent as possible, some core items of the service are even configured in observers. 

Observers must implement the `Typesetterio\Typesetter\Contracts\Observer` interface.  You may extend the 
`Typesetterio\Typesetter\Observers\Observer` abstract class so you don't have to define every interface method. Then, you can 
override only the ones you want.

Observers are ran in the order they are registered.

Available observer methods available are the following:

| Method | Definition | Parameters |
| ------ | ---------- | ---------- |
| `initializedMarkdownEnvironment` | After the Commonmark Environment has been initialized, this will allow customization of it. | `League\CommonMark\Environment\Environment` that you can add extensions or renders. |
| `parsed` | After a chapter's markdown has been parsed into HTML and set into a Chapter. The chapter makes methods available to understand the context and modify the HTML. Note that the abstract observer class offers a `getDomDocument()` method that accepts a Chapter and returns a DomDocument. Then you can modify or parse content easier if you'd like. | `Typesetterio\Typesetter\Chapter` |

The following Observers are available for you. They should all be prefixed by `Typestetterio\Typesetter\Observers`:

| Class | Definition | Parameters |
| ----- | ---------- | ---------- |
| `BreakToPageBreak` | Puts a page break after the template tag `{BREAK}` | The template to use - defaults to `{BREAK}` |
| `FirstElementInChapterCSSClass` | Puts a css class of `chapter-beginning` on the first element of every chapter except the first. | The class (defaults to `chapter-beginning`) and a boolean whether to skip the first chapter (default is `true`) |

## Chapter

The `Typesetterio\Typesetter\Chapter` class contains the content of your markdown for that specific chapter.

It contains a number of useful methods for you to interact with the content while it is being converted.

| Method                | Definition                                                                                             |
|-----------------------|--------------------------------------------------------------------------------------------------------|
| `getHtml()` | Get's the rendered HTML from markdown. Remember, this may have been modified by other observers first. |
| `setHtml($html)` | You must set the HTML after you've modified it.  This will cast to string if it's not already. |
| `getChapterNumber()` | Returns an integer indicating which chapter number this is. |
| `getTotalChapters()` | Returns an integer indicating how many total chapters there is to be parsed. |
| `isFirstChapter()` | Returns a boolean indicating if you're dealing with the first chapter. |
| `isLastChapter()` | Returns a boolean indicating if you're dealing with the last chapter. |

If you'd like to just get some status updates or notifications and don't need to modify any content, check out Events.

## Events

During the process of conversion, Typesetter issues some events that you may listen to. This can be useful for giving status updates or creating logs.

In order to register a listener, call the `listen` method with an event class and a callable.

Here's an example:

```php
$service = new \Typesetterio\Typesetter\Typesetter();
$service->listen(\Typesetterio\Typesetter\Events\Finished::class, function () use ($myNotifier) {
    $myNotifier->alert('The process has finished');
});
```

At this time events do not contain any data. If you want to modify anything, please look at observers.

The following events are available (these are all going to be in the `Typesetterio\Typesetter\Events` namespace):

| Event | Definition |
| ----- | ---------- |
| `Starting` | When the `generate()` method is first called. |
| `InitializedMarkdown` | After the markdown environment has been created and all observers have ran on it. |
| `PDFInitialized` | After the MPDF instance has been created and lightly configured. |
| `ThemeAdded` | When the theme has been found and applied to the PDF. |
| `CoverImageAdded` | A cover image has been found in your content and added. |
| `CoverHtmlAdded` | A cover html file has been found in your content and added. |
| `CoverGenerated` | Typesetter was unable to find either cover option so it generated one. |
| `TOCGenerated` | The Table of Contents has been generated and added. |
| `FooterGenerated` | The footer content has been generated and added. |
| `ContentGenerating` | The content has started rendering. This likely is the longest part of the process. |
| `PDFRendering` | The PDF has started rendering from HTML to PDF binary. This may also take a long time. |
| `Finished` | The whole process has finished and a PDF string has been returned from the method. |

You may listen to as many or as little events as you want. Remember, some of these are optional events based on your configuration.

## Themes

Theming support is done with HTML and CSS. The theme folder should contain a `theme.html` which contains a `<style>` declaration
as if it were in the head of an HTML file. This is where you can customize the theme of your PDF. Remember that you will 
be working with print styles in CSS so you can use things like page break.

More to come here!

## Fonts

At this time, Typesetter only supports the fonts that MPDF does. It will support font management in the future.

To see the list of fonts that are available, see the [MPDF Fonts Directory](https://github.com/mpdf/mpdf/tree/v8.1.6/ttfonts).

---

You're all set.  Still need some help? You might try looking at the [example book project](https://github.com/TypesetterIO/example-book) to get some hints.
