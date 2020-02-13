# XML Typesetting

Typesetting in XML is an essential part of journal article production. XML formatted according to the journal article tag suite used by the [NLM](https://jats.nlm.nih.gov/) ensures that the article can be rendered for online display. It is a [requirement](https://www.ncbi.nlm.nih.gov/pmc/about/guidelines/#techqual) to provide XML for inclusing in PMC.

Typesetting in JATS XML is facilitated using Texture, a free open source XML editor.

## XML Typesetting with Texture

Creating the XML version of your article requires 3 steps.

1. Download [Texture](https://github.com/epistemehealth/texture/releases/tag/v3.01-nab). This version of Texture has been specially modified for typesetting articles in Neuroanatomy and Behaviour.
2. Copy and paste your article into Texture.
3. Complete your article metadata

## Pasting your article into Texture

Texture allows you to edit your article metadata and content separately, insert references, figures and tables. Here are some tips:

* Enter your references in the order that they appear in your reference list.
* You can add references by inputting the DOI into Texture. You can add multiple DOIs at a time to speed things up.
* You need to select a license - usually a CC BY license is the default.
* You must define headings as "Heading 1", "Heading 2" or "Heading 3".
* Link your in-text references figures, tables or citations using the "Insert" menu, under the "Inline" section.
* If your article is very long and you find that Texture is slowing down (e.g. you have more than 70-100 references), you can typeset parts of the article separately and then knit the XML together.

### Article Metadata

Texture has a nearly complete set of metadata options in the manuscript details page. Fill in the following:

1. Volume - Neuroanatomy and Behaviour publishes one volume a year, with volume 1 in 2019.
2. E-Location ID: Enter the manuscript number (e.g. e10).
3. DOI: Enter the manuscript's DOI, which has the format `10.35430/nab.YYYY.e##` where `YYYY` is the current year and `e##` is the e-location ID.
3. Published Date - Put in today's date in ISO 8601 format (i.e. YYYY-MM-DD). Optional: Put in your submission and acceptance dates in 'Received Date' and 'Accepted Date' respectively.
4. Copyright Year and Copyright Holder can be left blank and will be automatically populated with the current year and `The Author(s)`.
5. Corresponding Author Note - Enter the corresponding author's email address. Don't forget to check the corresponding author checkbox for the relevant authors.

#### Authors and Affiliations

Authors can be added and linked to affiliations and funding. Provide each author's name and ORCID URL (e.g. `https://orcid.org/0000-0009-9999-9999`) whenever possible. If the author is a corresponding author, check the corresponding author box and provide their contact details in the Corresponding Author Note in the main article metadata section.

Affiliations should be given with the Department, Institution, City, State/Province and Country. ISNIs can be searched for at [isni.org](https://www.isni.org).

#### Funders

Funders can be entered with their institution, institution identifier and award identifier. Institution identifiers should be searched for at the [Crossref Funder Registry](https://www.crossref.org/services/funder-registry/).

#### Subjects

Find appropriate subject headings using the [MeSH Browser](https://meshb.nlm.nih.gov/search).

Add subjects by clicking on `Insert` and then `Subject`. Usually `Biological Sciences` and `Neurosciences` are sufficient. These should be entered as separate subject names (there is no need to fill subject category).

#### Keywords

Add author-provided keywords in the same way as for subjects - one keyword per box. 

## Save your XML file

Now save your XML file. Texture outputs .dar files, which are just zip files. Make sure to complete your typesetting before closing Texture as loading files may not work. Send the .dar file to us or, to extract your XML, change `.dar` to `.zip` and extract `manuscript.xml`.
