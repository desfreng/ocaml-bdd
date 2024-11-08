# ocaml-bdd

This is a simple implementation of a BDD library for OCaml,
mostly for teaching and quick experiment purposes.

## Build

You need `dune` on your system. If you don't have it, install `opam` then try `opam install dune`.

To build everything:

```sh
make
```

It will build these libraries:

- `bdd`: the main library - `lib/bdd.mli` should be self-explanatory
- `prop`: propositional logic, with a parser, used to test the main library - see `check` for example
- `bench_prop`: various ways of generating valid propositional formulae

Many executables:

- `test`: tests producing graphical output - you'll need the `graphviz` and `gv` packages from your distribution
- `tiling`
- `bdd_sat`: a propositional tautology checker using `bdd`
- `quant_elim`: simple tests for quantifier elimination
- `queen`: computes the number of solutions to the n-queens problem, using a propositional formula (this is not an efficient way to solve this problem, simply another way to test the `bdd` library)
- `path`
- `check`: a quick check
- `bench_prop_cli`: generate valid propositional formulae from command line

To run any of them, let's say `check`, do:

```sh
dune exec test/check.exe
```

You can combine some of them, e.g.:

```sh
dune exec test/bench_prop_cli.exe -- -pigeon-p 7 | dune exec test/bdd_sat.exe
```

You might need to set the environment variable `DUNE_CONFIG__GLOBAL_LOCK` to `disabled` to allow multiple dune instance running.

## Test

You can run tests using:

```sh
make test
```

## Install

```sh
make install
```
