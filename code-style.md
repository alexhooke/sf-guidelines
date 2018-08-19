# Code Style Guidelines
 
## Status of this Document

The intent of this guide is to reduce cognitive friction when scanning code
from different authors.
 
The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”,
“SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be
interpreted as described in [RFC2119](https://www.ietf.org/rfc/rfc2119.txt).
 
## 1. General rules

### 1.1. Files

All files with code MUST end with a single blank line.

### 1.2. Lines

There MUST NOT be a hard limit on line length.

The soft limit on line length MUST be 120 characters; automated style checkers
MUST warn but MUST NOT error at the soft limit.

Lines SHOULD NOT be longer than 80 characters; lines longer than that SHOULD
be split into multiple subsequent lines of no more than 80 characters each.

There MUST NOT be trailing whitespace at the end of non-blank lines.

Blank lines MAY be added to improve readability and to indicate related
blocks of code.

There MUST NOT be more than one statement per line.

### 1.3. Indenting

Code MUST use an indent of 4 spaces, and MUST NOT use tabs for indenting.

N.b.: Using only spaces, and not mixing spaces with tabs, helps to avoid
problems with diffs, patches, history, and annotations. The use of spaces
also makes it easy to insert fine-grained sub-indentation for inter-line
alignment.

### 1.4. True / False / Null

The Apex constants <code>true</code>, <code>false</code>, and <code>null</code> MUST be in lower case.