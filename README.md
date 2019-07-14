# Article Production

This repository includes resources for article production in PDF and XML format.

# LaTeX template

A LaTeX template is provided based on the oup-contemporary class by Oxford University Press and Overleaf. In order to use this package, authors and typesetters will need to download a LaTeX editor, such as the free [MiKTeX](https://miktex.org/) package.

## Typesetting in LaTeX

Most authors will probably write their article in Word or similar software and may have little to no prior experience using LaTeX. But most people should be able to typeset an article with some basic instructions and a little bit of help.

In order to typeset the PDF, it is first necessary to get some of the following:
1. The reference list in .bib format. This can usually be exported from a citation manager like Endnote or Zotero.
2. Figures as high quality image files. For line drawings (e.g. graphs), vector formats are ideal because they retain quality when zooming in and out. For example, graphs can be exported from Prism in PDF format or line drawings can be saved in .svg format.

Place these assets in the same directory as the LaTeX files.

## Modify main.tex

To typeset your article, modify main.tex by adding your author details and article text to the document. The file is set up so that most of the areas where you will need to make changes have been annotated using comments (anything after the % symbol).

Some of the main commands that most authors will have to use are:

<code>\section{}</code>

<code>\subsection{}</code>

<code>\cite{}</code>

<code>\begin{figure}</code>

<code>\begin{table}</code>

### References

The <code>\cite{}</code> command will extract the necessary details from your .bib file. Make sure your .bib file is in the same directory as your other LaTeX files and the name of your .bib file is specified in <code>\bibliography{}</code> - the default name is 'paper-refs'. In your .bib file, a citation is formatted as follows:

>@article{referenceID,
>
>   author = {Lastname, Given Names and Lastname, Given Names and Lastname, Given Names},
>
>   title = {The article title},
>
>   journal = {Journal Title},
>
>   volume = {53},
>
>   number = {6},
>
>   pages = {640-660},
>
>   DOI = {10.xxxx/123456}
>
>   url = {https://doi.org/10.xxxx/123456},
>
>   year = {2012},
>
>   type = {Journal Article}
>
>}

Insert the referenceID into the \cite command, e.g. <code>\cite{referenceID}</code>. If you need to cite more than one article, separate the IDs by a comma, e.g. <code>\cite{ref1,ref2,ref3}</code>. Reference numbering and inclusion in the reference list will then be done automatically.

### Special characters

Beware special characters such as <code>%</code> and <code>&</code>. These characters have a special meaning in LaTeX, so can stop your article from being typeset. To use these characters in text, insert a <code>\</code> before them, e.g. <code>\&</code> to ensure that they are interpreted as text, rather than code.

### Figures and Tables

The template main.tex has multiple examples of figures and tables that are either a single column or full column wide. Tables can also be set horizontally. Modify these templates to obtain your desired effect, paying attention to the instructions in the comments (anything after a <code>%</code> symbol).

## Typeset your article

You can now save your work and typeset your article. Make sure to select <code>LuaLaTeX+MakeIndex+BibTeX</code> before typesetting (in TeXworks it is a green arrow).
