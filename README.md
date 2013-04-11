![Karban](https://raw.github.com/mre/karban/master/assets/karban_small.png)

I hate accounting, especially invoicing. It's a repetitive, mind-boggling task, that steals away my energy; thus should be
handled by a machine. Believe me, I would give my pinky toe if I never ever had to do it again.
At most I just want to scribble a few notes and be done with it.
Maybe Tyler King hat the same thoughts while he created [Markdown Invoice][] to solve the problem.
It turns Markdown invoices into HTML or PDF.
Of course his tool is totally rad, so I borrowed it and adjusted it to my own needs.
This somehow grew out of my hand and I added a bunch of features and gave it a new name - karban.
Karban is a hacker-friendly, static invoice generator. It's kinda like [Jekyll][], but for invoices.

## How?

Simple. Put your invoices into the `invoices/` directory.
See `sample.md` for an example invoice in Markdown and its PDF output.

## Example run:

```bash
./karban --invoice="invoices/2424-11-04-xxx" --output=pdf --layout="layouts/unicorns.html"
Compiling invoice "invoices/2424-11-04-xxx"...
PDF saved to: invoices/2424-11-04-xxx.pdf
```

## Features

* Fancy HTML/CSS invoice layouts (with separate headers and footers) using [Twig][]
* PDF output
* Meta data using [YAML FrontMatter][]
* Multiple layouts
* Keep a plain text version of your invoices; text files are awesome.
* Completely adaptable to your own workflow

```bash
./karban --help
Usage:
 karban [-f|--format[="..."]] [-o|--output[="..."]] [-l|--layout[="..."]] [invoice]

Arguments:
 invoice               Name of an invoice in Markdown format

Options:
 --format (-f)         Format can be HTML or PDF (default: "pdf")
 --output (-o)         Output directory for the generated envoice
 --layout (-l)         Layout for invoice (default: "layouts/layout.html")
 --help (-h)           Display this help message.
 --quiet (-q)          Do not output any message.
 --verbose (-v)        Increase verbosity of messages.
 --version (-V)        Display this application version.
 --ansi                Force ANSI output.
 --no-ansi             Disable ANSI output.
 --no-interaction (-n) Do not ask any interactive question.
```

## Installation

### Instructions for Mac

#### Step 1: Karban requires PHP 5.4 or higher. If you have an older version of PHP make an upgrade

     curl -s http://php-osx.liip.ch/install.sh | bash -s 5.4

#### Step 2: Make PHP 5.4 to your standard distribution

     export PATH=/usr/local/php5/bin:$PATH
     (write this into your ~/.profile to make it permament)

#### Step 3: Install composer

     curl -sS https://getcomposer.org/installer | php
     sudo mv composer.phar /usr/local/bin/composer

#### Step 4: Download Karban

     git clone https://github.com/mre/karban.git

#### Step 5: Go into the Karban folder and run composer

     cd karban && composer install

## Credits

All credits go to [Tyler King][] who created the original Markdown Invoice.

## Note

At the moment you have to fiddle around with the page breaks when things go awry. That's a known issue caused by wkhtmltopdf. Yeah, it sucks; the only alternative might be to look for an alternative or wait for a proper fix since all the available hacks are messy. For the time being, you can use ```<div class="pagebreak"></div>``` anywhere in your markdown invoice to force a page break.


[Jekyll]: https://github.com/mojombo/jekyll
[Tyler King]: https://github.com/tyler-king
[Markdown Invoice]: https://github.com/tyler-king/markdown-invoice
[Twig]: http://twig.sensiolabs.org
[YAML FrontMatter]: https://github.com/Blaxus/YAML-FrontMatter
