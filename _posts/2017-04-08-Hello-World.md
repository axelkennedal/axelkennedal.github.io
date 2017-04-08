---
layout: post
title: "Pandoc: The new era of fancy documents"
---

# Tired of LaTeX?
Me too. That's why I thought there had to be a less painful way to create professional-looking documents for reports etc. Then I found a tool called *Pandoc* which essentially is a command line utility which allows you to convert textfiles between different formats. Turns out you can use this to **write markdown and convert it to PDF!** The cool thing is that it uses LaTeX "under the hood", meaning you can write beautiful markdown and have it turned into beautiful PDF:s!

## Getting Started
Here's a quick example of how you can use Pandoc. First download and install [Pandoc](http://pandoc.org/installing.html). Next create a markdown file somewhere on your computer, open it up and fill in the following:

```markdown
---
title: Pandoc Rocks!
author: A cool dude
date: \today
---

# So Amazing
Apparently you can create cool documents using markdown!

## Important Topic
I think bacon is a fundamental human right.
```

Save it, then use a bash terminal and execute the following (when you're in the same directory as your markdown file): ```pandoc markdownfile.md -o pdffile.pdf``` (where you of course replace the filenames with something that makes sense). **BOOM!** Pandoc should now have generated a LaTeX-looking pdf for you, and the only LaTeX you wrote was ```\today```! (If you haven't written markdown before; it's super simple and you can learn the essentials [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).)

## Necessary Evils
Okay so maybe I lied a little bit, you do have to write a teeny tiny bit of LaTeX here and there - but it's actually not too bad! For an example you might want to have the title, author and date be on it's own page, simple - just use ```\newpage```. Also you might want some fancy headers and footers, here's an examaple of that:

```markdown
---
title: Logic Design Lab (LD-Lab)
author: Axel Kennedal
date: \today
header-includes:
    - \usepackage{fancyhdr}
    - \pagestyle{fancy}
    - \fancyfoot[CO,CE]{Axel Kennedal}
    - \fancyfoot[LE,RO]{\thepage}
---
\newpage

# Assignment 1: Decoder
## Task 1.1
Below is a screenshot of my implementation of 2:4 decoder, made in Logisim.

![Schematics of the decoder](decoder.png){width=50%}

Verifying the correctness of the design was as simple as looking at the standard truth-table for a 2:4 decoder, trying out the four possible binary inputs to my implementation and checking whether the output was the same as in the truth-table. One could say I used perfect induction (although for proving the correctness of a circuit, not a theorem).
```
As you notice I introduced a new property of the document; ```header-includes```, use a ```\newpage``` and I also included an example of using images. As you can see you don't need any special packages or anything for that, you just write it with markdown and even speficy a width as simple as that.
Below is what the PDF looks like.

<div style="height: 10px;"></div>
<img src="pandoc_example1.png" style="width:50%;border: 1px solid #EEE;"/>
<img src="pandoc_example2.png" style="width:50%; float:left; border: 1px solid #EEE;"/>
<div style="height: 10px;"></div>

**That's pretty much it.** And oh yeah, you (almost) everything you can do in markdown, you can do here and convert to LaTeX:ish documents, like tables, lists and so on. If you find anything worth adding to this tutorial, feel free to fork and make a pull request with your changes. I've for an example seen you can use templates to style the PDF:s in more detail, might be worth to check out.
