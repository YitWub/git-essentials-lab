# Run guide

How to run the library demo from this repository.

## Prerequisites

- **JDK 17 or later.** Both `java` and `javac` must be on your PATH.
- **Python 3.9 or later.** The runner uses only the standard library.
- No Maven, Gradle, or third-party Java dependency is needed.

Check your tools:

```text
java -version
javac -version
python3 --version
```

On Windows, use `py -3` in place of `python3`.

## Run the demo

From the repository root:

```text
python3 run.py demo
```

## What the demo does

The runner compiles every Java source under `src/library/` into a temporary
directory, then runs `library.Main`. The temporary directory is removed
afterwards, so no `.class` files are left in the repository.

`Main` builds a small library scenario in memory: a catalog of three books, a
student member and a faculty member, and a clock fixed to 2026-09-01 so the
output is reproducible. It then prints the borrowing limits, searches the
catalog, borrows a book, prints the loan receipt and due date, returns the book,
and reports the overdue fee and the remaining active loans.

Expected output:

```text
Library loan demo (fixed date: 2026-09-01)
Student limit: 2
Faculty limit: 2
Search for 'git': []
Loan: Git Essentials
Borrowed by: Alex; due: 2026-09-15
Return fee: 0
Active loans after return: 0
```

The search line is empty because the catalog matches titles case-sensitively:
the query `git` does not match the title `Git Essentials`.

## Running the tests

The same runner executes the test suite:

```text
python3 run.py test
```