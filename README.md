# Invoice Boilerplate

Simple automated LaTeX invoicing system for companies and freelancers.

## Intro

Built along the lines of [cv-boilerplate](https://github.com/mrzool/cv-boilerplate) and [letter-boilerplate](https://github.com/mrzool/letter-boilerplate), this boilerplate contains the bare minimum to produce a professional-looking invoice with the least possible effort, so you can concentrate on things that matters.

![preview](preview.jpg)

The invoice content lives in `data.yml` and it's structured like so:

```YAML
invoice-nr: 2015-11-04
author: Max Mustermann
city: Musterstadt
from:
- Musterstraße 37
- 12345 Musterstadt
to:
- Universität Basel
- Petersplatz 1
- 4003 Basel
- Switzerland
VAT: 20
service:
- description: The first service provided
  price: 450.00
- description: And another one, with a list of details
  price: 245.00
  details:
    - Some more detailed explanation
    - of the service provided
    - Looking good
- description: The last service provided
  price: 245.00
```

When running `make`, [Pandoc](http://pandoc.org/) starts iterating on the data in the YAML file, populates `template.tex`, then pipes everything through XeTeX, which takes care of compiling a PDF ready to be printed/faxed/emailed and archived.

The math gets handled internally by LaTeX through the `spreadtab` package, Excel-style. You just need to provide a VAT rate and the prices for the individual services and the boilerplate takes care of the rest. Unicode support is provided by XeTeX.

Unless you intend to edit the template, no particular LaTeX knowledge is required to use this boilerplate.

## Dependencies

1. LaTeX with the following extra packages: `fontspec` `geometry` `ragged2e` `spreadtab` `fp` `xstring` `arydshln` `hhline` `titlesec` `enumitem` `xunicode` `xltxtra` `hyperref` `polyglossia`
2. [Pandoc](http://pandoc.org/)

To install LaTeX on Mac OS X, I recommend getting the smaller version BasicTeX from [here](https://tug.org/mactex/morepackages.html) and installing the additional packages with `tlmgr` afterwards. Same goes for Linux: install `texlive-base` with your package manager and add the needed additional packages later.

To install pandoc on Mac OS X, run `brew install pandoc`. To install it on Linux, refer to the [official docs](http://pandoc.org/installing.html).

## Getting started

1. Edit `data.yml` with your details, the invoice recipient's details, services and prices, and the desired settings.
2. Run `make` to compile the PDF.

Refer to [pandoc's documentation](http://pandoc.org/demo/example9/templates.html) to learn more about how templates work.

**Note**: this template needs to be compiled with XeTeX.

## Available settings

- **`VAT`**: Your VAT rate.
- **`currency`**: Your currency code (USD, EUR...)
- **`commasep`**: Set to true to use a comma as decimal separator. This is for display purposes only—remember to always use a dot to set the prices in your YAML file.
- **`lang`**: Sets the main language through the `polyglossia` package. This is important for proper hyphenation and date format.
- **`seriffont`**: Used for the heading and the sender address. Hoefler Text is the default, but every font installed on your system should work out of the box (thanks, XeTeX!)
- **`sansfont`**: Used to render the recipient address, the table and the final note.
- **`fontsize`**: Possible values here are 10pt, 11pt and 12pt.
- **`geometry`**: A string that sets the margins through `geometry`. Read [this](https://www.sharelatex.com/learn/Page_size_and_margins) to learn how this package works.
- **note**: This gets printed after the table as a closing note. Use it to provide your bank details and for your thank you message.

## Recommended readings

- [Grids of Numbers Recommendations](http://practicaltypography.com/grids-of-numbers.html) on Butterick's Practical Typography
- [Why Microsoft Word must Die](http://www.antipope.org/charlie/blog-static/2013/10/why-microsoft-word-must-die.html) by Charlie Stross
- [The Beauty of LaTeX](http://nitens.org/taraborelli/latex) by Dario Taraborelli

## See also

- [cv-boilerplate](https://github.com/mrzool/cv-boilerplate) — Easing the process of building and maintaining a CV using LaTeX
- [letter-boilerplate](https://github.com/mrzool/letter-boilerplate) — Quickly and painlessly generate high-quality letters from markdown through LaTeX

## License

[MIT](https://opensource.org/licenses/MIT)
