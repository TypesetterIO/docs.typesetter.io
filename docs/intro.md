---
layout: default
title: Introduction to Typesetter
description: Getting to know Typesetter
---
# Introduction

Create ebooks, flyers, one-sheets and more from markdown! This command runs locally using PHP to convert your markdown into a PDF. You can even use the underlying library as a dependency of a PHP project.

## Installation

This requires PHP 8.1 or above.

This tool is meant to be part of the repository that you have your written content. Because of that, you can install it into the local directory with the following command.

```bash
composer require typesetterio/typesetter-cli
```

If you want to just use the Typesetter library itself in your project without getting the command line tools, use the following:

```bash
composer require typesetterio/typesetter
```

This documentation focuses on the main functionality of the project - using the command line option to generate ebooks. However, most of the configuration and methodology also applies to the library.

---

Let's move on to [usage](basic-usage) next.
