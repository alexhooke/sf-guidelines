# Code Style: Lightning Platform
 
## Status of this Document

The intent of this guide is to reduce cognitive friction when scanning code
from different authors.
 
The keywords “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”,
“SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be
interpreted as described in [RFC2119](https://www.ietf.org/rfc/rfc2119.txt).

## 1. Naming Conventions

Naming conventions make the application easier to read and maintain. The naming standards documented here cover 
customisation and configuration areas of Salesforce. 

### 1.1. General rules

The API name of metadata entity (custom objects, fields, flows etc.) MUST use 
[Snake_Case](https://en.wikipedia.org/wiki/Snake_case) notation where each new word starts with a capital letter.

### 1.2. Custom Objects

The object name MUST be singular. (e.g. Review vs. Reviews)
