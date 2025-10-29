+++
title = "The worlds in which cryptography may or may not exist"
date = 2025-09-16T00:00:00Z
summary = "Impagliazzo's five possible worlds of computation and how each one affects the future of cryptography."
author = "Dean Malan"
author_social = "https://deanmalan.com"
original_url = "https://www.deanmalan.co.za/2025/2025-09-16-cryptography-worlds.html"
math = true
+++

If you're a programmer of any sort, chances are you have heard of the $\mathsf{P}$ vs $\mathsf{NP}$ problem many times before. However, have you ever heard of Impagliazzo's Five Worlds?

$\mathsf{P}$ vs $\mathsf{NP}$ asks whether the set of problems that can be _verified_ quickly can also be _solved_ quickly. You may also use the mental shortcut of asking whether "difficult" problems can be solved "easily", although it is not quite correct since there are other complexity classes that are even harder than $\mathsf{NP}$. That said, we will be using the "easy" instead of $\mathsf{P}$ and "hard" or "difficult" instead of $\mathsf{NP}$ a lot in this post.

What are Impagliazzo's Five Worlds? In 1995, Russell Impagliazzo [defined](https://ieeexplore.ieee.org/document/514853) five different "worlds" or scenarios in which cryptography may or may not exist. But wait a second, shouldn't there only be two worlds? One in which $\mathsf{P} = \mathsf{NP}$ and cryptography doesn't exist, and another in which $\mathsf{P} \neq \mathsf{NP}$ and cryptography _does_ exist?

It might be intuitive to think that if $\mathsf{P} \neq \mathsf{NP}$, then cryptography would exist. Intuitively, encryption is a $\mathsf{P}$-problem and decryption an $\mathsf{NP}$-problem, right? Well... that _is_ actually correct, but the challenge lies in _generating_ those encryptions that are $\mathsf{NP}$-difficult to decrypt.

Even if $\mathsf{NP}$-problems exist, we might not be able to generate new instances of those problems easily. In fact, this is true for the creation of Sudoku and crosswords puzzles. In order to create a new puzzle, we need to do a lot of checks and balances to ensure that it will be solvable. Believe me, I tried to create my own Sudoku puzzles as a bored kid in school and I was not able to create one that actually worked.

However, for the prime factorisation problem - which is used in many cryptographic protocols today - it is _easy_ to generate a new instance. We simply multiply any two random (large) primes.

## The five worlds

Let's see what five worlds Impagliazzo defined:

### Algorithmica

In **Algorithmica**, we have the scenario where $\mathsf{P} = \mathsf{NP}$. Most researchers believe this world is very unlikely to be true since we have many examples of $\mathsf{NP}$ problems for which no one has been able to find an efficient algorithm. In fact, it seems quite absurd that anyone might be able to solve a Sudoku puzzle, for example, in just a few steps. In Algorithmica, we obviously _won't_ have cryptography. Anyone will be able to decrypt any information they find.

### Heuristica

**Heuristica** is the world in which $\mathsf{P} \neq \mathsf{NP}$ and problems in $\mathsf{NP}$ are hard to solve in the worst case, but easy on average. Wait, what? Recall that complexity classes like $\mathsf{P}$ and $\mathsf{NP}$ consider the asymptotic complexity for **all instances** of the problem. In other words, a problem might be easy to solve in most cases, but if there are **any** instances for which it is hard, then the problem is in $\mathsf{NP}$.

In Heuristica, cryptography still isn't possible. Even though hard $\mathsf{NP}$-problems would exist, we wouldn't be able to find them easily and thus we wouldn't be able confidently create encryptions which we know will be difficult to decrypt.

### Pessiland

In the next world, called **Pessiland**, cryptography _still_ does not exist 😔. As you can infer from its name, this is Impagliazzo's least favourite world. In Pessiland, there are hard average-case $\mathsf{NP}$ problems, but one-way functions do not exist.

"What are one-way functions?", you ask. One-way functions (OWFs) are functions that are functions that are easy to compute, but hard to invert. One-way functions are the bedrock of modern cryptography. Every time we encrypt anything, a one-way function is used to compute the ciphertext (the encrypted text). Since the ciphertext is the output of a one-way function, it is hard for an adversary to invert (i.e. to decrypt and to read what we encrypted!).

If one-way functions do not exist, there would be no way for us to generate these _solved_ (in this case, encrypted) instances of $\mathsf{NP}$-problems.

### Minicrypt

In the fourth world, **Minicrypt**, cryptography finally _does_ exist - albeit only private-key cryptography (hence the "mini"). If you haven't heard of private-key and public-key cryptography before, don't worry too much about it for now. Just know while that _some_ cryptography would be possible in Minicrypt, many of the protocols we rely on today for communicating on the internet won't exist.

### Cryptomania

In the last world, **Cryptomania** 👾, cryptography in all its forms exists. As you can see, Impagliazzo was very excited about is world. It is this world in which we currently think (or at least pretend) we live in. All of modern cryptography in practice is based on the hope that we do actually live in Cryptomania.

What is the difference in the technical assumptions necessary for Cryptomania that does not exist in Minicrypt? Well, I'm glad you asked (or even if you didn't), because I'd like to tell you about my favourite type of function: **trapdoor one-way functions** 🚪. Honestly, what a cool name for a mathematical construct? And it does what it says in the name. Trapdoor OWFs are the same as one-way functions in that they are easy to compute and hard to invert, but they are also _easy to invert_ if and only if you have some secret "trapdoor" information.

Trapdoor OWFs makes public-key cryptography possible. I still remember the uncomfortable feeling of sending my SSH public key to my boss at one of my first internships and wondering how it could be that my public key won't reveal anything about my private key. Your private keys are your trapdoor secrets. When you decrypt something encrypted with your public key, you "open" the trapdoor!

## The new contender: Microcrypt

Impagliazzo theorised that his Five Worlds were the only five possibilities. However, in the last few years, more research in quantum computing has opened up the possibility of a sixth world, **Microcrypt**. I won't go into much details here, but [this Quanta Magazine](https://www.quantamagazine.org/cryptographers-discover-a-new-foundation-for-quantum-secrecy-20240603/) article explains the lead-up to this discovery.

Essentially, researchers have been working on basing quantum cryptography on mathematical constructs that are "weaker" than one-way functions. Dakshita Khurana and Kabir Tomer succesfully [proved](https://arxiv.org/abs/2409.15248) in 2024 that if certain assumptions about the relative advantage of quantum computers versus classical computers are true, quantum cryptography can exist if a new construct called **one-way puzzles** exist (even if one-way functions do not).

## Further reading

Impagliazzo's original 1995 [paper](https://ieeexplore.ieee.org/document/514853) is a surprisingly accessible read and the slightly janky, old-school formatting is endearing.

If you prefer something more modern, [this article](https://www.quantamagazine.org/which-computational-universe-do-we-live-in-20220418/) by Quanta Magazine is what originally got me interested in the topic. (Also, please [observe](https://www.quantamagazine.org/the-researcher-who-explores-computation-by-conjuring-new-worlds-20240327/) the schmodel photos of Impagliazzo on Quanta. I love that Quanta Magazine makes mathematicians look glamorous 💅).
