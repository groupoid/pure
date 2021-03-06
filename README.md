PTS: Pure Type System for Erlang
-------------------------------

[![Build Status](https://travis-ci.org/groupoid/pure.svg?branch=master)](https://travis-ci.org/groupoid/pure)

An intermediate Om language is based on Henk languages described first
by Erik Meijer and Simon Peyton Jones in 1997. Later on in 2015 a new implementation of the ideas
in Haskell appeared, called Morte. It used Boehm-Berarducci encoding of recursive data types into non-recursive terms.
Morte has constants, variables, and kinds, is based only on *pi*, *lambda* and *apply* constructions,
one axiom and four deduction rules. The Om language resembles Henk and Morte both in design
and in implementation. This language indended to be small, concise, easily provable, clean and be able
to produce verifiable programs that can be distributed over the networks and compiled at target with
safe linkage.


```
$ curl -fsSL https://raw.github.com/synrc/mad/master/mad > mad
$ chmod +x mad"
$ ./mad dep com pla bun om

```

The PTS Systax is the following:

```
   <> ::= #option

    I ::= #identifier

    U ::= * < #number >

    O ::= U | I | ( O ) | O O
            | λ ( I : O ) → O
            | ∀ ( I : O ) → O
```

OM is an implementation of PTS with Infinite Number of Universes,
the pure lambda calculus with dependent types. It can be compiled (code extraction) to bytecode
of Erlang virtual machines BEAM and LING.

Trusted PTS with Infinite Universes
-----------------------------------

In repository OM you may found following parts of core:

* [Parser](https://github.com/groupoid/om/blob/master/src/om_parse.erl)
* [Typechecker](https://github.com/groupoid/om/blob/master/src/om_type.erl)
* [Eraser](https://github.com/groupoid/om/blob/master/src/om_erase.erl)
* [Code Extractor](https://github.com/groupoid/om/blob/master/src/om_extract.erl)

PTS ships with different "modes" (spaces of types with own encodings), or "preludes", which
you may find in `priv` directory. They are selectable with `om:mode("normal")`.

#### [normal](https://github.com/groupoid/om/tree/master/priv/normal)

This is a minimal practical prelude similar to Morte's base library of Gabriel Gonzalez.
It contains common inductive constructions encoded using plain Church (or Boehm-Berarducci if you wish) encoding,
and two basic (co)monadic effect systems: IO (free monad, for finite I/O) and IOI (free comonad,
for infinitary I/O, long-term processes). The generated code is being sewed with
Erlang effects that are passed as parameters to pure functions.

Note: all these folders (modules) are encoded in plain CoC in OM repository to demonstrate
you the basic principles how things work. Later all these should be written in EXE
languages and translated to OM automatically. You may think of OM as the low-level
typed assembler of type theory.

Credits
-------

* Maxim Sokhatsky

OM A HUM
