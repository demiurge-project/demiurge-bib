# DEMIURGE-BIB

## How to use this repository

In order for this repository to work best, create a folder for all your papers.
Open a terminal in that folder and run:

    git clone https://github.com/demiurge-project/demiurge-bib.git demiurge-bib

In your .tex file include the following line to access the references:

    \bibliography{../demiurge-bib/definitions,../demiurge-bib/author,../demiurge-bib/address,../demiurge-bib/proceedings,../demiurge-bib/journal,../demiurge-bib/publisher,../demiurge-bib/series,../demiurge-bib/institution,../demiurge-bib/bibliography}

## How to contribute to the repository

1. Read the guidelines carefully.
2. Create a working copy of the repository (by branching or forking).
3. Edit the files according to the guidelines.  
   Please check if an entry is already present before adding it.
4. Commit your changes to your working copy.
5. Create a pull request from your working copy to the master branch.
6. We will review your edits and if they meet the standards outlined in this file, we will accept the pull request.

### What is a good commit message?

A good commit message consists of several parts.  
First comes one line that summarizes your edits. This line will be shown in the preview of github. Candidates for such a line could be "Added entries from GECCO2020", "Uploaded bibliography for ANTS2018 submission", "Fixed authors with more than two names".

Then you should add details of what you changed.

For example a good commit message could look like this:

    Updated author names for ANTS2018 paper of Kuckling et al.

    [Kuckling_J]: author key added
    [Birattari_M]: corrected typo in name

    [KucLigBozBir2018ants]: fixed author list
    [KucLigBozBir2018ants-supp]: fixed author list

### How do I create a pull request?

Use the github UI to create a pull request.
Select from demiurge-project/demiurge-bib the master branch as the base and your working copy as the compare branch.

## General guidelines

### How to choose the type of entry

* @Article:  
  Articles that have been published in a journal
* @InProceedings:  
  Articles that have been published in the proceedings of a conference
* @Book:  
  Books written by one or several authors
* @InCollection:  
  Works written by one or several authors, that are part of a collection (i.e. an appended collection of manuscripts from several authors)
* @PhDThesis:  
  PhD theses,
  if the thesis also was published as a book, cite the book instead
* @MastersThesis:  
  Master's theses
* @TechReport:  
  Technical reports
* @Misc:  
  Everything else (e.g. websites, software manuals, ...)  

### Generating a label for the entry

The label follows the general convention of ```[Authors][Year][Source]```.  
This differs from our previous standard by removing the colon ```:```.

##### Generating the author list in the label

The full rules can be found at http://iridia.ulb.ac.be/wiki/Conventions_for_Bibtex_labels  
As a summary: For up to four authors take the first three letters of each name, capitalize only the first letter of each name.
For more than four authors take the first three letters of the first three authors, capitalize only the first letter of each name. Then add ```-etal```.  

##### Generating the source identifier

For journals and proceedings use the same identifier as the key in the file ```journal.bib``` or ```proceedings.bib```. Note that for journals the identifier should be capitalized (e.g. SI), while for proceedings it should be uncapitalized (e.g. ants).  
For books, technical reports, phd teses, and master's theses the identifier is ```book```, ```techrep```, ```phd``` and ```master``` respectively.  
For works in collections and miscellaneous entries no general rule can be provided. Try to find a meaningful and descriptive identifier. **DO NOT LEAVE THE IDENTIFIER BLANK!**

##### Examples

The paper "Toward the formal foundation of Ant Programming" of Birattari, Di Caro and Dorigo, published 2002 at ANTS, then becomes ```BirDicDor2002ants```.

The paper "Hybrid metaheuristics for the vehicle routing problem with stochastic demands" of Bianchi, Birattari, Chiarandini, Manfrin, Mastrolilli, Paquete, Rossi-Doria and Schiavinotto, published 2006 in the Journal of Mathematical Modelling and Algorithms, then becomes ```BiaBirChi-etal2006JMMA```.

The paper "A Racing Algorithm for Configuring Metaheuristics" of Birattari, Stützle, Paquete and Varrentrapp, published 2002 at GECCO, then becomes ```BirStuPaqVar2002gecco```

### File structure

In order to decrease the variants of spellings for names, journals, conferences, etc. and in order to automate between using long and short versions of keys, this repository contains several files.

* [bibliography.bib](bibliography.bib): This file contains all bibliography entries. It will make use of the keys defined in other files.
* [author.bib](author.bib): This file contains entries for names of people. It is used to supply the keys for the fields ```author``` and ```editor```.
* [journal.bib](journal.bib): This file contains entries for journal names. It is used to supply the keys for the field ```journal```.
* [journal-short.bib](journal.bib): This file contains short entries for journal names. It is used to supply the keys for the field ```journal```. Whenever possible, it is recomended to use the original form in journal.bib.
* [proceedings.bib](proceedings.bib): This file contains entries for proceedings. It is used to supply the keys for the field ```booktitle``` of the @InProceedings entries in bibliography.bib.
* [proceedings-short.bib](proceedings-short.bib): This file contains short entries for proceedings. It is used to supply the keys for the field ```booktitle``` of the @InProceedings entries in bibliography.bib. Whenever possible, it is recomended to use the original form in proceedings.bib.
* [publisher.bib](publisher.bib): This file contains the entries for all publisher names. It is used to supply the keys for the field ```publisher```.
* [institution.bib](institution.bib): This file contains the entries for all institutions (university, research labs). It supplies the keys for the field ```school``` of the @PhDThesis and @MastersThesis entries and the field ```institution``` of the @TechReport entries in the bibliography.bib.
* [address.bib](address.bib): This file contains entries for addresses (city and country) for all journals and institutions. It supplies the keys for the field ```address```.
* [series.bib](series.bib): This file contains entries for publication series (such as LNCS). It supplies keys for the field ```series```.
* [series-short.bib](series.bib): This file contains short entries for publication series (such as LNCS). It supplies keys for the field ```series```. Whenever possible, it is recomended to use the original form in series.bib.
* [definitions.bib](definitions.bib): This file supplies keys used across all the files. For example, ```et al.```.

The file bibliography.bib contains all bibtex entries. New entries should be appended at the end of this file.
The other files only contain string definitions. These definitions should be kept in alphabetical order with regard to the key of the definition.

All files are indented with four spaces.  
The character ```=``` is justified using spaces (see templates).

### Bibtex entries
Bibtex entries should be as complete and correct as possible.  
The templates show the necessary information that needs to be included in every entry.  
If some fields are not applicable (e.g. a journal is not part of a series), then leave the field empty (e.g. ```series = {}```).
New entries should be added at the end of the file.

### Notes

LNCS (as probably other Springer series as well) issues separate volumes.
The number field is not used in this case.

For online publications (e.g. papers in an online only journal), specific identifiers should be put into the ```pages``` field.
For example Science Robotics uses a elocation-id (like eaav8006), which should be formatted as ```pages = {eaav8006}```.

We will not escape accents or special characters.
Make sure that your editor is set up with Unicode support (UTF-8 encoding).  
Note that some bibtex implementations might not support UTF-8.
In that case try and use Biblatex (with biber) instead.

Publications related to events (such as conferences, workshops or seminars) should be included as ```@InProceedings```.
Reference proceedings (and post-proceedings) from the file proceedings.bib.  
If the article was published in a special issue dedicated to the conference, it should be an ```@Article``` instead.
In that case the entry should be referencing the file journal.bib.

Sometimes titles or the list of authors can be long.
However **do not** put a line break in the field, as this hinders the tracking of changes that git can automatically do.

For conferences that are published in a different year, put the year of publication in the ```year``` field.
Sometimes an article becomes available online before the publication date.
In that case, use the publication date, as indicated by the publisher.

#### DOI

The field ```doi``` refers only to the identifier, not the URL at doi.org

Some DOIs contain an underscore.
**Do not** escape it as ```\_```.
Always keep the DOI in a shape that it can be pasted directly into doi.org.
If your bibliography does not comply with this convention, please look at ways of redefining the style or the doi command to handle the doi correctly.
Escaping in the bibliography is not an option as some styles handle the DOI correctly and would show the backslash in the bibliography.

#### Publishers:

In the case that a book is published in an imprint or that the original publisher was bought up by a publishing house (while keeping their brand as an imprint), use whatever name is more common.
For example "CRC Press" (an imprint of the "Taylor & Francis Group") is sufficiently well know to be used as publisher.
On the other hand, "A Bradford Book" (an imprint of "MIT Press") is not very know, and the publisher should rather be "MIT Press".

Springer has gone by many names in the past.
We will refer to all of them as Springer, nevertheless.

IEEE (Press) is not the same as IEEE Computer Society (Press).
However, if it is not clear if a publication was published be IEEE or IEEE Computer Society, the default is the IEEE publisher.

Ultimately, the goal of the adding the publisher is to give guidance on where to find additional information or from where to purchase a hard copy of the publication.

#### Address:

The field ```address``` is the address of the publisher (never the location that a conference took place).
It should be always of the form ```City, Country``` (e.g. ```Berlin, Germany```, ```Cham, Switzerland```, ```Brussels, Belgium```).  
If the address is located in the United States, use the format ```City, State, Country```, that is ```Piscataway, NJ, USA``` or ```Cambridge, MA, USA```.

#### Title:

Use sentence case (capitalizing only the first letter) for ```title``` fields.
Do not capitalize after a colon.
Words with defined capitalization (proper names, algorithms, etc.) should be escaped using curly braces ```{}``` (e.g. ```{AutoMoDe}```).
Algorithms that are only composed of regular words (simulated annealing, neural network) should not be protected.
Also enclose the full name in the curly braces and not only the parts you want to protect.
Do not use double curly braces as this will prevent the case changing algorithm from working correctly.
Do not use style commands (e.g. \texttt or \textit) in the title.  
Use title case (capitalizing everything but particles) for book titles.
This affects ```title``` fields of @Book entries, ```booktitle``` fields of @InCollection and @InProceedings (and for @InProceedings especially the value in the proceedings.bib files).  
The booktitle for proceedings (as defined in proceedings.bib) should be as written on the published proceedings.
If the title of the proceedings does not contain a reference to the conference, you can add the abbreviated name and year of the conference (prepended by a comma, e.g. ```, ANTS 2018```).

The field ```editor``` should contain the names of all editors of the publication.
In case that there are too many editors, the appearance should be controlled by the style and not by the file.

## Templates

#### Article
    @Article {,
        title        = {},
        author       = {},
        journal      = {},
        series       = {},
        volume       = {},
        number       = {},
        year         = {},
        pages        = {},
        doi          = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field use the keys from author.bib. <br>
For the ```journal``` field use the keys from journal.bib. <br>
For the ```series``` field use the keys from series.bib. <br>

#### InProceedings
    @InProceedings {,
        title        = {},
        author       = {},
        booktitle    = {},
        editor       = {},
        series       = {},
        volume       = {},
        number       = {},
        year         = {},
        pages        = {},
        publisher    = {},
        address      = {},
        doi          = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field and ```editor``` field use the keys from author.bib. <br>
For the ```booktitle``` field, use the keys from proceedings.bib. <br>
For the ```series``` field use the keys from series.bib. <br>
For the ```publisher``` field use the keys from publisher.bib. <br>
For the ```address``` field use the keys from address.bib. <br>

#### InCollection
    @InCollection {,
        title        = {},
        author       = {},
        booktitle    = {},
        editor       = {},
        series       = {},
        volume       = {},
        number       = {},
        year         = {},
        pages        = {},
        publisher    = {},
        address      = {},
        doi          = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field and ```editor``` field use the keys from author.bib. <br>
For the ```booktitle``` field, write the title here. Do not use the keys from proceedings.bib. <br>
For the ```series``` field use the keys from series.bib. <br>
For the ```publisher``` field use the keys from publisher.bib. <br>
For the ```address``` field use the keys from address.bib. <br>

#### Book
    @Book {,
        title        = {},
        author       = {},
        editor       = {},
        publisher    = {},
        address      = {},
        year         = {},
        edition      = {},
        doi          = {},
        note         = {},
        annote       = {},
    }
Choose either author (single author of the book or the same set of authors throughout the book) or editor field (otherwise). Leave the other field blank.  
For the ```author``` field and ```editor``` field use the keys from author.bib. <br>
For the ```publisher``` field use the keys from publisher.bib. <br>
For the ```address``` field use the keys from address.bib. <br>
For the ```edition``` field use the ordinal word (```Third```).

#### PhDThesis
    @PhDThesis {,
        title        = {},
        author       = {},
        school       = {},
        address      = {},
        year         = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field use the keys from author.bib. <br>
For the ```school``` field use the keys from institution.bib. <br>
For the ```address``` field use the keys from address.bib. <br>

#### MastersThesis
    @MastersThesis {,
        title        = {},
        author       = {},
        school       = {},
        address      = {},
        year         = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field use the keys from author.bib. <br>
For the ```school``` field use the keys from institution.bib. <br>
For the ```address``` field use the keys from address.bib. <br>

#### TechReport
    @TechReport {,
        title        = {},
        author       = {},
        institution  = {},
        address      = {},
        year         = {},
        number       = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field use the keys from author.bib. <br>
For the ```institution``` field use the keys from institution.bib. <br>
For the ```address``` field use the keys from address.bib. <br>

#### Misc
    @Misc {,
        title        = {},
        author       = {},
        howpublished = {},
        year         = {},
        note         = {},
        annote       = {},
    }
For the ```author``` field use the keys from author.bib. <br>
If the source was published online, then add ```\url{www.the-true-source.com}``` in the field ```howpublished```.
