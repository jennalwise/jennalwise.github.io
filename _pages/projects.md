---
layout: page
title: projects
permalink: /projects/
description: #A growing collection of your cool projects.
nav: false
#display_categories: [work, fun]
#horizontal: false
toc:
  sidebar: left
---

**My main line of work is on *gradual verification***, which smoothly and seamlessly combines static (compile time) and dynamic (run time) verification techniques to support the incremental specification and verification of code. 

I make advancements in gradual verification by taking a holistic approach to research; that is, I explore new techniques, designs, and features using mathematical formalizations, theories, and proofs, user studies, and through engineering and building related tools. 

So, I am current pursing the following research projects in gradual verification that span PL theory, SE (empirical SE and engineering tools), HCI, and CS education.

**Note,** I am open to pursing new projects in gradual verification, formal methods, programming languages, and software engineering. Email me to chat further.

### gradual verification for Rust
In this project we are building a gradual verifier for the Rust programming language. In doing so, we are exploring how gradual verification technology can leverage the static information in Rust's advanced type system and borrow checker to reduce run-time checking overhead related to ownership in gradual verification tools for imperative programs.
We are also exploring how gradual verification's reliance on run-time checking and related flexibility can assure unsafe Rust code. Finally, developing a gradual verifier for a fully fledged programming language provides us the opportunity to explore new theory and tackle new challenges related to gradually verifying new software types and properties, such as quantification, ghost code, concurrency, liveness, information flow, and so forth.

### proof synthesis and repair for gradual verifiers
While gradual verification makes developing specifications for verification easier, it does not eliminate the need to write them. A developer may need the strong guarantees of static verification in their software system, and must write enough specifications to achieve desired levels of static assurance. They may also need to write enough specifications to achieve a desired levels of run-time verification overhead. Once the developer writes their specifications, they may modify their code and then need to modify their existing specifications to follow suit. Following the promising work in proof synthesis and repair for proof assistants like Coq or Agda [[First et al. 2023](https://dl.acm.org/doi/abs/10.1145/3611643.3616243), [First et al. 2020](https://dl.acm.org/doi/abs/10.1145/3428299), [Yang and Deng 2019](https://proceedings.mlr.press/v97/yang19a.html), [Ringer 2021](https://www.proquest.com/openview/bcc06dabb4e7fce6b647c354d21d6f7c/1?pq-origsite=gscholar&cbl=18750&diss=y)], this project is exploring how machine learning and large language models can generate Hoare logic styled static specifications backed by gradual verification---i.e. *gradual proofs*---for both proof synthesis and repair tasks. This work shows promise as such specifications are close to code and can be gradually verified even if they are incomplete (partial). That is, just like developers, ML models and LLMs do not need to completely statically verify software to receive sound guarantees from gradual verification; they can stop when desired levels of static assurance are achieved.

This work is a joint collaboration with [Dr. Lin Tan](https://www.cs.purdue.edu/homes/lintan/) in CS @ Purdue.

### educational impact of gradual verification
Gradual verification's support for incremental verification should have a positive influence on student learning of specification techniques. Students can learn and receive feedback on individual constructs and ideas rather than learn and apply all the skills required for an inductive proof of correctness. For example, students can practice specifying and receive feedback on a list sortedness predicate without also having to learn and apply special logics, loop invariants, and inductive lemmas. Once the student has mastered the ideas individually, they can gradually integrate the ideas as they work towards a full proof. At any point in the process, students can check their understanding with meaningful verification feedback from the tool. In [my thesis work](https://jennalwise.github.io/assets/pdf/jenna_divincenzo_doctoral_dissertation.pdf), I found that static and dynamic reporting from gradual verification exposed incorrectness (and misunderstandings) of specifications early in the verification process. The specifications and misunderstandings were corrected far earlier than they would have using conventional means. In this line of work, we explore how students and practitioners learn to statically verify programs and how gradual verification can aid in the learning process by employing both short-term user studies in the lab and long-term studies in the classroom. This project is also exploring novel visualizations and error messaging in gradual verification technology to improve learning.

### evaluating gradual verifiers' soundness and adherence to gradual properties
In our [POPL 2024](https://arxiv.org/abs/2311.07559) paper, we uncovered a soundness bug in our gradual verifier, called [Gradual C0](https://arxiv.org/abs/2210.02428), through formal proofs. The bug arose from intricate interactions between the static and dynamic verification systems, which treat predicates differently across the two systems (iso-recursively vs. equi-recursively). Further, while formal proofs of soundness and gradual properties for gradual verifiers give us confidence that their design is correct, there is a question of whether or not their implementation realizes this design correctly. In fact, while empirically evaluating Gradual C0's performance, Gradual C0 was used to verify thousands of partial specifications that are correct. From this, we found and fixed a number of bugs in Gradual C0 where its design was implemented incorrectly. Thus, this line of work is exploring formal, engineering, and/or empirical solutions that evaluate gradual verifiers' soundness and their adherence to gradual properties to improve confidence in such tools.

### gradual program analysis
Static analyzers burden users by requiring them to either work through an unwieldy number of false positives or to explicitly annotate every part of their code. Fortunately, using the ideas from gradual verification, one can build a *gradual analysis* that 1) soundly supports missing annotations and 2) reduces false positives reported by a static analyzer in exchange for run-time overhead.
Rather than conservatively marking the code as buggy when the static analysis is imprecise, a run-time check is instead injected for the property.
In prior work, we developed the formalization, meta-theory, and implementation of a gradual null-pointer analysis. We also found preliminary evidence that our gradual null-pointer analysis reduces false positives compared to state-of-the-art checkers in the Infer static analyzer [[ECOOP 2021](https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.ECOOP.2021.3)].

We are developing more gradual analyses in various domains to eventually culminate in a theory and practical framework for the development of gradual analyses broadly.