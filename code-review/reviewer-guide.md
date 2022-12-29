# Code Review: Reviewer Guide

## The Standard of Code Review

The primary purpose of code review is to make sure that the overall
code health of code base is improving over time. All of the 
tools and processes of code review are designed to this end.

In order to accomplish this, a series of trade-offs have to be balanced.

A reviewer has ownership and responsibility over the code they are
reviewing. They want to ensure that the codebase stays consistent, maintainable,
and all of the other things mentioned in
["What to look for in a code review."](#what-to-look-for-in-a-code-review)

Thus, we get the following rule as the standard we expect in code reviews:

**In general, reviewers should favor approving a MR once it is in a state where
it definitely improves the overall code health of the system being worked on, 
even if the MR isn't perfect.**

That is _the_ senior principle among all of the code review guidelines.

There are limitations to this, of course. For example, if a MR adds a feature
that the reviewer doesn't want in their system, then the reviewer can certainly
deny approval even if the code is well-designed.

A key point here is that there is no such thing as "perfect" code&mdash;there is
only _better_ code. Reviewers should not require the author to polish every tiny
piece of a MR before granting approval. Rather, the reviewer should balance out
the need to make forward progress compared to the importance of the changes they
are suggesting. Instead of seeking perfection, what a reviewer should seek is
_continuous improvement_. A MR that, as a whole, improves the maintainability,
readability, and understandability of the system shouldn't be delayed for days
or weeks because it isn't "perfect."

Reviewers should _always_ feel free to leave comments expressing that something
could be better, but if it's not very important, prefix it with something like
"Nit: " to let the author know that it's just a point of polish that they could
choose to ignore.

Note: Nothing in this document justifies checking in MRs that definitely
_worsen_ the overall code health of the system. The only time you would do that
would be in an [emergency](emergencies.md).

### Mentoring

Code review can have an important function of teaching developers something new
about a language, a framework, or general software design principles. It's
always fine to leave comments that help a developer learn something new. Sharing
knowledge is part of improving the code health of a system over time. Just keep
in mind that if your comment is purely educational, but not critical to meeting
the standards described in this document, prefix it with "Nit: " or otherwise
indicate that it's not mandatory for the author to resolve it in this MR.

### Principles

*   Technical facts and data overrule opinions and personal preferences.

*   On matters of style, the [style guide](../code-style/index.md)
    is the absolute authority. Any purely style point (whitespace, etc.) that is
    not in the style guide is a matter of personal preference. The style should
    be consistent with what is there. If there is no previous style, accept the
    author's.

*   **Aspects of software design are almost never a pure style issue or just a
    personal preference.** They are based on underlying principles and should be
    weighed on those principles, not simply by personal opinion. Sometimes there
    are a few valid options. If the author can demonstrate (either through data
    or based on solid engineering principles) that several approaches are
    equally valid, then the reviewer should accept the preference of the author.
    Otherwise the choice is dictated by standard principles of software design.

*   If no other rule applies, then the reviewer may ask the author to be
    consistent with what is in the current codebase, as long as that doesn't
    worsen the overall code health of the system.

### Resolving Conflict

In any conflict on a code review, the first step should always be for the
developer and reviewer to try to come to consensus, based on the contents of
this document and the other documents in [The MR Author's Guide](author-guide.md)
and this [Reviewer Guide](reviewer-guide.md).

When coming to consensus becomes especially difficult, it can help to have a
face-to-face meeting or a VC between the reviewer and the author, instead of
just trying to resolve the conflict through code review comments. (If you do
this, though, make sure to record the results of the discussion in a comment on
the MR, for future readers.)

If that doesn't resolve the situation, the most common way to resolve it would
be to escalate. Often the escalation path is to a broader team discussion, 
having a TL weigh in, asking for a decision from a maintainer of the code, 
or asking an member of "Center of excellence" to help out.
**Don't let a MR sit around because the author and the reviewer can't come
to an agreement.**

## What to look for in a code review

### Functionality

Does this MR do what the developer intended? Is what the developer intended good
for the users of this code? The "users" are usually both end-users (when they
are affected by the change) and developers (who will have to "use" this code in
the future).

Mostly, we expect developers to test MRs well-enough that they work correctly by
the time they get to code review. However, as the reviewer you should still be
thinking about edge cases, trying to think like a user, and making sure that 
there are no bugs that you see just by reading the code.

You *can* validate the MR if you want—the time when it's most important for a
reviewer to check a MR's behavior is when it has a user-facing impact, such as a
**UI change**. It's hard to understand how some changes will impact a user when
you're just reading the code. For changes like that, you can have the developer
give you a demo of the functionality if it's too inconvenient to patch in the MR
and try it yourself.

### Complexity

Is the MR more complex than it should be? Check this at every level of the
MR—are individual lines too complex? Are functions too complex? Are classes too
complex? "Too complex" usually means **"can't be understood quickly by code
readers."** It can also mean **"developers are likely to introduce bugs when
they try to call or modify this code."**

A particular type of complexity is **over-engineering**, where developers have
made the code more generic than it needs to be, or added functionality that
isn't presently needed by the system. Reviewers should be especially vigilant
about over-engineering. Encourage developers to solve the problem they know
needs to be solved *now*, not the problem that the developer speculates *might*
need to be solved in the future. The future problem should be solved once it
arrives and you can see its actual shape and requirements in the physical
universe.

### Tests

Make sure that the tests in the MR are correct, sensible, and useful. Tests do
not test themselves, and we don't write tests for our tests — a human must ensure
that tests are valid.

Will the tests actually fail when the code is broken? If the code changes
beneath them, will they start producing false positives? Does each test make
simple and useful assertions? Are the tests separated appropriately between
different test methods?

Remember that tests are also code that has to be maintained. Don't accept
complexity in tests just because they aren't part of the main binary.

## Comments

Did the developer write clear comments in understandable English? Are all of the
comments actually necessary? Usually comments are useful when they **explain
why** some code exists, and should not be explaining *what* some code is doing.
If the code isn't clear enough to explain itself, then the code should be made
simpler. There are some exceptions (regular expressions and complex algorithms
often benefit greatly from comments that explain what they're doing, for
example) but mostly comments are for information that the code itself can't
possibly contain, like the reasoning behind a decision.

It can also be helpful to look at comments that were there before this MR. Maybe
there is a TODO that can be removed now, a comment advising against this change
being made, etc.

Note that comments are different from *documentation* of classes, modules, or
functions, which should instead express the purpose of a piece of code, how it
should be used, and how it behaves when used.

## Speed of Code Reviews

### How Fast Should Code Reviews Be?

If you are not in the middle of a focused task, **you should do a code review
shortly after it comes in.**

**One business day is the maximum time it should take to respond** to a code
review request (i.e. first thing the next morning).

Following these guidelines means that a typical MR should get multiple rounds of
review (if needed) within a single day.

### Speed vs. Interruption

There is one time where the consideration of personal velocity trumps team
velocity. **If you are in the middle of a focused task, such as writing code,
don't interrupt yourself to do a code review.** Research has shown that it can
take a long time for a developer to get back into a smooth flow of development
after being interrupted. So interrupting yourself while coding is actually
_more_ expensive to the team than making another developer wait a bit for a code
review.

Instead, wait for a break point in your work before you respond to a request for
review. This could be when your current coding task is completed, after lunch,
returning from a meeting, coming back from the microkitchen, etc.

### Emergencies

There are also [emergencies](emergencies.md) where MRs must pass through the
_whole_ review process very quickly, and where the quality guidelines would be
relaxed. However, please see [What Is An Emergency?](emergencies.md#what) for
a description of which situations actually qualify as emergencies and which
don't.