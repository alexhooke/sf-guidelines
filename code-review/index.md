# Salesforce Code Review Guide

## Introduction

A code review is a process where someone other than the author(s) of a piece of
code examines that code.

We use code review process to maintain the quality of our code and products.

This documentation is the canonical description of code review processes and policies.

This page is an overview of our code review process. There are two other large
documents that are a part of this guide:

-   **[How To Do A Code Review](reviewer-guide.md)**: A detailed guide for code
    reviewers.
-   **[The MR Author's Guide](author-guide.md)**: A detailed guide for developers
    whose MRs are going through review.

## What Do Code Reviewers Look For?

Code reviews should look at:

-   **Design**: Is the code well-designed and appropriate for your system?
-   **Functionality**: Does the code behave as the author likely intended? Is
    the way the code behaves good for its users?
-   **Complexity**: Could the code be made simpler? Would another developer be
    able to easily understand and use this code when they come across it in the
    future?
-   **Tests**: Does the code have correct and well-designed automated tests?
-   **Naming**: Did the developer choose clear names for variables, classes,
    methods, etc.?
-   **Comments**: Are the comments clear and useful?
-   **Style**: Does the code follow our
    [style guides](../code-style/index.md)?
-   **Documentation**: Did the developer also update relevant documentation?