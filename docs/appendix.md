# A Brief Diatribe

Every programming language, every build system, every compiler, web server, database and email client seem to gravitate towards adding infinite features and complexity so that their users can do ever more and more.

This is contrary to the UNIX philosophy: tools should do one thing and —by being tight and focused— do it damn well. If they are composable and flexible then they can be combined, piped and leveraged into a larger, more capable toolbox. The Internet is built with this toolbox.

Nowadays every programming language reimplements the same set of libraries and tools because using a well-maintained, mature and portable library that lives higher up the stack adds too much complexity. This extends the adolescence of new languages, results in no single language even becoming truly state of the art and leads to degrees of duplication that make the open source ecosystem fragile. This is to the detriment of all software, everywhere.

tea removes this complexity and adds some much needed robustness for the good of the entire open source ecosystem, the larger Internet and the whole world of software.


# What is tea?

tea is not a package manager.

*tea is unified packaging infrastructure*.

From the creator of [`brew`], tea is a standalone, binary download for all
platforms that puts the entire open
source ecosystem at your fingertips. Casually and effortlessly use the latest
and greatest or the oldest and most mature from any layer of any stack. Break
down the silos between programming communities, throw together scripts that
use entirely separate tools and languages and share them with the world with
a simple one-liner.

All you need is `tea`.

> tea is pre v1. This means there may still be some rough edges in day to day use.
> It also means that you should absolutely get involved. This is the key and
> golden time when getting involved is both easy and hugely fun. We look
> forward to meeting you 👊


# Our Goals

- To create incredible tooling: the base of every developer’s stack.
- To cater to our users, not ourselves.
- To take open source to the next level by funding the unpaid maintainers who thanklessly create the stack that powers the Internet.


# Philosophy

* Be non‑intrusive
    > don’t interfere with our users’ systems or habits
* Be “just works”
    > our users have better things to do than fix us
* Error messages must be excellent
    > trust that if it comes to it, our users can fix things provided we give
    > them a helping hand
* Be intuitive
    > being clever is good—but don’t be so clever nobody gets it
* Resist complexity
    > rethink the problem until a simpler solution emerges
* Be fast
    > we are in the way of our users’ real work, don’t make them wait


[`brew`]: https://brew.sh
