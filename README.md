# Excel as code

Excel is one of the most widely used software products in the entire
world.  Wordprocessors have *more* users to be sure, but, Excel is
*nothing* like a word processor. It is in reality a programming
language and database combined.

Not counting Excel users, there are only about 30 million
programmers. Estimates put the number of Excel users between 500m and
over 1 billion!

It is therefore, by far, the most used programming language on the
planet. It is easily 20 times more popular than the next contender.

Excels are running the core of a huge number of business functions
from budgeting, product management, customer accounts, and many many
other things besides.

The value of Excel is that it is presenting the data, with a set of
formulae that let you keep derived data up-to-date. This *inferred*
data provides sums and computations, sometimes simple, but sometimes
exquisitely complex.

And through this whole range of complexity, with half a billion users,
virtually nobody treats Excel *seriously* like a programming language.

How can this be? We have a programming language which is *essentially*
acting as a declarative database, and yet we don't do unit tests, we
don't keep track of changes, we collaborate it by sending it in them
mail and god-forbid we should doing any serious *linting* of what is
in the thing.

This is a really crazy situation.

The programmers and database managers will often look at this
situation in terror and tell excel-jockeys they need to get off excel
ASAP.

The excel-jockeys might look at the database nerds and IT geeks and
think that they must be off their rocker. Or maybe they even feel
ashamed but realise that there is no way they are going to be able to
do the their job properly by simply switching to using Oracle &
Python.

Of course anyone who has used Excel in anger realises *why* it is so
brilliant. Show me another declarative constraint based, data driven
inferrence language that I can teach to my grandmother and I'll eat my
hat!

People refuse to stop using Excel because it empowers them and they
simply don't want to be disempowered.

And right they are. The problem isn't Excel. The problem is that we
are treating Excel like its a word processor, and not what it is: a
programming language.

## The Programming Enlightement

In the dark ages of programming you had a source tree and you edited
files in some terrible text editor and then ran a compiler. Some time
later you'd have a binary that you'd run and see if it crashed. If
everything went well you might share the file on a file server with
your colleagues. They also changed it so you had to figure out how not
to break everything and paste their changes back into your source tree
(or vice versa).

This was clearly a disaster, leading to huge pain in getting the
source code merges to line up without failure.

Enter revision control.

People realised that there needed to be a system of checking files in
and out such that changes could be compared and collisions could be
avoided.

And never did the person have to leave programming in their favourite
editor. Nobody told them to store their code in Oracle. Nobody said
they should share their source code in Google Docs.

This enabled vast improvements in collaboration. Fearless editing of
files created a much more open development environment. You could go
ahead and make that change you knew had to cut across half of the code
because you could figure out how to merge it when the time came. The
number of programmers you could have working on a code base with much
lower communication overhead increased tremendously.

The revision control system enabled a completely new approach to
software development: Continuous Integration / Continuous Deployment
(CI/CD). CI/CD meant that when code was checked in, a series of hooks
that ran unit tests could be run. Linters could be run over the
checked in version. You could even have complex integration tests
running which checked if the software still worked properly with other
processes.

All of these checks meant that the *health* of the code could be known
up to the minute. It was still possible to introduce breaking changes
by messing something up in a clever way, but a *huge class of errors*
was removed.

## How Excel can join the Rennaisance

Unfortunately, none of this applies to Excel because Excel doesn't
work well with revision control.

Why?

Because Excel is not a source file. It is a database coupled with
code. Git was not built for this - it knows about lines in a file and
thats it. Good luck trying to use git to resolve merge conflicts - it
will simply butcher your file.

The path to enlightement is a more sophisticated revision control
systems - ones that can understand Excel.

Luckily such a thing does actually exist,
[VersionXL](https://versionxl.com).

## Collaboration

The first benefit to this new approach to putting Excel in version
control will be enabling collaboration. Sure you can send Excel files
to people, but this is the equivalent of me e-mailing my colleague my
source tree every time I want to make a change.

And if I share it with two people at once, I'm sure to end up with two
different changes. And now I must figure out how to incorporate
both. I've turned myself into a fault-prone (and probably very
expensive) revision control system. And if I make a mistake I'll be
digging through my e-mail looking for the one I sent to the first
person in order to merge the correct changes back in again.

Out of the traps we are winning whenever there is a collaboration -
even between two people. We get to merge with less hassle, and any
mistake is just a rollback.

And at no point did we have to leave Excel.

## CI/CD for Excel

Now that we have a revision control system for Excel, we can start to
think seriously about CI/CD and what it would mean to really treat
Excel as code in a modern development environment.

First off is *linting*. Linting just means writing queries or scripts
which can look for obvious syntactic bugs. The value of this can not
be overstated. The number of stupid and obvious syntactic bugs (such
as mispellings) that even incredibly intelligent programers make is
huge. And the value of noticing that even larger.

What would Excel linting look like? It could be as simple as saying:

> All currency values in this file should be in dollars

Or maybe it says:

> Cells in column C must be numeric.

But it could be that specific files would require custom and complex
linting. That's fine, that happens with code too! You should be able
to simply at it as a test hook on commit. Once you get the green
light, you know that it's safe to merge.

In large corporations or organisations its often the case that you'll
even want aspects of the layout, the number of sheets etc. to remain
uniform even after updates. Linting can enable this to happen.

Of course linting doesn't catch more complex semantic errors. For that
we often want to write down what we *expect* some formula to do. And
to test that we should have a test case for our formula. This is unit
testing.

Unit testing excel might mean ensuring certain formulae meet a set of
external assertions that ensure that they still "do the right thing".

The value of having these external verifications might not seem
obvious when you're calculating a total, but if the calculation is
very complex you probably want to have a few test cases (which might
not necessarily be in your workbook) to sanity test.

And the more important the *value* of the calculations, the more
sanity should prevail.

## Conclusion

Excel *is* a programming language. It's time we start treating it like
one. Excel users want to keep using the power of their favourite
language.

They don't need to change that.

What needs to change is the idea that they are not programmers, so
they can join us in using modern software practices.
