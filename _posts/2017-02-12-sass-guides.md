---
layout: post
title: SASS Guide
---

## What is Sass? 
Sass is a preprocessor. 

What is preprocessor? 

Preprocessor is a program that takes one type of data and transform it into another type of data.

In case of Sass, preprocessor takes Sass code and transform it into CSS code. 


## Why Sass? 

Sass has extra features (variables, nesting, more complex operations,...) that help save time when dealing with CSS.

## Installing Sass

To install Sass you need Ruby installed. If you are using Mac, it already has Ruby. If you are using Windows, the easiest way to install Ruby is to use [Ruby installer](https://rubyinstaller.org/).

The following steps are performed on Mac.

To check whether Sass is already install or not 

```bash
$ sass -v

Sass 3.4.23 (Selective Steve)
```

To install Sass

```bash
$ sudo gem install sass

Successfully installed sass-3.4.23
Parsing documentation for sass-3.4.23
Installing ri documentation for sass-3.4.23
1 gem installed
```

## Simple starter: Using sass command line to transform sass to css

Given sass a file at ~/project/sample.scss

```scss
body {
  background-color: green;
  p {
    font-size: 12px;
  }
}
```

To transfrom scss files, use `sass --watch` command

```bash 
$ cd ~/project
$ sass --watch sample.scss:sample.css

>>> Sass is watching for changes. Press Ctrl-C to stop.
      write sample.css
      write sample.css.map
```

Sass will transform `sample.scss` into `sample.css` and keep an eye on `sample.scss` (option `--watch`). As soon as it detects a change on `sample.scss`, it will re-transform again. 

The output: 

sample.css

```css
body {
  background-color: green; }
  body p {
    font-size: 12px; }

/*# sourceMappingURL=sample.css.map */
```
