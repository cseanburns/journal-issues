# journal-issues

Published as:

Burns, C.S. (2023). The issues with journal issues: Let journals be digital libraries. *Publications, 11*(1).
[https://doi.org/10.3390/publications11010007](https://doi.org/10.3390/publications11010007)
Preprint:
[https://doi.org/10.48550/arXiv.2301.00832](https://doi.org/10.48550/arXiv.2301.00832)

This repo contains a manuscript on journal issues,
digital affordances, and open science
that was submitted to the journal
[Publications](https://www.mdpi.com/journal/publications) as
part of a 10th anniversary special issue of that journal.

The manuscript is written in Markdown.
Citations are added using the
[ZotCite](https://github.com/jalvesaq/zotcite)
Vim plugin and
[Zotero](https://www.zotero.org/).

The Markdown file is converted to HTML
and to ODT files using
[Pandoc](https://pandoc.org/).
I wrote the following Bash
functions to make the conversion
to APA formatted documents.

To convert to HTML in APA style:

```
#!/usr/bin/bash

# Date: 2022-3-14
# Convert a markdown file into an APA formatted file. 
# To be used with the Zotcite plugin for Zotero and Vim 

makeapa () {
  local sourcefile="$1"
  local zotfile="${HOME}/.vim/plugged/zotcite/python3/zotref.py"
  local apafile="${HOME}/Zotero/styles/apa.csl"
  pandoc "${sourcefile}" -s -o \
    "$(basename -s md "$sourcefile")"html -F\
    "${zotfile}" --citeproc --csl "${apafile}"
}

makeapa "$@"
```

To convert to ODT in APA style:

```
#!/usr/bin/bash

# Date: 2022-3-14
# Convert a markdown file into an APA formatted file. 
# To be used with the Zotcite plugin for Zotero and Vim 

makeapa () {
  local sourcefile="$1"
  local zotfile="${HOME}/.vim/plugged/zotcite/python3/zotref.py"
  local apafile="${HOME}/Zotero/styles/apa.csl"
  pandoc "${sourcefile}" -s -o \
    "$(basename -s md "$sourcefile")"odt -F\
    "${zotfile}" --citeproc --csl "${apafile}"
}
makeapa "$@"
```

