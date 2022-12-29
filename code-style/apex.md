# Code Style: Apex
 
## Status of this Document

The intent of this guide is to reduce cognitive friction when scanning code
from different authors.
 
The keywords “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”,
“SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be
interpreted as described in [RFC2119](https://www.ietf.org/rfc/rfc2119.txt).
 
## 1. General rules

### 1.1. Files

Each top-level global or public class MUST start with an ApexDoc on the first line, containing a high level description of its purpose.

All files with code MUST end with a single blank line.

All files with code MUST be encoded in UTF-8.

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

_N.b.: Using only spaces, and not mixing spaces with tabs, helps to avoid
problems with diffs, patches, history, and annotations. The use of spaces
also makes it easy to insert fine-grained sub-indentation for inter-line
alignment._

### 1.4. True / False / Null

The Apex constants <code>true</code>, <code>false</code>, and <code>null</code> MUST be in lower case.

## 2. Naming Conventions

Naming conventions make the application easier to read and maintain. The naming standards documented here cover customisation and configuration areas of Salesforce. 

### 2.1 Rules common to all identifiers

Identifiers MUST use only ASCII letters and digits. Thus each valid identifier name is matched by the regular expression `\w+`.

Special prefixes or suffixes SHOULD NOT be used. For example, these names are not acceptable: mName, s_name and kName.

### 2.2. Classes and Interfaces

Class names MUST be **nouns**.

Interfaces names SHOULD be **nouns** or **adjectives**.

Use whole words and SHOULD avoid acronyms and abbreviations.

### 2.3. Methods

Methods MUST be verbs, in mixed case with the first letter lowercase and with the first letter of each internal word 
capitalised.

### 2.4. Constant names

Constant names MUST use CONSTANT_CASE (all uppercase letters, with each word separated from the next by a single underscore).

Constants are static final fields whose contents are deeply immutable and whose methods have no detectable side effects. 
If any of the instance's observable state can change, it is not a constant. Merely intending to never mutate the object 
is not enough.

### 2.5. Non-constant field names (properties, variables and etc.)

Variable names SHOULD be short yet meaningful.

Non-constant field names (static or otherwise) MUST be written in lowerCamelCase.

One-character variable names SHOULD be avoided except for temporary variables.

_N.b.: Common names for temporary variables are i, j, k, m, and n for integers; c, d, and e for characters._

## 3. Classes, Properties, and Methods

The term “class” refers to all classes and interfaces.

### 3.1 Extends and Implements

The extends and implements keywords MUST be declared on the same line as the class name.

The opening brace MUST be on the same line with the class name; the closing brace for the class MUST go on the next line after the body.

```java
public class ClassName extends ParentClass implements Countable {

    // constants, properties, methods
}
```

### 3.2 Properties

There MUST NOT be more than one property declared per statement.

### 3.3 Methods

Visibility MUST be declared on all methods.

Method names MUST NOT be declared with a space after the method name. The opening brace MUST be on the same line with the method name, and the closing brace MUST go on the next line following the body. There MUST NOT be a space after the opening parenthesis, and there MUST NOT be a space before the closing parenthesis.

A method declaration looks like the following. Note the placement of parentheses, commas, spaces, and braces:

```java
public class ClassName {

    public static void fooBarBaz(Integer arg1, String arg2) {
        // method body
    }
}
```

### 3.4 Method Arguments

In the argument list, there MUST NOT be a space before each comma, and there MUST be one space after each comma.

Argument lists MAY be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list MUST be on the next line, and there MUST be only one argument per line.

When the argument list is split across multiple lines, the closing parenthesis and opening brace MUST be placed together on their own line with one space between them.

```java
public class ClassName {

    public static void aVeryLongMethodName(
        List<Account> accountsBeforeUpdate,
        List<Account> accountsAfterUpdate,
        Boolean isAdminMode,
        Boolean isSomething
    ) {
        // method body
    }
}
```

### 3.5. abstract, final, and static

When present, the abstract and final declarations MUST precede the visibility declaration.

When present, the `static` declaration MUST come after the visibility declaration.

```java
abstract public class ClassName {

    final public static String CONSTANT_NAME = 'TEST';
}
```

### 3.6. Method and Function Calls

When making a method or function call, there MUST NOT be a space between the method or function name and the opening parenthesis, there MUST NOT be a space after the opening parenthesis, and there MUST NOT be a space before the closing parenthesis. In the argument list, there MUST NOT be a space before each comma, and there MUST be one space after each comma.

```java
// TODO: example
```

Argument lists MAY be split across multiple lines, where each subsequent line is indented once. When doing so, the first item in the list MUST be on the next line, and there MUST be only one argument per line.

```java
// TODO: example
```


## 4. Control Structures

The general style rules for control structures are as follows:

* There MUST be one space after the control structure keyword
* There MUST NOT be a space after the opening parenthesis
* There MUST NOT be a space before the closing parenthesis
* There MUST be one space between the closing parenthesis and the opening brace
* The structure body MUST be indented once
* The closing brace MUST be on the next line after the body

The body of each structure MUST be enclosed by braces. This standardizes how the structures look, and reduces the likelihood of introducing errors as new lines get added to the body.

### 4.1. if, else if, else

An if structure looks like the following. Note the placement of parentheses, spaces, and braces; and that else and elseif are on the same line as the closing brace from the earlier body.

```java
if (expr1) {
    // if body
} else if (expr2) {
    // else if body
} else {
    // else body;
}
```

### 4.2 switch

// TODO

### 4.3 while, do while

A `while` statement looks like the following. Note the placement of parentheses, spaces, and braces.

```java
while (expr) {
    // structure body
}
```

Similarly, a `do while` statement looks like the following. Note the placement of parentheses, spaces, and braces.

```java
do {
    // structure body;
} while (expr);
```

### 4.4 for

A `for` statement looks like the following. Note the placement of parentheses, spaces, and braces.

```java
for (Integer i = 0; i < 10; i++) {
    // for body
}
```

A list or set iteration `for` loop statement looks like the following. Note the placement of parentheses, spaces, and braces.

```java
for (Custom_Record__c record: customRecords) {
    // for body
}
```

A SOQL `for` statement looks like the following. Note the placement of parentheses, spaces, and braces.

```java
for (Custom_Record__c record: [SELECT Id FROM Custom_Record__c LIMIT 10]) {
    // for body
}
```

### 4.5 try, catch

A `try catch` block looks like the following. Note the placement of parentheses, spaces, and braces.

```java
try {
    // try body
} catch (FirstExceptionType e) {
    // catch body
} catch (OtherExceptionType e) {
    // catch body
}
```