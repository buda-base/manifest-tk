# Pagination specifications

This document documents the features of the standard pagination string used in the format. We hope that by doing this pagination data can be shared between projects more easily.

### Poti folios

This is the main pagination type, used in Tibetan pechas, and most Indic and Southeast Asian manuscripts. It is composed of three components:

- `folionum`: the indicated folio number, an integer (not padded with 0: `1`, not `01`)
- `duplind`: duplicate indication: some Tibetan pechas have two (or more) folios with the same number in a row, which is sometimes indicated as *གོང་མ།* (first) / *འོག་མ།* (second). We indicate the duplication with a single quote character `'`.
- `side`: recto or verso, indicated as `a` / `b` (lower case)
- `certaintyind`: an indication of uncertainty: `?`
- `detailind`: an indication that an image is a detail of a page, this is indicated by `(d)` where `d` can be followed by any number if several images of details are present: `(d1)`, `(d2)`, etc.

The following Python regexp is catching all the components of this pagination type:

```regex
(?P<folionum>\d+)(?P<duplind>'*)(?P<side>[ab])(?P<certaintyind>\??)(?P<detailind>\(d\d*\))?
```

