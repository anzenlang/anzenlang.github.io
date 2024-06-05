---
layout: page
title: Lean 4 training
permalink: /training/
subtitle: # <a href='#'>Affiliations</a>. Address. Contacts. Moto. Etc.
---



# Lean 4?

[Lean 4][lean] is a relatively new language that has been growing rapidly during the last two years.
Originally developed as a confidential project by Leonardo de Moura at Microsoft Research, Leonardo
is now part of Amazon Web Services (AWS) and Lean 4 now has a fairly large community and its own
foundation: the [Lean FRO][fro] (For Research Organization).

Lean 4 rides the current trend towards *safer* languages, *i.e.* languages able to provide strong
guarantees **at compile-time**. The most recent and successful example of this trend is the [Rust
language][rust]: a systems language that guarantees memory-/thread-safety thanks to a very strong
type system.

Lean 4 goes way beyond Rust in terms of static safety however. Its type system is based on the
[*Calculus of Inductive Constructions*][cic] (CIC), which is (almost) the same foundation that the
[Coq] *Interactive Theorem Prover* (ITP) is built on. This means that Lean's type system is strong
enough to express and reason about *regular* programs, but also pretty much any theorem/proof you
can find in the field of logics. This includes **proofs about programs**, meaning you can express
and verify any property you want about your programs, *though this requires a lot of expertise*.

Unlike traditional ITPs such as Coq however, Lean is also a slick, modern, ergonomic and extremely
powerful programming language. This makes it easier to prove your programs correct since you these
programs are written in the same *world* (the Lean world) used to prove they are correct. The proofs
are also a lot more trustworthy as there is no need to discuss the encoding of, say, the `C`
language in, say, Coq to trust that the Coq proof of the `C` program actually says anything about
the program.

As a simple example of Lean's capabilities consider *arrays*. Accessing the element at some index
`i` in an array `a` might not be legal if `a` does not contain at least `i` elements. If the access
is not legal, then we might read/write outside `a` which is **bad**. We can solve this problem by
always checking `i` is a legal index (as in Java for instance), but this means paying a price at
runtime. We can also use the iterator pattern *à la* Rust, which is a nice solution but can be
limiting for complex array manipulations.

In Lean, accessing the `a[i]` requires a *proof* that `i` is a legal index. This proof is usually
very easy to produce and guarantees, *at compile-time*, that the access is legal. It can thus be
compiled to a runtime-check-free array access which is both optimal and completely safe.

This example also highlights one of the many aspects of Lean that display its concern for
performance. Lean compiles to `C` and has a *very* minimal runtime ([see here (PDF)][beans]). There
are too many efficiency-related mechanisms to discuss here, but depending on the kind of programs
you write Lean tends to approach `C`/`C++`-levels of efficiency, even surpassing these languages
sometimes. This is because, as Rust has already shown, a compiler that knows more about your
programs can optimize them much, much more aggressively without sacrificing safety.



# Training Program

We propose a 3-day training program that presents Lean from basics to relatively advanced concepts.
The program does **not** turn participants into Lean experts, instead it gives a solid foundation
to approach existing code and start writing original projects.

This training program is focused on the software-development aspects of Lean. The ITP pure-logics
facets of Lean are extremely deep and complex, and the program only covers them as they naturally
appear in a *"normal"* software development setting.



## Details

The training program is structured around a project so that the various topics are discussed in a
tangible context, as opposed to relying on small standalone code snippets.

Participants write (most of) the project themselves as the concepts are introduced gradually. That
is, concepts are used by participants during or immediately after their introduction.

It is difficult to gauge how fast/slow a group of participants can digest the program. We account
for this impredictability by ending the program with a *"code what you want"* session --- though we
do provide project suggestions with solution. This session is fully supervised and is a good
opportunity for participants to dive deeper into aspects of Lean they want to explore while still
having access to the trainer for guidance.

Importantly, the final free session gives some flexibility as it can last from half a day to a full
day depending on how fast participants assimilate the rest of the program.

### First day

- Lean project layout, comments, file `import`s, `namespace` basics;
- *query commands* (`#check`, `#eval`, ...), more `namespace`s;
- basics of function `def`initions;
- structures and inductive types, even more `namespace`s;
- type parameters, (auto-)implicit parameters, type universes 🙀.

### Second day

- proof basics: `Prop`;
- type-`class`es;
- monads for developers;
- pushing the running project further.

### Third day

- anything remaining from the previous days;
- open discussion;
- *"code what you want"* with supervision and some recommended projects (with solutions).



[lean]: https://lean-lang.org
[fro]: https://lean-fro.org
[rust]: https://www.rust-lang.org
[cic]: https://coq.inria.fr/doc/v8.9/refman/language/cic.html
[coq]: https://coq.inria.fr
[beans]: https://arxiv.org/pdf/1908.05647
