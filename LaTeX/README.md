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

```
\section{}
\subsection{}
\cite{}
\begin{figure}
\begin{table}
\ref{fig:id}
```
NB: If you copy and paste the block for `\begin{figure}` in the template it will try and make your figure a 1-column figure by default. If you want a figure that spans two columns, just an add asterisk to it - `\begin{figure*}`.

### Article Options

The main.tex file has watermarking options and settings for the authors' choice of license:

1. Draft watermark. If you are just submitting your article, you should leave `\watermark{draft}` as is (line 18). If your article is accepted and you are preparing it for publication, you should change it to `\watermark{none}`.
2. Choice of License. If you are using the default CC BY license, you should leave `\togglefalse{NC}` as is (line 72). If you want to use a CC BY-NC license, comment it out `%%% \togglefalse{NC}` and uncomment `\toggletrue{NC}` (i.e. delete the `%%%`.

### Article Metadata

The main.tex file has metadata fields that you'll need to complete for:

1. Article title (line 33)
2. Author names (lines 36-40). The author names are duplicated on line 40 for the sake of PDF metadata. The template provides the examples of `\authfn{2}` to denote an equal contribution for authors 1 and 2.
3. Affiliations and Author notes (lines 42-47)
4. Paper Category (line 50). This should be Research Article, Review, Professional Perspectives, Correspondence, Commentary or Editorial.
5. 'Short' Author list for a running page heard (line 53). This should be abbreviated 'et al.' when there are 3 or more authors.
6. Keywords list (lines 56-61). Replace 'Keyword One' through to 'Keyword Six' with your keywords. If you use fewer than 6 keywords, you should remove the unused keyword functions `\kwdxxx` from line 84, lines 363 and 378, and delete the `\newcommand{}{}` function for each unused keyword (lines 56-61).
7. Article volume, number, year and DOI (lines 64-68). Article volume `\jvolume` follows calendar year, beginning with volume 1 in 2019. `\jnumber` should always be 1, `\jarticlenum` should be an e followed by submission number (e.g. e99), `\jyear` should be the year and `\jdoi` should follow the specified format (e.g. `\jdoi{10.35430/nab.2019.e99`).

### References

The `\cite{}` command will extract the necessary details from your .bib file. Make sure your .bib file is in the same directory as your other LaTeX files and the name of your .bib file is specified in `\bibliography{}` - the default name is 'paper-refs'. In your .bib file, a citation is formatted as follows:

```
@article{referenceID,
   author = {Lastname, Given Names and Lastname, Given Names and Lastname, Given Names},
   title = {The article title},
   journal = {Journal Title},
   volume = {53},
   number = {6},
   pages = {640-660},
   DOI = {10.xxxx/123456}
   url = {https://doi.org/10.xxxx/123456},
   year = {2012},
   type = {Journal Article}
}
```

Most citation managers will allow you to export your article's references as a .bib file. If you did not use a citation manager, you can get help converting your citations to .bib using [text2bib](https://text2bib.economics.utoronto.ca/) (registration required) thanks to Fabian Qifei Bai and Martin J. Osborne at the University of Toronto.

Insert the referenceID into the \cite command, e.g. `\cite{referenceID}`. If you need to cite more than one article, separate the IDs by a comma, e.g. `\cite{ref1,ref2,ref3}`. Reference numbering and inclusion in the reference list will then be done automatically.

### Special characters

Beware special characters such as `%` and `&`. These characters have a special meaning in LaTeX and so can stop your article from typesetting. To use these characters in text, insert a `\` before them, e.g. `\&` to ensure that they are interpreted as text, rather than code. This goes for both main.tex and your paper references .bib file.

### Figures and Tables

The template main.tex has multiple examples of figures and tables that are either a single column or full column wide. Tables can also be set horizontally. Modify these templates to obtain your desired effect, paying attention to the instructions in the comments (anything after a `%` symbol).

## Typeset your article

You can now save your work and typeset your article. Make sure to select `LuaLaTeX+MakeIndex+BibTeX` before typesetting (in TeXworks it is a green arrow).

Please send all of your typesetting files (i.e. main.tex, paper-refs.bib + any figures) along with your .pdf in case any changes need to be made by editors before publication.
