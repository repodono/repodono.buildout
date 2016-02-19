Contributing to repodono
========================

Contributions to the repodono project is welcomed, provided that the
resulting code is owned by you and is licensed under GPLv2 or later.

Guidelines overview
-------------------

To aid in collaborative development and future debugging needs, all code
checked in must comply to a base guideline.  The following are the core
guidelines in brief:

- Guidelines be pragmatic rather than dogmatic.
- Aim for 100% test coverage during development; tests are counted.
- Require 100% test coverage on release (ideally on master also).
- PEP8 compliance (use flake8 supplied with build scripts).
- Commit messages must follow the 50/72 format.

Testing and Coverage
--------------------

The repodono project aims to minimize bugs, and one way to achieve this
is to ensure that all code committed must have asscoiated tests, so for
this the project loosely follows the principles introduced by Test
Driven Development (TTD).  This is examplified by tests covering all
aspects of all the code within the project.

However, pure TDD is not used, as the hard requirement that tests are
written before any code are rather rigid for prototyping up new
features, but they must be written later and all logic be tested with
output/side-effects checked by unit tests, and ideally with integration
tests to cover up everything.

For bug fixes, tests must be written first to demonstrate the failure
case to document what went wrong and most of all enable reproduction so
others can see what went wrong.  Fixes can be written, run against all
existing tests to ensure that the fix doesn't break existing features,
and then committed.  This leads into commits and discipline of this art.

Committing code
---------------

This is where rules become a bit more firm, and I generally require that
all contributions follow this to ensure everything run smoothly into the
future.

Commits be atomic

  That is, the change at hand should be able to stand on its own, yet
  without being clobbered with unrelated changes.  This aids with
  debugging especially using ``git bisect`` as bugs can easily be
  narrowed down into a small handful of lines rather than a couple
  thousand lines.  This means no sqashing of dozens of commits down into
  one (resulting in a giant blob that is very hard to read or understand
  or figure out how the author got there), but squashing of test fix
  commit down to its associated test failure commit can be done.

Commit messages must follow the 50/72 format.

  This means having a maximum of 50 characters for the first line of the
  commit, allowing the oneline log filter to easily show what happened.
  
  This is then followed by two newline characters, to leave a gap for
  where the descriptive message will go, which will document in detail
  what was changed within the commit (ideally in point form) and each
  line must not exceed 72 characters in length.  This policy is in-line
  with the Linux kernel commit style, and allows a very consistent way
  to read commits.

Split up code rearrangement, formatting, file moving from changes

  This means **no changing code** if the commit is meant to correct
  formatting, renaming or moving files, or moving segments of code out
  from one file to another.  This really means no sneaking in changes
  as this can introduce bugs.  Of course, this means that references
  that broke should be amended (such as imports) to ensure tests
  continue to pass.

No force push to master

  Except to undo really problematic issues, such as purging commits that
  are malicious in nature.

Avoid merges

  Use ``git rebase`` instead.  New commits from feature/bugfix branches
  *on top* of master can better show code evolution and aid in using
  ``git bisect`` when necesary.

Feature branches are friend

  Do developments on feature branches, rebase onto master whenever
  necessary to keep track of latest development.  Feature branches by
  nature belongs to the owner(s) and they can force push them whenever
  they can, as all changes to master are rebased on top of it.

  Before rebasing feature branches onto master, ensure they are properly
  covered by tests.

Commits do not fail tests

  New commits shouldn't break existing tests, especially on master.
  Ideally, when rebasing feature branches back onto master, run tests
  on each commit as the rebasing happens and correct any test failures
  and amend the associated commit.  This can be done easily with rebase
  by doing something like ``git rebase -i master --exec bin/test``,
  which will show that after each rebase the command to run the tests
  are done, and if all the tests passes on all commits then the rebase
  is completed and good.  This will aid with future debugging.
