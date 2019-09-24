# XML Typesetting

Typesetting in XML is an essential part of journal article production. XML formatted according to the journal article tag suite used by the [NLM](https://jats.nlm.nih.gov/) ensures that the article can be rendered for online display. It is a [requirement](https://www.ncbi.nlm.nih.gov/pmc/about/guidelines/#techqual) to provide XML for inclusing in PMC.

Typesetting in JATS XML is facilitated using Texture, a free open source XML editor.

## XML Typesetting with Texture

Creating the XML version of your article requires 3 steps.

1. Download [Texture](https://github.com/substance/texture/releases). This guide was written using Texture 2.2.
2. Copy and paste your article into Texture.
3. Add additional metadata that is not currently implemented by Texture.

## Pasting your article into Texture

Texture allows you to edit your article metadata and content separately, insert references, figures and tables. Here are some tips:

* Enter your references in the order that they appear in your reference list. This will make it easier to give them numeric labels later.
* You can add references by inputting the DOI into Texture. To improve the way your article displays, remove the day and month of publication from your reference information after you have added it.
* For authors, 'Name' refers to 'Surname' or 'Last name'.
* Texture doesn't allow you to select CC-BY-NC as a license. If you are choosing the CC-BY-NC license, select the CC-BY license and then change the license url later.
* You must define headings as "Heading 1", "Heading 2" or "Heading 3".
* Link your in-text references figures, tables or citations using the "Insert" menu, under the "Inline" section.

## Metadata not implemented by Texture

When you save your article, Texture will save it in .dar format. This is just a zip file that contains your article's XML and figures. An easy way to extract your XML for editing is to change the .dar extension to .zip. You can then extract your article's XML.

You'll then need to work through the following additions.

### Journal metadata

Immediately after the `<front>` tag, copy and paste the journal's metadata:
```
    <journal-meta>
      <journal-id journal-id-type="publisher-id">Neuroanatomy and Behaviour</journal-id>
      <journal-title-group>
      <journal-title>Neuroanatomy and Behaviour</journal-title>
      <abbrev-journal-title abbrev-type="publisher">NAB</abbrev-journal-title>
      </journal-title-group>
      <issn pub-type="epub">2652-1768</issn>
      <publisher>
      <publisher-name>Episteme Health Inc.</publisher-name>
      <publisher-loc>
      <city>Melbourne</city>
      <state>Victoria</state>
      <country>Australia</country>
      </publisher-loc>
      </publisher>
    </journal-meta>
```

### Complete article metadata

Texture doesn't yet allow you to add the DOI for your article or MeSH subject categories for your article. So you'll need to do this manually by copying and pasting the following immediately after the `<article-meta>` tag:
```
    <article-id pub-id-type="publisher-id">e-id</article-id>
    <article-id pub-id-type="doi">10.35430/nab.YYYY.e-id</article-id>
    <article-categories>
    <subj-group>
    <subject>Biological Sciences</subject>
    <subj-group>
    <subject>Neurosciences</subject>
    </subj-group>
    </subj-group>
    </article-categories>
```
And replace `YYYY` with your publication year and `e-id` with your submission number, prefixed with an `e` (e.g. e123).

### Fix corresponding author tags for display

While Texture includes the details of the corresponding author, they need to be repeated in the following way or they will not display in LENSreader on the journal website.

1. Find the corresponding author's `<contrib>` tags. Add the following tag before the `</contrib>` tag:
```
<xref rid="cor001" ref-type="corresp">*</xref>
```
The result should look like this:
```
        <contrib id="person-ece5add46632453d9cc03f98a42f0d58" contrib-type="person" equal-contrib="no" corresp="yes" deceased="no">
          <name>
            <surname>Author</surname>
            <given-names>Genius Scientist</given-names>
          </name>
          <email>email@domain.tld</email>
          <xref ref-type="aff" rid="organisation-6b61f11b67cec178e344128ac8499776" />
          <xref rid="cor001" ref-type="corresp">*</xref>
        </contrib>
 ```

2. After the last `</aff>` tag, add the corresponding author email(s):
```
<corresp id="cor001">*<email xlink:type="simple">email@domain.tld</email></corresp>
```
You can have multiple corresponding authors. Just assign each one a different id (e.g. corresp id="cor1" and corresp id="cor2") and a different symbol (e.g. * and ^).

### Copyright and Permissions

If you haven't entered your copyright statement in Texture (or need to modify your license tag), you can simply and copy and paste the relevant copyright and permissions tags into the XML here. Look for the tag `<permissions id="permission">`. Immediately after this tag, for a CC-BY-licensed article, you should end up with:
```
        <copyright-year>YYYY</copyright-year>
        <copyright-holder>Author Names</copyright-holder>
        <license>
          <ali:license_ref>http://creativecommons.org/licenses/by/4.0/</ali:license_ref>
        </license>
        <copyright-statement>Except where otherwise noted, the content of this article is licensed under <ext-link ext-link-type="uri" xlink:href="http://creativecommons.org/licenses/by/4.0/" xlink:type="simple">Creative Commons Attribution License</ext-link>, which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited</copyright-statement>
```
Where `YYYY` is replaced with the year of publication and `Author Names` are your surnames (e.g. Author and Author; or Author et al.)

If you want a CC-BY-NC-licensed article, you should end up with:
```
        <copyright-year>YYYY</copyright-year>
        <copyright-holder>Author Names</copyright-holder>
        <license>
          <ali:license_ref>http://creativecommons.org/licenses/by-nc/4.0/</ali:license_ref>
        </license>
        <copyright-statement>Except where otherwise noted, the content of this article is licensed under <ext-link ext-link-type="uri" xlink:href="http://creativecommons.org/licenses/by-nc/4.0/" xlink:type="simple">Creative Commons Attribution-NonCommercial 4.0 International License</ext-link>.  In addition to this license, reuse of a reasonable portion of the work for fair dealing purposes under Australian copyright law, such as medical research, education, scholarship, or not-for-profit or charitable purposes, is also permitted. For additional permissions, please contact the corresponding author.</copyright-statement>
```

### Label the reference list

Texture doesn't number each item in your reference list, so we need to do this manually in order for it to display in the online reference list.

Look for the `<ref-list>` tag. Each citation begins with a `ref` tag. For each reference you need to add the following immediately after the `ref` tag:
```
<label>#n</label>
```
Where #n is the reference number.

You should end up with something like this:
```
      <ref id="journal-article-ref-ddc0ff83231e3b9cd8588b8f2478f8e1">
      **<label>1</label>**
        <element-citation publication-type="journal">
          <issue>1</issue>
          <page-range>640-660</page-range>
          <volume>53</volume>
          <year>2012</year>
          <pub-id pub-id-type="doi">10.1234/651654sd51</pub-id>
          <person-group person-group-type="author">
            <name>
              <surname>Author</surname>
              <given-names>First Name</given-names>
            </name>
            <name>
              <surname>Author</surname>
              <given-names>First Name</given-names>
            </name>
          </person-group>
          <source>Journal Name</source>
          <article-title>Article title: Very interesting article</article-title>
        </element-citation>
      </ref>
      
      <ref id="journal-article-ref-9868e663c05a07990a7460a90243036b">
      **<label>2</label>**
        <element-citation publication-type="journal">
          <issue>6</issue>
          <page-range>640-660</page-range>
          <volume>53</volume>
          <year>2012</year>
          <pub-id pub-id-type="doi">10.5647/5818185624</pub-id>
          <person-group person-group-type="author">
            <name>
              <surname>Author</surname>
              <given-names>First Name</given-names>
            </name>
            <name>
              <surname>Author</surname>
              <given-names>First Name</given-names>
            </name>
          </person-group>
          <source>Journal of Scientific Papers</source>
          <article-title>A paper which reports studies in behavioural neuroscience</article-title>
        </element-citation>
      </ref>
```

### Save your XML file

Now save your XML file and return it to us for publication!
