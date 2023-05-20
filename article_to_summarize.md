Main menu

WikipediaThe Free Encyclopedia
Search Wikipedia
Create account
Log in

Personal tools
Contents hide
(Top)
Abstract examples
Toggle Abstract examples subsection
The Ali Baba cave
Two balls and the colour-blind friend
Definition
Practical examples
Toggle Practical examples subsection
Discrete log of a given value
Short summary
Hamiltonian cycle for a large graph
Completeness
Zero-knowledge
Soundness
Variants of zero-knowledge
Zero knowledge types
Applications
Toggle Applications subsection
Authentication systems
Ethical behavior
Nuclear disarmament
Blockchains
History
Zero-Knowledge Proof protocols
See also
References
Zero-knowledge proof

Article
Talk
Read
Edit
View history

Tools
From Wikipedia, the free encyclopedia
"ZKP" redirects here. For the airport in Russia, see Zyryanka Airport. For other uses, see Zero knowledge.
In cryptography, a zero-knowledge proof or zero-knowledge protocol is a method by which one party (the prover) can prove to another party (the verifier) that a given statement is true while the prover avoids conveying any additional information apart from the fact that the statement is indeed true. The essence of zero-knowledge proofs is that it is trivial to prove that one possesses knowledge of certain information by simply revealing it; the challenge is to prove such possession without revealing the information itself or any additional information.[1]

If proving a statement requires that the prover possess some secret information, then the verifier will not be able to prove the statement to anyone else without possessing the secret information. The statement being proved must include the assertion that the prover has such knowledge, but without including or transmitting the knowledge itself in the assertion. Otherwise, the statement would not be proved in zero-knowledge because it provides the verifier with additional information about the statement by the end of the protocol. A zero-knowledge proof of knowledge is a special case when the statement consists only of the fact that the prover possesses the secret information.

Interactive zero-knowledge proofs require interaction between the individual (or computer system) proving their knowledge and the individual validating the proof.[1]


This section needs to be updated. The reason given is: There are also Non-interactive zero-knowledge proofs. Please help update this article to reflect recent events or newly available information. (December 2022)
A protocol implementing zero-knowledge proofs of knowledge must necessarily require interactive input from the verifier. This interactive input is usually in the form of one or more challenges such that the responses from the prover will convince the verifier if and only if the statement is true, i.e., if the prover does possess the claimed knowledge. If this were not the case, the verifier could record the execution of the protocol and replay it to convince someone else that they possess the secret information. The new party's acceptance is either justified since the replayer does possess the information (which implies that the protocol leaked information, and thus, is not proved in zero-knowledge), or the acceptance is spurious, i.e., was accepted from someone who does not actually possess the information.

Some forms of non-interactive zero-knowledge proofs exist,[2][3] but the validity of the proof relies on computational assumptions (typically the assumptions of an ideal cryptographic hash function).

Abstract examples
The Ali Baba cave

Peggy randomly takes either path A or B, while Victor waits outside

Victor chooses an exit path

Peggy reliably appears at the exit Victor names
There is a well-known story presenting the fundamental ideas of zero-knowledge proofs, first published in 1990 by Jean-Jacques Quisquater and others in their paper "How to Explain Zero-Knowledge Protocols to Your Children".[4] Using the common Alice and Bob anthropomorphic thought experiment placeholders, the two parties in a zero-knowledge proof are Peggy as the prover of the statement, and Victor, the verifier of the statement.

In this story, Peggy has uncovered the secret word used to open a magic door in a cave. The cave is shaped like a ring, with the entrance on one side and the magic door blocking the opposite side. Victor wants to know whether Peggy knows the secret word; but Peggy, being a very private person, does not want to reveal her knowledge (the secret word) to Victor or to reveal the fact of her knowledge to the world in general.

They label the left and right paths from the entrance A and B. First, Victor waits outside the cave as Peggy goes in. Peggy takes either path A or B; Victor is not allowed to see which path she takes. Then, Victor enters the cave and shouts the name of the path he wants her to use to return, either A or B, chosen at random. Providing she really does know the magic word, this is easy: she opens the door, if necessary, and returns along the desired path.

However, suppose she did not know the word. Then, she would only be able to return by the named path if Victor were to give the name of the same path by which she had entered. Since Victor would choose A or B at random, she would have a 50% chance of guessing correctly. If they were to repeat this trick many times, say 20 times in a row, her chance of successfully anticipating all of Victor's requests would become very small (1 in 220, or very roughly 1 in a million).

Thus, if Peggy repeatedly appears at the exit Victor names, he can conclude that it is extremely probable that Peggy does, in fact, know the secret word.

One side note with respect to third-party observers: even if Victor is wearing a hidden camera that records the whole transaction, the only thing the camera will record is in one case Victor shouting "A!" and Peggy appearing at A or in the other case Victor shouting "B!" and Peggy appearing at B. A recording of this type would be trivial for any two people to fake (requiring only that Peggy and Victor agree beforehand on the sequence of A's and B's that Victor will shout). Such a recording will certainly never be convincing to anyone but the original participants. In fact, even a person who was present as an observer at the original experiment would be unconvinced, since Victor and Peggy might have orchestrated the whole "experiment" from start to finish.

Further notice that if Victor chooses his A's and B's by flipping a coin on-camera, this protocol loses its zero-knowledge property; the on-camera coin flip would probably be convincing to any person watching the recording later. Thus, although this does not reveal the secret word to Victor, it does make it possible for Victor to convince the world in general that Peggy has that knowledge—counter to Peggy's stated wishes. However, digital cryptography generally "flips coins" by relying on a pseudo-random number generator, which is akin to a coin with a fixed pattern of heads and tails known only to the coin's owner. If Victor's coin behaved this way, then again it would be possible for Victor and Peggy to have faked the "experiment", so using a pseudo-random number generator would not reveal Peggy's knowledge to the world in the same way that using a flipped coin would.

Notice that Peggy could prove to Victor that she knows the magic word, without revealing it to him, in a single trial. If both Victor and Peggy go together to the mouth of the cave, Victor can watch Peggy go in through A and come out through B. This would prove with certainty that Peggy knows the magic word, without revealing the magic word to Victor. However, such a proof could be observed by a third party, or recorded by Victor and such a proof would be convincing to anybody. In other words, Peggy could not refute such proof by claiming she colluded with Victor, and she is therefore no longer in control of who is aware of her knowledge.

Two balls and the colour-blind friend
Imagine your friend "Victor" is red-green colour-blind (while you are not) and you have two balls: one red and one green, but otherwise identical. To Victor, the balls seem completely identical. Victor is skeptical that the balls are actually distinguishable. You want to prove to Victor that the balls are in fact differently-coloured, but nothing else. In particular, you do not want to reveal which ball is the red one and which is the green.

Here is the proof system. You give the two balls to Victor and he puts them behind his back. Next, he takes one of the balls and brings it out from behind his back and displays it. He then places it behind his back again and then chooses to reveal just one of the two balls, picking one of the two at random with equal probability. He will ask you, "Did I switch the ball?" This whole procedure is then repeated as often as necessary.

By looking at the balls' colours, you can, of course, say with certainty whether or not he switched them. On the other hand, if the balls were the same colour and hence indistinguishable, there is no way you could guess correctly with probability higher than 50%.

Since the probability that you would have randomly succeeded at identifying each switch/non-switch is 50%, the probability of having randomly succeeded at all switch/non-switches approaches zero ("soundness"). If you and your friend repeat this "proof" multiple times (e.g. 20 times), your friend should become convinced ("completeness") that the balls are indeed differently coloured.

The above proof is zero-knowledge because your friend never learns which ball is green and which is red; indeed, he gains no knowledge about how to distinguish the balls.[5]

Definition

This section needs additional citations for verification. Please help improve this article by adding citations to reliable sources in this section. Unsourced material may be challenged and removed.
Find sources: "Zero-knowledge proof" – news · newspapers · books · scholar · JSTOR (July 2022) (Learn how and when to remove this template message)
A zero-knowledge proof of some statement must satisfy three properties:

Completeness: if the statement is true, an honest verifier (that is, one following the protocol properly) will be convinced of this fact by an honest prover.
Soundness: if the statement is false, no cheating prover can convince an honest verifier that it is true, except with some small probability.
Zero-knowledge: if the statement is true, no verifier learns anything other than the fact that the statement is true. In other words, just knowing the statement (not the secret) is sufficient to imagine a scenario showing that the prover knows the secret. This is formalized by showing that every verifier has some simulator that, given only the statement to be proved (and no access to the prover), can produce a transcript that "looks like" an interaction between an honest prover and the verifier in question.
The first two of these are properties of more general interactive proof systems. The third is what makes the proof zero-knowledge.[6]

Zero-knowledge proofs are not proofs in the mathematical sense of the term because there is some small probability, the soundness error, that a cheating prover will be able to convince the verifier of a false statement. In other words, zero-knowledge proofs are probabilistic "proofs" rather than deterministic proofs. However, there are techniques to decrease the soundness error to negligibly small values (e.g. guessing correctly on a hundred or thousand binary decisions has a 1 / 2^100 or 1/ 2^1000 soundness error, respectively. As the number of bits increases, soundness error decreases toward zero).

A formal definition of zero-knowledge has to use some computational model, the most common one being that of a Turing machine. Let
�
P,
�
V, and
�
S be Turing machines. An interactive proof system with
(
�
,
�
)
{\displaystyle (P,V)} for a language
�
L is zero-knowledge if for any probabilistic polynomial time (PPT) verifier
�
^{\hat {V}} there exists a PPT simulator
�
S such that

∀
�
∈
�
,
�
∈
{
0
,
1
}
∗
,
View
�
^
⁡
[
�
(
�
)
↔
�
^
(
�
,
�
)
]
=
�
(
�
,
�
)
{\displaystyle \forall x\in L,z\in \{0,1\}^{*},\operatorname {View} _{\hat {V}}\left[P(x)\leftrightarrow {\hat {V}}(x,z)\right]=S(x,z)}
where
View
�
^
⁡
[
�
(
�
)
↔
�
^
(
�
,
�
)
]
{\displaystyle \operatorname {View} _{\hat {V}}\left[P(x)\leftrightarrow {\hat {V}}(x,z)\right]} is a record of the interactions between
�
(
�
)
P(x) and
�
^
(
�
,
�
)
{\displaystyle {\hat {V}}(x,z)}. The prover
�
P is modeled as having unlimited computation power (in practice,
�
P usually is a probabilistic Turing machine). Intuitively, the definition states that an interactive proof system
(
�
,
�
)
{\displaystyle (P,V)} is zero-knowledge if for any verifier
�
^{\hat {V}} there exists an efficient simulator
�
S (depending on
�
^{\hat {V}}) that can reproduce the conversation between
�
P and
�
^{\hat {V}} on any given input. The auxiliary string
�
z in the definition plays the role of "prior knowledge" (including the random coins of
�
^{\hat {V}}). The definition implies that
�
^{\hat {V}} cannot use any prior knowledge string
�
z to mine information out of its conversation with
�
P, because if
�
S is also given this prior knowledge then it can reproduce the conversation between
�
^{\hat {V}} and
�
P just as before.[citation needed]

The definition given is that of perfect zero-knowledge. Computational zero-knowledge is obtained by requiring that the views of the verifier
�
^{\hat {V}} and the simulator are only computationally indistinguishable, given the auxiliary string.[citation needed]

Practical examples
Discrete log of a given value
We can apply these ideas to a more realistic cryptography application. Peggy wants to prove to Victor that she knows the discrete log of a given value in a given group.[7]

For example, given a value
�
y, a large prime
�
p and a generator
�
g, she wants to prove that she knows a value
�
x such that
�
�
mod
�
=
�
{\displaystyle g^{x}{\bmod {p}}=y}, without revealing
�
x. Indeed, knowledge of
�
x could be used as a proof of identity, in that Peggy could have such knowledge because she chose a random value
�
x that she didn't reveal to anyone, computed
�
=
�
�
mod
�
{\displaystyle y=g^{x}{\bmod {p}}} and distributed the value of
�
y to all potential verifiers, such that at a later time, proving knowledge of
�
x is equivalent to proving identity as Peggy.

The protocol proceeds as follows: in each round, Peggy generates a random number
�
r, computes
�
=
�
�
mod
�
{\displaystyle C=g^{r}{\bmod {p}}} and discloses this to Victor. After receiving
�
C, Victor randomly issues one of the following two requests: he either requests that Peggy discloses the value of
�
r, or the value of
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}}. With either answer, Peggy is only disclosing a random value, so no information is disclosed by a correct execution of one round of the protocol.

Victor can verify either answer; if he requested
�
r, he can then compute
�
�
mod
�
{\displaystyle g^{r}{\bmod {p}}} and verify that it matches
�
C. If he requested
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}}, he can verify that
�
C is consistent with this, by computing
�
(
�
+
�
)
mod
(
�
−
1
)
mod
�
{\displaystyle g^{(x+r){\bmod {(p-1)}}}{\bmod {p}}} and verifying that it matches
(
�
⋅
�
)
mod
�
{\displaystyle (C\cdot y){\bmod {p}}}. If Peggy indeed knows the value of
�
x, she can respond to either one of Victor's possible challenges.

If Peggy knew or could guess which challenge Victor is going to issue, then she could easily cheat and convince Victor that she knows
�
x when she does not: if she knows that Victor is going to request
�
r, then she proceeds normally: she picks
�
r, computes
�
=
�
�
mod
�
{\displaystyle C=g^{r}{\bmod {p}}} and discloses
�
C to Victor; she will be able to respond to Victor's challenge. On the other hand, if she knows that Victor will request
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}}, then she picks a random value
�
′
r', computes
�
′
=
�
�
′
⋅
(
�
�
)
−
1
mod
�
{\displaystyle C'=g^{r'}\cdot \left(g^{x}\right)^{-1}{\bmod {p}}}, and discloses
�
′
C' to Victor as the value of
�
C that he is expecting. When Victor challenges her to reveal
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}}, she reveals
�
′
r', for which Victor will verify consistency, since he will in turn compute
�
�
′
mod
�
{\displaystyle g^{r'}{\bmod {p}}}, which matches
�
′
⋅
�
C'\cdot y, since Peggy multiplied by the modular multiplicative inverse of
�
y.

However, if in either one of the above scenarios Victor issues a challenge other than the one she was expecting and for which she manufactured the result, then she will be unable to respond to the challenge under the assumption of infeasibility of solving the discrete log for this group. If she picked
�
r and disclosed
�
=
�
�
mod
�
{\displaystyle C=g^{r}{\bmod {p}}}, then she will be unable to produce a valid
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}} that would pass Victor's verification, given that she does not know
�
x. And if she picked a value
�
′
r' that poses as
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}}, then she would have to respond with the discrete log of the value that she disclosed – but Peggy does not know this discrete log, since the value C she disclosed was obtained through arithmetic with known values, and not by computing a power with a known exponent.

Thus, a cheating prover has a 0.5 probability of successfully cheating in one round. By executing a large enough number of rounds, the probability of a cheating prover succeeding can be made arbitrarily low.

Short summary
Peggy proves to know the value of x (for example her password).

Peggy and Victor agree on a prime
�
p and a generator
�
g of the multiplicative group of the field
�
�
{\displaystyle \mathbb {Z} _{p}}.
Peggy calculates the value
�
=
�
�
mod
�
{\displaystyle y=g^{x}{\bmod {p}}} and transfers the value to Victor.
The following two steps are repeated a (large) number of times.
Peggy repeatedly picks a random value
�
∈
�
[
0
,
�
−
2
]
{\displaystyle r\in U[0,p-2]} and calculates
�
=
�
�
mod
�
{\displaystyle C=g^{r}{\bmod {p}}}. She transfers the value
�
C  to Victor.
Victor asks Peggy to calculate and transfer either the value
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(p-1)}}} or the value
�
r. In the first case Victor verifies
(
�
⋅
�
)
mod
�
≡
�
(
�
+
�
)
mod
(
�
−
1
)
mod
�
{\displaystyle (C\cdot y){\bmod {p}}\equiv g^{(x+r){\bmod {(p-1)}}}{\bmod {p}}}. In the second case he verifies
�
≡
�
�
mod
�
{\displaystyle C\equiv g^{r}{\bmod {p}}}.
The value
(
�
+
�
)
mod
(
�
−
1
)
{\displaystyle (x+r){\bmod {(}}p-1)} can be seen as the encrypted value of
�
mod
(
�
−
1
)
{\displaystyle x{\bmod {(}}p-1)}. If
�
r is truly random, equally distributed between zero and
(
�
−
2
)
{\displaystyle (p-2)}, this does not leak any information about
�
x (see one-time pad).

Hamiltonian cycle for a large graph
The following scheme is due to Manuel Blum.[8]

In this scenario, Peggy knows a Hamiltonian cycle for a large graph G. Victor knows G but not the cycle (e.g., Peggy has generated G and revealed it to him.) Finding a Hamiltonian cycle given a large graph is believed to be computationally infeasible, since its corresponding decision version is known to be NP-complete. Peggy will prove that she knows the cycle without simply revealing it (perhaps Victor is interested in buying it but wants verification first, or maybe Peggy is the only one who knows this information and is proving her identity to Victor).

To show that Peggy knows this Hamiltonian cycle, she and Victor play several rounds of a game.

At the beginning of each round, Peggy creates H, a graph which is isomorphic to G (i.e. H is just like G except that all the vertices have different names). Since it is trivial to translate a Hamiltonian cycle between isomorphic graphs with known isomorphism, if Peggy knows a Hamiltonian cycle for G she also must know one for H.
Peggy commits to H. She could do so by using a cryptographic commitment scheme. Alternatively, she could number the vertices of H. Next, for each edge of H, on a small piece of paper, she writes down the two vertices that the edge joins. Then she puts all these pieces of paper face down on a table. The purpose of this commitment is that Peggy is not able to change H while, at the same time, Victor has no information about H.
Victor then randomly chooses one of two questions to ask Peggy. He can either ask her to show the isomorphism between H and G (see graph isomorphism problem), or he can ask her to show a Hamiltonian cycle in H.
If Peggy is asked to show that the two graphs are isomorphic, she first uncovers all of H (e.g. by turning over all pieces of papers that she put on the table) and then provides the vertex translations that map G to H. Victor can verify that they are indeed isomorphic.
If Peggy is asked to prove that she knows a Hamiltonian cycle in H, she translates her Hamiltonian cycle in G onto H and only uncovers the edges on the Hamiltonian cycle. This is enough for Victor to check that H does indeed contain a Hamiltonian cycle.
It is important that the commitment to the graph be such that Victor can verify, in the second case, that the cycle is really made of edges from H. This can be done by, for example, committing to every edge (or lack thereof) separately.

Completeness
If Peggy does know a Hamiltonian cycle in G, she can easily satisfy Victor's demand for either the graph isomorphism producing H from G (which she had committed to in the first step) or a Hamiltonian cycle in H (which she can construct by applying the isomorphism to the cycle in G).

Zero-knowledge
Peggy's answers do not reveal the original Hamiltonian cycle in G. Each round, Victor will learn only H's isomorphism to G or a Hamiltonian cycle in H. He would need both answers for a single H to discover the cycle in G, so the information remains unknown as long as Peggy can generate a distinct H every round. If Peggy does not know of a Hamiltonian cycle in G, but somehow knew in advance what Victor would ask to see each round then she could cheat. For example, if Peggy knew ahead of time that Victor would ask to see the Hamiltonian cycle in H then she could generate a Hamiltonian cycle for an unrelated graph. Similarly, if Peggy knew in advance that Victor would ask to see the isomorphism then she could simply generate an isomorphic graph H (in which she also does not know a Hamiltonian cycle). Victor could simulate the protocol by himself (without Peggy) because he knows what he will ask to see. Therefore, Victor gains no information about the Hamiltonian cycle in G from the information revealed in each round.

Soundness
If Peggy does not know the information, she can guess which question Victor will ask and generate either a graph isomorphic to G or a Hamiltonian cycle for an unrelated graph, but since she does not know a Hamiltonian cycle for G she cannot do both. With this guesswork, her chance of fooling Victor is 2−n, where n is the number of rounds. For all realistic purposes, it is infeasibly difficult to defeat a zero-knowledge proof with a reasonable number of rounds in this way.

Variants of zero-knowledge
Different variants of zero-knowledge can be defined by formalizing the intuitive concept of what is meant by the output of the simulator "looking like" the execution of the real proof protocol in the following ways:

We speak of perfect zero-knowledge if the distributions produced by the simulator and the proof protocol are distributed exactly the same. This is for instance the case in the first example above.
Statistical zero-knowledge[9] means that the distributions are not necessarily exactly the same, but they are statistically close, meaning that their statistical difference is a negligible function.
We speak of computational zero-knowledge if no efficient algorithm can distinguish the two distributions.
Zero knowledge types
Proof of knowledge: the knowledge is hidden in the exponent like in the example shown above.
Pairing based cryptography: given f(x) and f(y), without knowing x and y, it is possible to compute f(x×y).
Witness indistinguishable proof: verifiers cannot know which witness is used for producing the proof.
Multi-party computation: while each party can keep their respective secret, they together produce a result.
Ring signature: outsiders have no idea which key is used for signing.
Applications
Authentication systems
Research in zero-knowledge proofs has been motivated by authentication systems where one party wants to prove its identity to a second party via some secret information (such as a password) but doesn't want the second party to learn anything about this secret. This is called a "zero-knowledge proof of knowledge". However, a password is typically too small or insufficiently random to be used in many schemes for zero-knowledge proofs of knowledge. A zero-knowledge password proof is a special kind of zero-knowledge proof of knowledge that addresses the limited size of passwords.[citation needed]

In April 2015, the Sigma protocol (one-out-of-many proofs) was introduced.[10] In August 2021, Cloudflare, an American web infrastructure and security company decided to use the one-out-of-many proofs mechanism for private web verification using vendor hardware.[11]

Ethical behavior
One of the uses of zero-knowledge proofs within cryptographic protocols is to enforce honest behavior while maintaining privacy. Roughly, the idea is to force a user to prove, using a zero-knowledge proof, that its behavior is correct according to the protocol.[12][13] Because of soundness, we know that the user must really act honestly in order to be able to provide a valid proof. Because of zero knowledge, we know that the user does not compromise the privacy of its secrets in the process of providing the proof.[citation needed]

Nuclear disarmament
In 2016, the Princeton Plasma Physics Laboratory and Princeton University demonstrated a technique that may have applicability to future nuclear disarmament talks. It would allow inspectors to confirm whether or not an object is indeed a nuclear weapon without recording, sharing or revealing the internal workings which might be secret.[14]

Blockchains
Zero-knowledge proofs were applied in the Zerocoin and Zerocash protocols, which culminated in the birth of Zcoin[15] (later rebranded as Firo in 2020)[16] and Zcash cryptocurrencies in 2016. Zerocoin has a built-in mixing model that does not trust any peers or centralised mixing providers to ensure anonymity.[15] Users can transact in a base currency and can cycle the currency into and out of Zerocoins.[17] The Zerocash protocol uses a similar model (a variant known as a non-interactive zero-knowledge proof)[18] except that it can obscure the transaction amount, while Zerocoin cannot. Given significant restrictions of transaction data on the Zerocash network, Zerocash is less prone to privacy timing attacks when compared to Zerocoin. However, this additional layer of privacy can cause potentially undetected hyperinflation of Zerocash supply because fraudulent coins cannot be tracked.[15][19]

In 2018, Bulletproofs were introduced. Bulletproofs are an improvement from non-interactive zero-knowledge proof where trusted setup is not needed.[20] It was later implemented into the Mimblewimble protocol (which the Grin and Beam cryptocurrencies are based upon) and Monero cryptocurrency.[21] In 2019, Firo implemented the Sigma protocol, which is an improvement on the Zerocoin protocol without trusted setup.[22][10] In the same year, Firo introduced the Lelantus protocol, an improvement on the Sigma protocol, where the former hides the origin and amount of a transaction.[23]

History
Zero-knowledge proofs were first conceived in 1985 by Shafi Goldwasser, Silvio Micali, and Charles Rackoff in their paper "The Knowledge Complexity of Interactive Proof-Systems".[12] This paper introduced the IP hierarchy of interactive proof systems (see interactive proof system) and conceived the concept of knowledge complexity, a measurement of the amount of knowledge about the proof transferred from the prover to the verifier. They also gave the first zero-knowledge proof for a concrete problem, that of deciding quadratic nonresidues mod m. Together with a paper by László Babai and Shlomo Moran, this landmark paper invented interactive proof systems, for which all five authors won the first Gödel Prize in 1993.

In their own words, Goldwasser, Micali, and Rackoff say:

Of particular interest is the case where this additional knowledge is essentially 0 and we show that [it] is possible to interactively prove that a number is quadratic non residue mod m releasing 0 additional knowledge. This is surprising as no efficient algorithm for deciding quadratic residuosity mod m is known when m’s factorization is not given. Moreover, all known NP proofs for this problem exhibit the prime factorization of m. This indicates that adding interaction to the proving process, may decrease the amount of knowledge that must be communicated in order to prove a theorem.

The quadratic nonresidue problem has both an NP and a co-NP algorithm, and so lies in the intersection of NP and co-NP. This was also true of several other problems for which zero-knowledge proofs were subsequently discovered, such as an unpublished proof system by Oded Goldreich verifying that a two-prime modulus is not a Blum integer.[24]

Oded Goldreich, Silvio Micali, and Avi Wigderson took this one step further, showing that, assuming the existence of unbreakable encryption, one can create a zero-knowledge proof system for the NP-complete graph coloring problem with three colors. Since every problem in NP can be efficiently reduced to this problem, this means that, under this assumption, all problems in NP have zero-knowledge proofs.[25] The reason for the assumption is that, as in the above example, their protocols require encryption. A commonly cited sufficient condition for the existence of unbreakable encryption is the existence of one-way functions, but it is conceivable that some physical means might also achieve it.

On top of this, they also showed that the graph nonisomorphism problem, the complement of the graph isomorphism problem, has a zero-knowledge proof. This problem is in co-NP, but is not currently known to be in either NP or any practical class. More generally, Russell Impagliazzo and Moti Yung as well as Ben-Or et al. would go on to show that, also assuming one-way functions or unbreakable encryption, that there are zero-knowledge proofs for all problems in IP = PSPACE, or in other words, anything that can be proved by an interactive proof system can be proved with zero knowledge.[26][27]

Not liking to make unnecessary assumptions, many theorists sought a way to eliminate the necessity of one way functions. One way this was done was with multi-prover interactive proof systems (see interactive proof system), which have multiple independent provers instead of only one, allowing the verifier to "cross-examine" the provers in isolation to avoid being misled. It can be shown that, without any intractability assumptions, all languages in NP have zero-knowledge proofs in such a system.[28]

It turns out that in an Internet-like setting, where multiple protocols may be executed concurrently, building zero-knowledge proofs is more challenging. The line of research investigating concurrent zero-knowledge proofs was initiated by the work of Dwork, Naor, and Sahai.[29] One particular development along these lines has been the development of witness-indistinguishable proof protocols. The property of witness-indistinguishability is related to that of zero-knowledge, yet witness-indistinguishable protocols do not suffer from the same problems of concurrent execution.[30]

Another variant of zero-knowledge proofs are non-interactive zero-knowledge proofs. Blum, Feldman, and Micali showed that a common random string shared between the prover and the verifier is enough to achieve computational zero-knowledge without requiring interaction.[2][3]

Zero-Knowledge Proof protocols
The most popular interactive or non-interactive zero-knowledge proof (e.g., zk-SNARK) protocols can be broadly categorized in the following four categories: Succinct Non-Interactive ARguments of Knowledge (SNARK), Scalable Transparent ARgument of Knowledge (STARK), Verifiable Polynomial Delegation (VPD), and Succinct Non-interactive ARGuments (SNARG). A list of zero-knowledge proof protocols and libraries is provided below along with comparisons based on transparency, universality, plausible post-quantum security, and programming paradigm.[31] A transparent protocol is one that does not require any trusted setup and uses public randomness. A universal protocol is one that does not require a separate trusted setup for each circuit. Finally, a plausibly post-quantum protocol is one that is not susceptible to known attacks involving quantum algorithms.

Zero-knowledge proof (ZKP) systems
ZKP System	Publication year	Protocol	Transparent	Universal	Plausibly Post-Quantum Secure	Programming Paradigm
Pinocchio[32]	2013	zk-SNARK	No	No	No	Procedural
Geppetto[33]	2015	zk-SNARK	No	No	No	Procedural
TinyRAM[34]	2013	zk-SNARK	No	No	No	Procedural
Buffet[35]	2015	zk-SNARK	No	No	No	Procedural
ZoKrates[36]	2018	zk-SNARK	No	No	No	Procedural
xJsnark[37]	2018	zk-SNARK	No	No	No	Procedural
vRAM[38]	2018	zk-SNARG	No	Yes	No	Assembly
vnTinyRAM[39]	2014	zk-SNARK	No	Yes	No	Procedural
MIRAGE[40]	2020	zk-SNARK	No	Yes	No	Arithmetic Circuits
Sonic[41]	2019	zk-SNARK	No	Yes	No	Arithmetic Circuits
Marlin[42]	2020	zk-SNARK	No	Yes	No	Arithmetic Circuits
PLONK[43]	2019	zk-SNARK	No	Yes	No	Arithmetic Circuits
SuperSonic[44]	2020	zk-SNARK	Yes	Yes	No	Arithmetic Circuits
Bulletproofs[20]	2018	Bulletproofs	Yes	Yes	No	Arithmetic Circuits
Hyrax[45]	2018	zk-SNARK	Yes	Yes	No	Arithmetic Circuits
Halo[46]	2019	zk-SNARK	Yes	Yes	No	Arithmetic Circuits
Virgo[47]	2020	zk-SNARK	Yes	Yes	Yes	Arithmetic Circuits
Ligero[48]	2017	zk-SNARK	Yes	Yes	Yes	Arithmetic Circuits
Aurora[49]	2019	zk-SNARK	Yes	Yes	Yes	Arithmetic Circuits
zk-STARK[50]	2019	zk-STARK	Yes	Yes	Yes	Assembly
Zilch[31]	2021	zk-STARK	Yes	Yes	Yes	Object-Oriented
See also
Arrow information paradox
Cryptographic protocol
Feige–Fiat–Shamir identification scheme
Proof of knowledge
Topics in cryptography
Witness-indistinguishable proof
Zero-knowledge password proof
Non-interactive zero-knowledge proof
References
"What is a zero-knowledge proof and why is it useful?". 16 November 2017.
Blum, Manuel; Feldman, Paul; Micali, Silvio (1988). Non-Interactive Zero-Knowledge and Its Applications (PDF). Proceedings of the Twentieth Annual ACM Symposium on Theory of Computing (STOC 1988). pp. 103–112. doi:10.1145/62212.62222. ISBN 978-0897912648. S2CID 7282320. Archived (PDF) from the original on December 14, 2018.
Wu, Huixin; Wang, Feng (2014). "A Survey of Noninteractive Zero Knowledge Proof System and Its Applications". The Scientific World Journal. 2014: 560484. doi:10.1155/2014/560484. PMC 4032740. PMID 24883407.
Quisquater, Jean-Jacques; Guillou, Louis C.; Berson, Thomas A. (1990). How to Explain Zero-Knowledge Protocols to Your Children (PDF). Advances in Cryptology – CRYPTO '89: Proceedings. Lecture Notes in Computer Science. Vol. 435. pp. 628–631. doi:10.1007/0-387-34805-0_60. ISBN 978-0-387-97317-3.
Chalkias, Konstantinos. "Demonstrate how Zero-Knowledge Proofs work without using maths". CordaCon 2017. Retrieved 2017-09-13.
Feige, Uriel; Fiat, Amos; Shamir, Adi (1988-06-01). "Zero-knowledge proofs of identity". Journal of Cryptology. 1 (2): 77–94. doi:10.1007/BF02351717. ISSN 1432-1378. S2CID 2950602.
Chaum, David; Evertse, Jan-Hendrik; van de Graaf, Jeroen (1987). An Improved Protocol for Demonstrating Possession of Discrete Logarithms and Some Generalizations. Advances in Cryptology – EuroCrypt '87: Proceedings. Lecture Notes in Computer Science. Vol. 304. pp. 127–141. doi:10.1007/3-540-39118-5_13. ISBN 978-3-540-19102-5.
Blum, Manuel (1986). "How to Prove a Theorem So No One Else Can Claim It" (PDF). ICM Proceedings: 1444–1451. CiteSeerX 10.1.1.469.9048. Archived (PDF) from the original on Jan 3, 2023.
Sahai, Amit; Vadhan, Salil (1 March 2003). "A complete problem for statistical zero knowledge" (PDF). Journal of the ACM. 50 (2): 196–249. CiteSeerX 10.1.1.4.3957. doi:10.1145/636865.636868. S2CID 218593855. Archived (PDF) from the original on 2015-06-25.
Groth, J; Kohlweiss, M (14 April 2015). "One-Out-of-Many Proofs: Or How to Leak a Secret and Spend a Coin". Annual International Conference on the Theory and Applications of Cryptographic Techniques. Lecture Notes in Computer Science. Berlin, Heidelberg: EUROCRYPT 2015. 9057: 253–280. doi:10.1007/978-3-662-46803-6_9. hdl:20.500.11820/f6ec5d8f-cfda-4f56-9bd0-d9222b8d9a43. ISBN 978-3-662-46802-9. S2CID 16708805.
"Introducing Zero-Knowledge Proofs for Private Web attestation with Cross/Multi-Vendor Hardware". The Cloudflare Blog. 2021-08-12. Retrieved 2021-08-18.
Goldwasser, S.; Micali, S.; Rackoff, C. (1989), "The knowledge complexity of interactive proof systems" (PDF), SIAM Journal on Computing, 18 (1): 186–208, doi:10.1137/0218012, ISSN 1095-7111
Abascal, Jackson; Faghihi Sereshgi, Mohammad Hossein; Hazay, Carmit; Ishai, Yuval; Venkitasubramaniam, Muthuramakrishnan (2020-10-30). "Is the Classical GMW Paradigm Practical? The Case of Non-Interactive Actively Secure 2PC". Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security. CCS '20. Virtual Event, USA: Association for Computing Machinery: 1591–1605. doi:10.1145/3372297.3423366. ISBN 978-1-4503-7089-9. S2CID 226228208.
"PPPL and Princeton demonstrate novel technique that may have applicability to future nuclear disarmament talks - Princeton Plasma Physics Lab". www.pppl.gov. Archived from the original on 2017-07-03.
Hellwig, Daniel; Karlic, Goran; Huchzermeier, Arnd (3 May 2020). "Privacy and Anonymity". Build your own blockchain - A practical guide to distributed ledger technology. SpringerLink. p. 112. doi:10.1007/978-3-030-40142-9_5. ISBN 9783030401429. S2CID 219058406. Retrieved 3 December 2020.
Hurst, Samantha (28 October 2020). "Zcoin Announces Rebranding to New Name & Ticker "Firo"". Crowdfund Insider. Archived from the original on 30 October 2020. Retrieved 4 November 2020.
Bonneau, J; Miller, A; Clark, J; Narayanan, A (2015). "SoK: Research Perspectives and Challenges for Bitcoin and Cryptocurrencies". 2015 IEEE Symposium on Security and Privacy. San Jose, California: 104–121. doi:10.1109/SP.2015.14. ISBN 978-1-4673-6949-7. S2CID 549362.
Ben-Sasson, Eli; Chiesa, Alessandro; Garman, Christina; Green, Matthew; Miers, Ian; Tromer, Eran; Virza, Madars (18 May 2014). "Zerocash: Decentralized Anonymous Payments from Bitcoin" (PDF). IEEE. Retrieved 26 January 2016.
Orcutt, Mike. "A mind-bending cryptographic trick promises to take blockchains mainstream". MIT Technology Review. Retrieved 2017-12-18.
Bünz, B; Bootle, D; Boneh, A (2018). "Bulletproofs: Short Proofs for Confidential Transactions and More". IEEE Symposium on Security and Privacy. San Francisco, California: 315–334. doi:10.1109/SP.2018.00020. ISBN 978-1-5386-4353-2. S2CID 3337741. Retrieved 3 December 2020.
Odendaal, Hansie; Sharrock, Cayle; Heerden, SW. "Bulletproofs and Mimblewimble". Tari Labs University. Archived from the original on 29 September 2020. Retrieved 3 December 2020.
Andrew, Munro (30 July 2019). "Zcoin cryptocurrency introduces zero knowledge proofs with no trusted set-up". Finder Australia. Archived from the original on 30 July 2019. Retrieved 30 July 2019.
Aram, Jivanyan (7 April 2019). "Lelantus: Towards Confidentiality and Anonymity of Blockchain Transactions from Standard Assumptions". Cryptology ePrint Archive (Report 373). Retrieved 14 April 2019.
Goldreich, Oded (1985). "A zero-knowledge proof that a two-prime moduli is not a Blum integer". Unpublished Manuscript.
Goldreich, Oded; Micali, Silvio; Wigderson, Avi (1991). "Proofs that yield nothing but their validity". Journal of the ACM. 38 (3): 690–728. CiteSeerX 10.1.1.420.1478. doi:10.1145/116825.116852. S2CID 2389804.
Russell Impagliazzo, Moti Yung: Direct Minimum-Knowledge Computations. CRYPTO 1987: 40-51
Ben-Or, Michael; Goldreich, Oded; Goldwasser, Shafi; Hastad, Johan; Kilian, Joe; Micali, Silvio; Rogaway, Phillip (1990). "Everything provable is provable in zero-knowledge". In Goldwasser, S. (ed.). Advances in Cryptology—CRYPTO '88. Lecture Notes in Computer Science. Vol. 403. Springer-Verlag. pp. 37–56.
Ben-or, M.; Goldwasser, Shafi; Kilian, J.; Wigderson, A. (1988). "Multi prover interactive proofs: How to remove intractability assumptions" (PDF). Proceedings of the 20th ACM Symposium on Theory of Computing: 113–121.
Dwork, Cynthia; Naor, Moni; Sahai, Amit (2004). "Concurrent Zero Knowledge". Journal of the ACM. 51 (6): 851–898. CiteSeerX 10.1.1.43.716. doi:10.1145/1039488.1039489. S2CID 52827731.
Feige, Uriel; Shamir, Adi (1990). Witness Indistinguishable and Witness Hiding Protocols. Proceedings of the Twenty-Second Annual ACM Symposium on Theory of Computing (STOC). pp. 416–426. CiteSeerX 10.1.1.73.3911. doi:10.1145/100216.100272. ISBN 978-0897913614. S2CID 11146395.
Mouris, Dimitris; Tsoutsos, Nektarios Georgios (2021). "Zilch: A Framework for Deploying Transparent Zero-Knowledge Proofs". IEEE Transactions on Information Forensics and Security. 16: 3269–3284. doi:10.1109/TIFS.2021.3074869. ISSN 1556-6021. S2CID 222069813.
Parno, B.; Howell, J.; Gentry, C.; Raykova, M. (May 2013). "Pinocchio: Nearly Practical Verifiable Computation". 2013 IEEE Symposium on Security and Privacy: 238–252. doi:10.1109/SP.2013.47. ISBN 978-0-7695-4977-4. S2CID 1155080.
Costello, Craig; Fournet, Cedric; Howell, Jon; Kohlweiss, Markulf; Kreuter, Benjamin; Naehrig, Michael; Parno, Bryan; Zahur, Samee (May 2015). "Geppetto: Versatile Verifiable Computation". 2015 IEEE Symposium on Security and Privacy: 253–270. doi:10.1109/SP.2015.23. hdl:20.500.11820/37920e55-65aa-4a42-b678-ef5902a5dd45. ISBN 978-1-4673-6949-7. S2CID 3343426.
Ben-Sasson, Eli; Chiesa, Alessandro; Genkin, Daniel; Tromer, Eran; Virza, Madars (2013). "SNARKs for C: Verifying Program Executions Succinctly and in Zero Knowledge". Advances in Cryptology – CRYPTO 2013. Lecture Notes in Computer Science. 8043: 90–108. doi:10.1007/978-3-642-40084-1_6. hdl:1721.1/87953. ISBN 978-3-642-40083-4.
Wahby, Riad S.; Setty, Srinath; Ren, Zuocheng; Blumberg, Andrew J.; Walfish, Michael (2015). "Efficient RAM and Control Flow in Verifiable Outsourced Computation". Proceedings 2015 Network and Distributed System Security Symposium. doi:10.14722/ndss.2015.23097. ISBN 978-1-891562-38-9.
Eberhardt, Jacob; Tai, Stefan (July 2018). "ZoKrates - Scalable Privacy-Preserving Off-Chain Computations". 2018 IEEE International Conference on Internet of Things (IThings) and IEEE Green Computing and Communications (GreenCom) and IEEE Cyber, Physical and Social Computing (CPSCom) and IEEE Smart Data (SmartData): 1084–1091. doi:10.1109/Cybermatics_2018.2018.00199. ISBN 978-1-5386-7975-3. S2CID 49473237.
Kosba, Ahmed; Papamanthou, Charalampos; Shi, Elaine (May 2018). "xJsnark: A Framework for Efficient Verifiable Computation". 2018 IEEE Symposium on Security and Privacy (SP): 944–961. doi:10.1109/SP.2018.00018. ISBN 978-1-5386-4353-2.
Zhang, Yupeng; Genkin, Daniel; Katz, Jonathan; Papadopoulos, Dimitrios; Papamanthou, Charalampos (May 2018). "vRAM: Faster Verifiable RAM with Program-Independent Preprocessing". 2018 IEEE Symposium on Security and Privacy (SP): 908–925. doi:10.1109/SP.2018.00013. ISBN 978-1-5386-4353-2.
Ben-Sasson, Eli; Chiesa, Alessandro; Tromer, Eran; Virza, Madars (20 August 2014). "Succinct non-interactive zero knowledge for a von Neumann architecture". Proceedings of the 23rd USENIX Conference on Security Symposium. USENIX Association: 781–796. ISBN 9781931971157.
Kosba, Ahmed; Papadopoulos, Dimitrios; Papamanthou, Charalampos; Song, Dawn (2020). "MIRAGE: Succinct Arguments for Randomized Algorithms with Applications to Universal zk-SNARKs". Cryptology ePrint Archive.
Maller, Mary; Bowe, Sean; Kohlweiss, Markulf; Meiklejohn, Sarah (6 November 2019). "Sonic: Zero-Knowledge SNARKs from Linear-Size Universal and Updatable Structured Reference Strings". Proceedings of the 2019 ACM SIGSAC Conference on Computer and Communications Security. Association for Computing Machinery: 2111–2128. doi:10.1145/3319535.3339817. hdl:20.500.11820/739b94f1-54f0-4ec3-9644-3c95eea1e8f5. S2CID 242772913.
Chiesa, Alessandro; Hu, Yuncong; Maller, Mary; Mishra, Pratyush; Vesely, Noah; Ward, Nicholas (2020). "Marlin: Preprocessing zkSNARKs with Universal and Updatable SRS". Advances in Cryptology – EUROCRYPT 2020. Lecture Notes in Computer Science. Springer International Publishing. 12105: 738–768. doi:10.1007/978-3-030-45721-1_26. ISBN 978-3-030-45720-4. S2CID 204772154.
Gabizon, Ariel; Williamson, Zachary J.; Ciobotaru, Oana (2019). "PLONK: Permutations over Lagrange-bases for Oecumenical Noninteractive arguments of Knowledge". Cryptology ePrint Archive.
Bünz, Benedikt; Fisch, Ben; Szepieniec, Alan (2020). "Transparent SNARKs from DARK Compilers". Advances in Cryptology – EUROCRYPT 2020. Lecture Notes in Computer Science. Springer International Publishing. 12105: 677–706. doi:10.1007/978-3-030-45721-1_24. ISBN 978-3-030-45720-4. S2CID 204892714.
Wahby, Riad S.; Tzialla, Ioanna; Shelat, Abhi; Thaler, Justin; Walfish, Michael (May 2018). "Doubly-Efficient zkSNARKs Without Trusted Setup". 2018 IEEE Symposium on Security and Privacy (SP): 926–943. doi:10.1109/SP.2018.00060. ISBN 978-1-5386-4353-2.
Bowe, Sean; Grigg, Jack; Hopwood, Daira (2019). "Recursive Proof Composition without a Trusted Setup". Cryptology ePrint Archive.
Zhang, Jiaheng; Xie, Tiancheng; Zhang, Yupeng; Song, Dawn (May 2020). "Transparent Polynomial Delegation and Its Applications to Zero Knowledge Proof". 2020 IEEE Symposium on Security and Privacy (SP): 859–876. doi:10.1109/SP40000.2020.00052. ISBN 978-1-7281-3497-0.
Ames, Scott; Hazay, Carmit; Ishai, Yuval; Venkitasubramaniam, Muthuramakrishnan (30 October 2017). "Ligero: Lightweight Sublinear Arguments Without a Trusted Setup". Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security. Association for Computing Machinery: 2087–2104. doi:10.1145/3133956.3134104. ISBN 9781450349468. S2CID 5348527.
Ben-Sasson, Eli; Chiesa, Alessandro; Riabzev, Michael; Spooner, Nicholas; Virza, Madars; Ward, Nicholas P. (2019). "Aurora: Transparent Succinct Arguments for R1CS". Advances in Cryptology – EUROCRYPT 2019. Lecture Notes in Computer Science. Springer International Publishing. 11476: 103–128. doi:10.1007/978-3-030-17653-2_4. ISBN 978-3-030-17652-5. S2CID 52832327.
Ben-Sasson, Eli; Bentov, Iddo; Horesh, Yinon; Riabzev, Michael (2019). "Scalable Zero Knowledge with No Trusted Setup". Advances in Cryptology – CRYPTO 2019. Lecture Notes in Computer Science. Springer International Publishing. 11694: 701–732. doi:10.1007/978-3-030-26954-8_23. ISBN 978-3-030-26953-1. S2CID 199501907.
Categories: Theory of cryptographyZero-knowledge protocols
This page was last edited on 16 May 2023, at 22:14 (UTC).
Text is available under the Creative Commons Attribution-ShareAlike License 3.0; additional terms may apply. By using this site, you agree to the Terms of Use and Privacy Policy. Wikipedia® is a registered trademark of the Wikimedia Foundation, Inc., a non-profit organization.
Privacy policyAbout WikipediaDisclaimersContact WikipediaMobile viewDevelopersStatisticsCookie statementWikimedia FoundationPowered by MediaWikiToggle limited content width
Close
You can toggle between a fixed width and full width by clicking this button.