Joy0
----

This is a bit modified fork of a **Joy0** by **Manfred von Thun**
that [**Ruurd Wiersma**](https://wodan58.github.io) had.
I am going to change it in a way to allow compiling it with no problems
using latest compilers and maybe minor ergonomic changes.
No changes beyound just making it work, pretty-printing and bugfixes if
bugs will be found (and hoepfully **no major changes in 'behaviour'**)

Changes
-------

Some system header files have been added. Functions declarations have been
ANSIfied, allowing compilation with all warnings turned on.

The return value of newnode needs to be captured in a variable.
This introduces a sequence point, preventing unspecified behaviour.
TRACING was used to locate the problem, so it was kept in the source code.
CORRECT\_GARBAGE\_COLLECTOR prints a runtime error in case of memory overflow.

Warning
-------

The source code assumes that sizeof(long) == sizeof(void *).

Build
-----

    make

Test
----

    cd test2
    for i in *.joy
    do
        ../joy $i >$i.out
    done
    grep -l false *.out
